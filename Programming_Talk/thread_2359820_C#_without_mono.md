---
title: "C# without mono?"
date: 2017-04-28
forum: Programming Talk
---

### Post by MikeCyber on 2017-04-28
Hi
anyone using this?
[https://www.microsoft.com/net/core#linuxubuntu](https://www.microsoft.com/net/core#linuxubuntu)

Could I use that in Unreal? 
Thanks

---

### Post by MikeCyber on 2017-04-29
Followed this:
[https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu?ocid=player](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu?ocid=player)

but it creates a dll? how to run this on other machines?
Thanks

---

### Post by Olav on 2017-05-04
You will need to have the .net environment installed on the machine you want to run your application on. Then launch the program with the command
```
dotnet program.dll
```

---

### Post by MikeCyber on 2017-05-05
never heard of. Also on Windows/Mac? I guess not for c++ with vs code?

---

### Post by Olav on 2017-05-06
If you build a C or C++ project you will end up with an executable file (no extension necessary on Linux, .exe on Windows) that, depending on the project, will either have the libraries that your program uses linked into it (self contained executable) or it will depend on external shared objects (.so on Linux, .dll on Windows) that will have to be present on your target system. Those in turn are either distributed with your program or installed separately, in that case probably as packages.

Since you are developing in C# for .NET your programs will always (very much by definition) depend on the .NET framework (Microsoft .NET Core in this case, other options are the full Microsoft .NET stack on Windows and Mono on Linux and other OSs). There is no way around this.

The advantage of .NET Core is supposed to be that there are ways to package and distribute the Core files with your application, so in theory your application could be installed and run everywhere without depending on whatever version of the framework is already present on a particular system. You will just have to read the documentation or follow one of the many tutorials/howtos that are floating around. They should explain the nuts and bolts of this.

I hope this makes the situation clearer for you. Sorry I can't help you with how it works on Mac OS exactly, but an educated guess says it will be very similar to the situation on Linux.

---

