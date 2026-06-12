---
title: "Programming language close to C#.NET in Ubuntu?"
date: 2008-08-12
forum: Programming Talk
---

### Post by thunderbirdje on 2008-08-12
In what language are most programs in Ubuntu written? Or does it differs? Like Banshee, F-Spot, ...

Irecently changed from windows to Ubuntu (wiha). In windows, I used C# (.NET) for programming (mostly C because of the fine tune options (C and C++ memory management) ands also the cryptic short language. (That's why I don't like Java that much, I'm almost feel like a typist instead of programmer in Java with the long names).

Which language is closed to C# (.NET) in Ubuntu? I used .NET mainly for the GUI's and the interop functions with MS Office (did a lot of automation).

I know there is Java (closs-platform) en the eclipse interface, but I was wondering if there is a good alternative?

I would like to make an application with datbase which is able to load an image and ask the user for a point: example some muscle, or acupuncture point :)). I know it isn't the most easy application to start with (that's why I'm in search of a decent programming languague, would be nice if it is close to C# .NET because it cut downs the learning time).

Thanks in advance :)

---

### Post by Lod on 2008-08-12
Try searching for Mono. This is a port of the MS .Net programming language to Linux.

---

### Post by Kadrus on 2008-08-12
> In what language are most programs in Ubuntu written? Or does it differs? Like Banshee, F-Spot, ...
Most of them are written in Python or C,using a graphical toolkit.
> Which language is closed to C# (.NET) in Ubuntu? I used .NET mainly for the GUI's and the interop functions with MS Office (did a lot of automation).
As said above you can use C# under Ubuntu using Mono,read the sticky,there is a link to a thread guiding you on how to set everything up.
> I know there is Java (closs-platform) en the eclipse interface, but I was wondering if there is a good alternative?
[Scala]("http://www.scala-lang.org/") is a great alternative to Java in my opinion,as it brings an imperative programming style with object orientation and as well functional programming.([Wikipedia]("http://en.wikipedia.org/wiki/Scala_(programming_language)"))

> I would like to make an application with datbase which is able to load an image and ask the user for a point: example some muscle, or acupuncture point ).
That can be done in any language,so you have multiple options.

---

### Post by LaRoza on 2008-08-12
> **thunderbirdje said:**
> In what language are most programs in Ubuntu written? Or does it differs? Like Banshee, F-Spot, ...

Which language is closed to C# (.NET) in Ubuntu? I used .NET mainly for the GUI's and the interop functions with MS Office (did a lot of automation).


I think F-Spot is written in C#, not sure though.

You can use C# on Linux. See the sticky.

---

### Post by tinny on 2008-08-12
> **LaRoza said:**
> I think F-Spot is written in C#, not sure though.

You can use C# on Linux. See the sticky.

Yeah F-Spot is C#.

Mono is what the OP should use.

Mono = .Net implementation on Linux :evil:
C# = Just a language
MonoDevelop = De facto C# Mono IDE

---

### Post by Methuselah on 2008-08-12
Java is close in syntax a philosophy and supported by more different IDEs and libraries, but Mono is essentially C#.

---

### Post by cszikszoy on 2008-08-12
> **LaRoza said:**
> I think F-Spot is written in C#, not sure though.

You can use C# on Linux. See the sticky.

F-Spot, Beagle, Banshee and Gnome-Do are all written in Mono.

Also, wikipedia's search facilities are written in Mono.

---

### Post by lakersforce on 2008-08-12
If you want to develop for C#, you should stick to Windows. In my experience Visual Studio 2008 runs much more stable than Monodevelop. Also Monodevelop does not (yet) include a Winforms editor, but (more or less) forces you to use Gtk.

Stay on Windows!

Not trying to start a flame-war, just adding my 5 cents.

---

### Post by thunderbirdje on 2008-08-13
Hm, thanks for all the input.

Of course I do love C# cause C gave the birth to it :D

I'll check out the mono and maybe learn the Python language (just time is at this moment a b*tch :)).

It is always nice to know in which language some programs were/are written.

In the future it would be just great to join some development group. I do worhsip al those people whom invest all programming time and help developing Ubuntu and onther open source projects. :KS

Thanks again

---

### Post by babyhuey on 2008-08-13
> **thunderbirdje said:**
> Hm, thanks for all the input.

Of course I do love C# cause C gave the birth to it :D

Thanks again


C did not give birth to C#. I would say C is a distant cousin. If anything, Java gave birth to C#.

---

### Post by Shin_Gouki2501 on 2008-08-13
> **babyhuey said:**
> C did not give birth to C#. I would say C is a distant cousin. If anything, Java gave birth to C#.

I agree and so would recommend java. What again you want to build?

---

### Post by babyhuey on 2008-08-13
> **Shin_Gouki2501 said:**
> I agree and so would recommend java. What again you want to build?


C# to Java should be an easy transition for OP. I like C#.NET but Mono and Monodevelop are not up to par with .NET and Java.

---

### Post by thunderbirdje on 2008-08-14
> C did not give birth to C#. I would say C is a distant cousin.

Yes, if you I look again at my sentence, you're right ;-)

> What again you want to build?

An application which is capable of showing (different) anatomical images of a human body. The goal is that the application would be some kind of 'teacher' to the user. The application should ask for an acupuncture point (for example 'LI4') and gives the user a good image where you can point it. Then the user should try to locate it (within some 'deviation marge' set before). 

What the application need:
- images
- list with locations of the points (meridian_name, point_number, 
image_map, x, y)

Could maybe also done with a DB or just some text-files...

---

### Post by Shin_Gouki2501 on 2008-08-14
some xml data as reference start will just do fine. A Clear Object Model and some Use Cases and this shouldn't be too much of a Problem. How many experience with C# you got?
Just start with some basic SWT stuff like displaying images and get some buttons to work.

---

