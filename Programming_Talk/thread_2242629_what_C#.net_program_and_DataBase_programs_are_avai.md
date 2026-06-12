---
title: "what C#.net program and DataBase programs are available on Ubuntu ?"
date: 2014-09-03
forum: Programming Talk
---

### Post by Mohannad0010 on 2014-09-03
Hi There,
I have used to work with Visual Studio using c# with Access and SQLServer DB in Windows
but I have a problem now of what program is equal to VisualStudio to work with it in Ubuntu
and what database is available
in fact, I want to create database programs that works on windows so I wish to know what staff should I use to work with
I'll be waiting for your replies :)

---

### Post by MG&amp;TL on 2014-09-03
The [Mono project]("http://www.mono-project.com/") provides a .NET runtime and libraries on Linux, but it's not 100% up-to-date with Microsoft's version for obvious reasons. You can in theory use anything to build Mono software, but the MonoDevelop IDE is probably the most like Visual Studio. Mono also has [database access]("http://www.mono-project.com/docs/database-access/") libraries.

As far as I know you can't run SQL Server on *nixes, but what you could do is run SQL Server on a separate machine and connect to that (good practice anyway for production), then use a different provider like SQLite for local development.

---

### Post by slickymaster on 2014-09-03
*Moved to the ***Programming Talk**[I] sub-forum.

[/I]Hey Mohannad0010, welcome to the forums. If you already have experience with Visual Studio, your best bet is to use Mono. Mono is a Visual Studio equivalent for Linux, compatible with Visual Basic and C# code, a great thing for a beginner Ubuntu user that was a .Net programmer on Windows. Eclipse IDE is also a great and very powerful programming tool also compatible with C#.

Like MG&TL already pointed out, you can't run SQL Server on *nixes systems, at least not easily, but Ubuntu provides two popular database servers, MySQL and PostgreSQL.

---

### Post by Mohannad0010 on 2014-09-03
I'm really thankful for you [COLOR=#DD4814]**MG&TL **[/COLOR]and [COLOR=#C61919]**slickymaster **[/COLOR]for your answers that quick,
 I got most of what I needed and I'm downloading Mono now
I'll try to start a new beginning with Ubuntu,
 I like it and Linux generally hoping to find all I need here and leave windows finally
regards

---

### Post by slickymaster on 2014-09-03
You're welcome.

Please mark your thread as SOLVED so other people searching the forums know that it provides a working solution for their problem.

Just follow the link in my signature if you don't know how to do it.

---

### Post by CptPicard on 2014-09-04
I would like to point out though that if you want to code for Windows, you're better off doing it using Windows. There is no real Visual Studio replacement, and whether your Mono apps actually run on Windows is questionable.

As I see it you might want to consider two options -- either move over to the Java world where at least the language is close to C# and you get a mature, genuinely multiplatform stack, or you consider writing your database apps as web applications using any of the many existing technologies.

---

