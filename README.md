# ASP.NET Core Identity with In Memory Custom User Store
This sample repo show how you can use custom UserStore for ASP.NET Core Identity
For the sake of simplicity, we will use `MemoryCache` to store user information. 

- create new ASP.NET MVC with individual auth by running `dotnet new webapp --auth Individual`
- edit `startup.cs` and remove `.AddEntityFrameworkStores<ApplicationDbContext>();` and `services.AddDbContext<ApplicationDbContext>()` call
- add new `InMemoryUserStore.cs` file which implements all Identity Interfaces
- add implementations using `IMemoryCache`
- on `startup.cs`, call `.AddUserStore<InMemoryUserStore<IdentityUser>>();` after `AddDefaultIdentity()`
- NOTE: since we run in memory, every you restart the server, you will need to sign up again
