---
title: "Learning how to program in Gnome, need some suggestions."
date: 2005-03-28
forum: Programming Talk
---

### Post by audax321 on 2005-03-28
Hey everyone,

    I'm new to Ubuntu. Before I used Windows and SuSE with KDE. In Windows I programmed with VB6 and VB.Net. When I started using SuSE I wanted to learn a programming language so I started to learn C++, but KDevelop and all the tutorials and stuff started to make my head spin so I gave up on it.

Now, I'm using Ubuntu with Gnome and hoping that its easier to program for than KDE. From what I understand Gnome uses C and not C++? I want to learn how to make basic GUI applications and go from there. I've done some very basic C++ programming (dos/console kind) in an introductory class in college.

Anyway, I was wondering if any of you had suggestions for books, websites, tutorials for someone new to C programming specifically for Gnome. When I was trying to learn in KDE, everything I read seemed to have a Windows programming slant to it so it made it somewhat difficult.

Thanks.

---

### Post by bored2k on 2005-03-28
[http://ubuntuforums.org/showthread.php?t=20406](http://ubuntuforums.org/showthread.php?t=20406)
Maybe this link can help ?

---

### Post by audax321 on 2005-03-28
bored2k, I looked at that link before and gave it some thought, but I think I'm ready to learn C. I just need some good books or tutorials that start from the beginning and work their way up through GUI programming and relate to C in Linux. Most of the books I found were either too basic or started too advanced and dealt mostly with C in Windows. I have a little over four years of experience with VB, so I want to give learning C another shot. I know under Windows learning C is a must as VB's memory management in some of the programs I've created was really bad and implementing threading made it better, but not as good as I had hoped.

I'm still looking at Python as a possibility, but I want to learn a language that is easily supported in both Windows as well as Linux so I can move back and forth relatively easily. Now I think another question I have is, would it be easier to learn C for Windows first and then learn C for Linux or vice versa? Also if it would be easier to learn C for Windows, is the .Net or the version 6 variety better to start with?

---

### Post by ups on 2005-03-28
As for development with GNOME, there's a good amount of documentation at:
[http://developer.gnome.org/doc/](http://developer.gnome.org/doc/)

Also, check out Newren's excellent guide here: [Developing with GNOME](http://www.gnome.org/~newren/tutorials/developing-with-gnome/html/index.html)
Keep in mind that you don't need to build GNOME from CVS, which is also mentioned in this guide. But lots of other things are covered there, like glade/libglade (which you should use to quickly create GUIs).

Another thing would be to install devhelp and its supporting packages (search for it in synaptic and install all devhelp packages). You can use devhelp to browse all the documentation offline, and it also supports searching. A definite must have tool for programming with GNOME.

---

### Post by dataw0lf on 2005-03-28
If I were you, I'd also give wxWidgets a chance.  They're easy to use, cross platform, and are generally very well done.

---

### Post by audax321 on 2005-03-29
[QUOTE=dataw0lf]If I were you, I'd also give wxWidgets a chance.  They're easy to use, cross platform, and are generally very well done.[/QUOTE]

I just looked at some sample code for wxWidgets and I actually understood what was going on! :) Although if I go the wxWidgets route, I would have to learn C++ instead of C but I could easily port applications between Windows and Linux, correct?

Will users on Windows or Linux have to have to have extra stuff installed to actually run programs, like a wxWidgets Framework or something? Or will the programs just run after they've been compiled.

---

### Post by toojays on 2005-03-29
audax321,

With wxWidgets it is fairly painless to write applications which are portable between Windows and GNU/Linux. At my work I have recently implemented our latest application using wxWidgets, so I have some experience here. It is still important to test on both platforms, but the differences tend to be fairly trivial.

For your second question, about whether the user needs to have a framework installed, the answer is that you can choose. The answer tends to be dictated by the target audience and licensing issues. In my case, for our Windows build, we use *static linking*, which means that the final executable actually includes the code from the framework. In the Ubuntu package for the program, I use *dynamic linking*, which means that my package is dependent on libwxgtk-2.4. Static linking results in a much larger executable, but on Windows it means you can have the entire program in a single EXE, rather than needing a wxWidgets DLL.

These notes about static linking versus dynamic linking apply to Gtk/Gnome (and most other libraries) as well.

---

### Post by poster_nutbag on 2005-03-29
If you are new to C/C++, you should spend a few months coding WITHOUT using a gui lib. If you start with, say gtk, then you would have to learn the enviroment, the language AND the gui lib all at the same time. Just concentrate on pure C to start with and it'll make your life a lot easier.

---

### Post by pdamoc on 2005-04-04
for GUI programming python yields faster development.
I've done C, C++, Java and Python and I can testify that productivity gains are significant especialy if you're lazy (like me). :) 

go with python/wxPython!

the added benefit of wxpython is the fact that it has a huge helping community and belive me, that counts!

---

### Post by Abundance on 2009-09-19
> **pdamoc said:**
> for GUI programming python yields faster development.
I've done C, C++, Java and Python and I can testify that productivity gains are significant especialy if you're lazy (like me). :) 

go with python/wxPython!

the added benefit of wxpython is the fact that it has a huge helping community and belive me, that counts!

+1 for python yielding faster development vs C, C++ and Java!

Don't just take our word for it, though; here's an article by the great ESR on the topic:
[http://www.linuxjournal.com/article/3882]("http://www.linuxjournal.com/article/3882")

---

