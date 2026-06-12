---
title: "ASP.NET IDE/Interpretor/Apache module?"
date: 2006-08-12
forum: Programming Talk
---

### Post by drewsimon on 2006-08-12
Hi! I've got to start learning ASP.NET and developing ASP.NET websites and I'd love to do it on my Ubuntu laptop. Anybody know:

1. A good IDE in which to develop ASP.NET stuff. (with syntax highlighting, autocomplete, etc)
  -AND-
2. An Apache module or any other type of software that would allow me to test the code that I write?

---

### Post by cord on 2006-08-13
monodevelop is probably the best you will get in linux.

Mono itself comes with xsp which I believe is what it uses for processing asp.net. It can either be used itself as the webserver or used as a part of apache. For a sample guide you can check here:
[http://www.mono-project.com/Mod_mono](http://www.mono-project.com/Mod_mono)

---

### Post by ember on 2006-08-13
As cord mentioned, you can use mono, yet you'd better be using C# (not VB) then, because support is more complete. Generelly mono's status is quite good as for .NET 1.1 and reasonable for .NET 2.0 (at least as long as you do not use to much WebForm-components).

Sadly I found monodevelop to be inferior to Visual Studio (which I consider to be the best IDE for Windows), especially when it comes to debugging.

---

### Post by cord on 2006-08-15
> **ember said:**
> As cord mentioned, you can use mono, yet you'd better be using C# (not VB) then, because support is more complete. Generelly mono's status is quite good as for .NET 1.1 and reasonable for .NET 2.0 (at least as long as you do not use to much WebForm-components).

Sadly I found monodevelop to be inferior to Visual Studio (which I consider to be the best IDE for Windows), especially when it comes to debugging.

This is definitely true. Visual studio is part of the reason I still dual boot and have been doing so since the first .net release. It is quite amazing in alot of its functionality even though it feels sluggish even on a high spec system.

Debugging, visualizers, etc... are very very nice. I think it will be extraordinarily difficult for something like visual studio to be cloned in monodevelop. Even something like the visual studio express editions will present a considerable and time consuming challenge.

Anyhow, if you can somehow mannage it, I recommend having a dual boot of windows just for this. Alot of the tools you will need are free.

---

### Post by X.Cyclop on 2006-08-15
> **drewsimon said:**
> 
2. An Apache module or any other type of software that would allow me to test the code that I write?
Look for **apache::asp**. ;)

---

### Post by LordHunter317 on 2006-08-15
That's for ASP 3.0, not ASP.NET.

My real recommendation is to get VMWare and run it in Windows.  Depending on how much ASP.NET you need to know, you won't be able to learn it all on Mono.  The platform just isn't complete enough yet.  You wouldn't be able to experiment with everything you need to know for the ASP.NET exam, for example.

If you just want to play with basics, it's adequate.  But lots of fancy stuff doesn't work, and lots of stuff MS expects you to know is impossible on Mono (e.g., anything related to SQL Server, of which there's a lot of builtin stuff in ASP.NET).

---

