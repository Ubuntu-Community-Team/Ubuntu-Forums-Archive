---
title: "C# for Linux?"
date: 2007-04-08
forum: Programming Talk
---

### Post by lsutiger on 2007-04-08
Hi all! I am starting a bit of a big project at work...converting my personal office to Linux (other than our web/mail/ftp server). I have some small apps that I write in C# (mostly console apps) that communicate with the W2K3 server. Is there an IDE for C# in Linux? I use the VS 2K3 libraries to do text parsing and database operations and would just need to know the equivalent classes. 
I just jumped into Linux about 3 months or so ago, only using the dual boot to use Symantec PC Anywhere for work. I am so impressed with the community and the way the OS just works! I have only had to reboot my puter 3 times since install! Impressed!

I am not that jazzed about learning Python yet, but if thats the way to go.....oh well, I will jump. But from what I know, Python is just a scripting language? Correct me if I am wrong. I am looking for a similar Visual solution. I love writing code, but when visual came out, it as so much easier than writing most of the code for a window to function.
And just FYI...my background is basic, VB, C++, TAS 3.0, TAS 5.1 and C# ( In that order).

Thanx for any replies!

---

### Post by Frosty Cold Drink on 2007-04-08
Python will do everything you need to do. That said, check out [Mono]("http://www.mono-project.com/Main_Page") for C# on Linux and [Mono Develop]("http://www.monodevelop.com/Main_Page") for an IDE.

---

### Post by pmasiar on 2007-04-08
> **lsutiger said:**
> Python is just a scripting language?

Not sure what you mean by "just a scripting" language. It compiles to bytecode, and you can compile it farther to native architecture if you want.

Python + C libraries where you need speed is good enough for Google and NASA, I bet it can handle whatever you throw at it.

C# in Linux is controversial, go check archives, repeating them is beating dead horse.

---

### Post by samjh on 2007-04-08
Mono is a good platform, and C# is a good language.  Leverage your existing knowledge of VB and C#, and use Mono.

Mono's default IDE is Monodevelop, which has an integrated GUI designer for GTK#.  The current release of Mono is 1.2.3, which implements most of the ECMA C# 2.0 and CLI standard (with libraries), a VB.NET compiler and runtime, as well as GTK# and Mono-specific libraries.
[www.mono-project.com](www.mono-project.com)

Python is a general-purpose programming language, not merely a scripting language.  But it isn't for everyone.  Don't be pushed into it by evangelists' subjective opinions (there are a few around here) - try it for yourself and make up your own mind.  It's a very capable and easy-to-use language.

---

### Post by skeeterbug on 2007-04-09
> **samjh said:**
> Mono is a good platform, and C# is a good language.  Leverage your existing knowledge of VB and C#, and use Mono.

Mono's default IDE is Monodevelop, which has an integrated GUI designer for GTK#.  The current release of Mono is 1.2.3, which implements most of the ECMA C# 2.0 and CLI standard (with libraries), a VB.NET compiler and runtime, as well as GTK# and Mono-specific libraries.
[www.mono-project.com](www.mono-project.com)

Python is a general-purpose programming language, not merely a scripting language.  But it isn't for everyone.  Don't be pushed into it by evangelists' subjective opinions (there are a few around here) - try it for yourself and make up your own mind.  It's a very capable and easy-to-use language.

I would have to agree here. Give Python a try, and give Mono a try. We are mostly a .NET shop here, and we were going to try GTK#/Mono for a smart client application, but it was going to take too long to design the UI using GTK# vs using Visual Studio 2k5. Another thing we found annoying was breakpoints, you couldn't set breakpoints and step through your code. The documentation for Mono seems pretty good.

---

### Post by lsutiger on 2007-04-09
Thanx for all the input! I installed Mono via Adept and got it running. I started off ith a simple project (window with a button and some other events/signals), but one thing is really strange....I added a button to the window with the visual designer, and the button is the size of the window...so I look in properties and there are no size properties.
Oh the learning curve....lol
Could someone point me in the right direction? Is there a really good book on Mono? Thats how I learned about 50% of programming.
Thanx!

---

### Post by j_g on 2007-04-09
> I added a button to the window, and the button is the size of the window

With Windows, each control has its own size unrelated to any other control. With Linux, you have to put controls inside of a container, and then those controls try to fill up all the space in the container. (GTK tries to do auto-sizing of controls when the enduser resizes your window. Windows leaves that to an application to do via handling the WM_SIZE message). Your window is considered one container. So when you put your button inside of it, the button fills up the entire window. What you need to do is first put some horizontal and vertical "child containers" inside your window, to divide up its area into "sub-containers" (if you will). Then when you put a control inside of one of these sub-containers, it will fill up only that amount of space, and no more.

---

### Post by lsutiger on 2007-04-09
So sorta like frames in VS?

---

### Post by samjh on 2007-04-10
> **lsutiger said:**
> So sorta like frames in VS?

More like content panels and layout managers in Java.

WinForms will allow you to specify sizes of objects to whatever you want, and the sizes will stay that way.  In other words, WinForms uses layouts that are "absolute".  But GTK uses "containers", and whatever you put into that container will try to fill up the space.  For example, you might place a Vertical Box container divided into three sections onto a window.  Place a button on the top section of the container, and it will fill up that section and leave the other two sections blank.  You can put containers within containers, etc., to create more complex layouts.

---

### Post by lsutiger on 2007-04-10
All I ask is for a link to a tutorial! :D

---

### Post by samjh on 2007-04-10
> **lsutiger said:**
> All I ask is for a link to a tutorial! :D
Here, catch!

For hand-coding GTK (quite educational):
[http://www.mono-project.com/GtkSharp:_Hello_World](http://www.mono-project.com/GtkSharp:_Hello_World)

For using Stetic (the GUI designer that comes with Mono):
[http://www.monodevelop.com/Stetic_GUI_Designer](http://www.monodevelop.com/Stetic_GUI_Designer) (it didn't work for me, though)

---

### Post by lsutiger on 2007-04-10
I owe you multiple thanx! :D

---

