---
title: "Learned VB.net, What Now?"
date: 2011-03-09
forum: Programming Talk
---

### Post by a.kleiner on 2011-03-09
Okay, so I've learned the basics of programming in my VB.net class, what would be the best language to learn next? Preferably something I can use to write programs for Ubuntu?

---

### Post by ve4cib on 2011-03-09
There are a few choices, all of which are viable:

1- C and/or C++.  These get used a lot for high-performance programs and allow the most flexibility when dealing directly with hardware.  They also tend to be the easiest to mess up and the hardest to debug.

2- C#/GTK#.  Mono is a Linux-compatible .NET implementation, and the C# language is basically the same between the Windows world and the Linux world (barring a few libraries).  You already know how to work with .NET, so this would be an easy transition.

3- Python.  Some might call it a high-powered scripting language.  It's very easy to write, very easy to learn, and gets used for everything from server-side scripts to batch processing to GUI applications.

4- Java.  Similar to C++ in terms of syntax, but with automatic garbage collection, proper object-orientation, and is generally nicer to debug.  It's not terribly popular for writing applications outside of the corporate and web application worlds, but it works.

5- Lisp/Scheme.  It'll throw everything you think you know about programming out the window and force you to think very, very differently.  It doesn't get used much outside of AI research fields, but it's a fun language to play around with.


Those would probably be my top-5 (counting C and C++ as the one choice).  Depending on what kinds of applications you want to write that will affect your choice.  End-user applications with GUIs would probably be easiest in C#, C++, or Python.

C and C++ have a steep learning curve because of all of the very low-level management you need to do.  But they're used all over the place, and are good languages to learn eventually.  If you ever want to do anything with the kernel you need to learn C.

---

### Post by PaulM1985 on 2011-03-09
I think I would go with C#.  It is quite a good language which seems to be growing in popularity commercially at the minute.  It should be an easy-ish transition.

Also Java is worth learning and is quite similar to C# in alot of ways.

Paul

---

### Post by a.kleiner on 2011-03-09
> **ve4cib said:**
> There are a few choices, all of which are viable:

1- C and/or C++.  These get used a lot for high-performance programs and allow the most flexibility when dealing directly with hardware.  They also tend to be the easiest to mess up and the hardest to debug.

2- C#/GTK#.  Mono is a Linux-compatible .NET implementation, and the C# language is basically the same between the Windows world and the Linux world (barring a few libraries).  You already know how to work with .NET, so this would be an easy transition.

3- Python.  Some might call it a high-powered scripting language.  It's very easy to write, very easy to learn, and gets used for everything from server-side scripts to batch processing to GUI applications.

4- Java.  Similar to C++ in terms of syntax, but with automatic garbage collection, proper object-orientation, and is generally nicer to debug.  It's not terribly popular for writing applications outside of the corporate and web application worlds, but it works.

5- Lisp/Scheme.  It'll throw everything you think you know about programming out the window and force you to think very, very differently.  It doesn't get used much outside of AI research fields, but it's a fun language to play around with.


Those would probably be my top-5 (counting C and C++ as the one choice).  Depending on what kinds of applications you want to write that will affect your choice.  End-user applications with GUIs would probably be easiest in C#, C++, or Python.

C and C++ have a steep learning curve because of all of the very low-level management you need to do.  But they're used all over the place, and are good languages to learn eventually.  If you ever want to do anything with the kernel you need to learn C.

Alright, thanks for the explanation!

---

### Post by Dragonbite on 2011-03-09
C# would allow you to use the .NET framework you are familiar with, as well as code (via Mono) for many different platforms including mobile phones (except those plugins cost $$$$), including Droid, iOS and I believe Windows 7 Phone is either supported or should be supported soon.

I see a lot of references to Python with Linux as well as web applications (Google makes good use of Python I have heard).

Should look at some C-based language since the syntax is more similar with a wider variety of languages (C, C++, Qt, Java, C#, PHP, Javascript, etc.) than VB.NET. Believe me, I use VB.NET at work and am trying to migrate my skills to C# but have difficulty finding the time.

---

### Post by directhex on 2011-03-09
Technically you can write apps for Ubuntu with VB.NET - but making a GUI is a pain. C# would likely be a good fit for you, since you already have experience with .NET

---

