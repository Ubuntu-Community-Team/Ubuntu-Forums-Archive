---
title: "is c# only for microsoft and windows ?"
date: 2006-03-13
forum: Programming Talk
---

### Post by krypto_wizard on 2006-03-13
is c# only for microsoft and windows or can also be used under Linux platform ?

I know this is very dumb question but I had to ask it  as I heard Borland also has a C# builder.

Thanks

---

### Post by oakz on 2006-03-13
[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by sapo on 2006-03-13
A link say more than a thousand words :)

[http://www.monodevelop.com/Main_Page](http://www.monodevelop.com/Main_Page)

---

### Post by rfruth on 2006-03-13
C++ is C++ what you need is a compiler / debugger or is that what you were asking about ?

---

### Post by krypto_wizard on 2006-03-13
I was asking if C# is proprietory language of Microsoft OR is it an open standard ?
[QUOTE=rfruth]C++ is C++ what you need is a compiler / debugger or is that what you were asking about ?[/QUOTE]

---

### Post by celloandy on 2006-03-14
Yeah, as the links above indicate, the Mono platform, sponsored mainly by Novell, provides a C# compiler and a .NET runtime environment that'll run lots of .NET software, though their implementation of System.Windows.Forms, the MS GUI component, is lacking, at this point.  Mono 1.2, due out Real Soon Now, should greatly improve this shortcoming, but there has certainly already been lots of development in C# for Linux.  Up until now, this has been mainly using the Gtk# toolkit (which is, in my opinion, superior to SWF, anyway), so most while C# work is being done, most of the stuff written under Mono has been written specifically targetting Linux, and most stuff written for Windows/SWF really only runs well under Windows, at this point, so despite Mono, there hasn't been a ton of cross-platform work, as some people expected when Mono was first announced.  Still, Mono is stable, and it's really easy to get started in using it.  A fair number of up-and-coming Linux apps, again, mostly developed by Novell, are written in using Mono, like Banshee and Beagle.

As for standards, both C# and .NET are ECMA standards, though Mono doesn't yet completely comply with those standards, and Microsoft does own patents relating to some parts of C# and .NET technology, which has led some to question how open it really is.  Still, it's there, it works well on Linux, and lots of people are using it to do cool things, so if C# interests you, take a look at the links above.

Andrew

---

### Post by commodore on 2006-03-14
But it's made by Microsoft. Why Linux people even want to use it? I mean they can fiddle it but they actually want to use it.

---

### Post by LordHunter317 on 2006-03-14
[QUOTE=commodore]But it's made by Microsoft. Why Linux people even want to use it?[/quote]Because I have clients who need to be able to target Windows and Linux?

Because until you step outside it's abilities, ASP.NET is superior to every other web framework out there?

---

### Post by celloandy on 2006-03-14
[quote=commodore]But it's made by Microsoft. Why Linux people even want to use it? I mean they can fiddle it but they actually want to use it.[/quote]
Because Microsoft got a lot of things right with their design of .NET, and open-source developers would be stubborn idiots not to at least consider using a technology that is, at least in some ways, superior to things currently used under Linux.  For example, .NET allows classes written in any .NET-targetted language to be used, and even extended, in any other .NET-targetted language.  This means that if good, complete .NET compilers were developed for lots of languages (and several, like Python and Ruby, are in the works), you could forget about having to maintain language bindings.  The Gtk+ folks could just produce one set of bindings, .NET, and everybody could use them from any language, which would save an enormous amount of man-power, and let Gtk+ developers concentrate on their toolkit rather than just bindings.

It's not perfect, by any means, but it's cool stuff.  Watching its use in the open-source world, it seems to allow rapid developmen comparable with Python, without nearly the speed penalties in the finished product.  You have the right to be skeptical, but don't discount it just because it's from Microsoft.

Andrew

---

### Post by Ozitraveller on 2006-03-15
Microsoft also has a c++ complier, but it doesn't mean that another company can't implement their own c++ compiler, many other companies have c++ compliers. And as far as I know they have helped Novell with some of their work on c#. It's to Microsoft's advantage to let other companies implement it! Bacause that would reinforce it as the standard language.

Iron Python was written in C#.

---

