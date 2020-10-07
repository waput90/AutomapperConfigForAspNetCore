# Configuring AutoMapper in ASP.NET Core Application

what is automapper? is a simple little library built to solve a deceptively complex problem - getting rid of code that mapped one object to another. This type of code is rather dreary and boring to write, so why not invent a tool to do it for us? [Click here for more info.](https://automapper.org/)

1. first is you need to install it to your ASP.NET Core Application

you must add this package also 
```
AutoMapper.Extensions.Microsoft.DependencyInjection
```

2. Then after that you need to define it to services 

```
serviceCollection.AddAutoMapper(typeof(ProfileWrapper));
```

make sure that you have the namespace for mapper to use their library
```
using AutoMapper;
```
3. Then we will create our ProfileWrapper this would be the sample for creating source
and also we can register those map to different model

```
 public class ProfileWrapper : Profile
  {
      public ProfileWrapper()
      {
          CreateMap<[Model 1], [Model 2]>();

          CreateMap<[Model 1], [Model 2]>()
              .ForMember(dest =>
                  dest.[Property 1],
                  opt => opt.MapFrom(src => src.[Property 2]))
                  
          CreateMap<IEnumerable<[Model 1]>, IEnumerable<[Model 2]>>();

      }
  }
```

4. For application we'll use inject IMapper interface to our constructor

```
IMapper mappper 
```

5. Then we can use it via

```
mapper.Map<[YOUR MODEL HERE]>([MODEL NEEDS TO MAP]);
```
