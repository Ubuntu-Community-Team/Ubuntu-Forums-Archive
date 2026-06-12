---
title: "Help me decide what to learn"
date: 2005-03-19
forum: Programming Talk
---

### Post by dolson on 2005-03-19
Anyhow, my background is this:

QBASIC
QuickBASIC 4.5
Turbo Pascal for Windows
Visual Basic 6.0
Delphi 5.0-7.0
Kylix 2
Java
C/C++ with SDL
Bash scripting

My preferred console programming language is C/C++ and I use the SDL libraries to develop games (crappy ones, but anyhow). My preferred GUI development over the years has been with Delphi under Windows, but now I want to finally tackle GUI development on Linux, specifically Gnome/GTK2. I don't like KDE, and I don't even have the KDE libs installed.

I have many choices after reading some threads and searching on the net:

* I could learn some Python and use BoaConstructor or something.
* I could look into MonoDevelop and learn C#.
* I could use VDKBuilder.
* I could learn Glade and use Anjuta.
* I could install the KDE libs and Gambas and develop some KDE apps.
* I may still have Kylix kicking around.
* I could use Java and Swing or whathaveyou.

Personally, I'm leaning towards VDKBuilder or Glade+Anjuta. What do you think, given my Gnome/GTK2, C/C++, and Delphi-style preferences?

---

### Post by DJ_Max on 2005-03-19
To be honest you really have no limits since learning Java gives you a universal set of skills in OO. Python would be a snap to learn.

Glade is a program for use with C, C++, Python, etc for making GUI in those languages easier.
So I would go Python & Glade. Anjunta is a nice IDE.

---

### Post by defkewl on 2005-03-19
I would go with Java if I were you. You could use the same source code under any OS.

---

### Post by dolson on 2005-03-19
[QUOTE=defkewl]I would go with Java if I were you. You could use the same source code under any OS.[/QUOTE]
 My experience with it was a few years back. I'd have to re-learn it. The Java apps I've run these days are bloated and slow. Is this due to bad programmers, bad Java VM implementation, or just the overall nature of Java apps? I can't really remember much about when I used Java, only that I seemed to be the only one in my classes that could write the assignments and have them work properly.

I'm not really interested in cross-platform, but if I were, I could still do it with C and GTK, couldn't I? I assume so, since Gaim, Ethereal, and Gimp are apps that I use extensively at work on Windows.

Anyhow, thanks for your thoughts so far. I've debated installing VDKBuilder and Glade and trying them out, but I was hoping someone would maybe know if one or the other had an advantage over the other. I've used Anjuta in the past for my C/C++ SDL work, and I really like it overall. I'm not entirely familiar with how the auto tools work, so sometimes I can run into issues with that.

Am I right in thinking that Python doesn't produce binaries, only source that is interpreted? If that is the case, sorta like QBASIC programs, I'm not sure I want to go that route either.

I'm still debating though. Anyhow, maybe I'll just install some things on my laptop and experiment on it.

---

### Post by DJ_Max on 2005-03-19
> I can't really remember much about when I used Java, only that I seemed to be the only one in my classes that could write the assignments and have them work properly. 
Thats because Java is advanced & has a learning curve due to how strict it is.

Python is a bytecode compiled language  it just compiles on the fly. A .pyc is generated to avoid reparsing sources.

I encourage you to take a look at [Ruby.](http://ruby-lang.org/)

---

### Post by dolson on 2005-03-20
Well, Glade2 is a lot nicer than what I remember it being. I think perhaps it's because I now somewhat understand how it all works, whereas the last time I tried it, I wasn't really ready for it. So UI design is pretty much taken care of.

If it's not too hard to write the events, then I'm just going to stick with Anjuta and trusty old C++, rather than learn a new language. If I can't figure it out in a couple hours or so, I'll take up re-learning Java again. :)

---

### Post by defkewl on 2005-03-20
[QUOTE=dolson]My experience with it was a few years back. I'd have to re-learn it. The Java apps I've run these days are bloated and slow. Is this due to bad programmers, bad Java VM implementation, or just the overall nature of Java apps? I can't really remember much about when I used Java, only that I seemed to be the only one in my classes that could write the assignments and have them work properly.
[/QUOTE]

Don't blame the tool, blame the user. Haha. Of course the speed of the application that you wrote using Java depends on the source. If you want a faster compiler, try using Jikes from IBM.

---

### Post by dolson on 2005-03-20
[QUOTE=defkewl]Don't blame the tool, blame the user. Haha. Of course the speed of the application that you wrote using Java depends on the source. If you want a faster compiler, try using Jikes from IBM.[/QUOTE]

I'm not talking about apps that I wrote, I'm talking about things like LimeWire, jKaiUI, and things like that. Other people's Java stuff. It's slow and looks like crap.

I do appreciate the cross-platform ability of Java, don't get me wrong, but I'm only really interested in Linux, and I like the pretty GTK2.  8-)

---

### Post by Rottweiler on 2005-03-20
[QUOTE=dolson]My preferred console programming language is C/C++ and I use the SDL libraries to develop games (crappy ones, but anyhow). My preferred GUI development over the years has been with Delphi under Windows, but now I want to finally tackle GUI development on Linux, specifically Gnome/GTK2. I don't like KDE, and I don't even have the KDE libs installed.[/QUOTE]**For GUI programming I can't imagine anyone recommending anything other than wxWidgets.**

It's multiplatform. It produces apps in the native widget set. It doesn't get you locked into a particular lib (GTK, Qt, MFC, etc.)

All applications should be built, if possible, as multiplatform. That's our best tool for getting people to make the proprietary-->OSS journey.

After than, learn Python. It is the perfect salve for those who secretly miss VB. But has none of the problems of VB or the peculiarities of Java or the brain-twisting arcaneness of C++.

---

### Post by Daniel G. Taylor on 2005-03-20
GNOME, KDE, Mac OSX, Windows, BeOS, etc all have different GUI coding standards, so wx is not always the best option for a cross-platform GUI program. It is, however, probably the easiest to maintain.

I would vote for Python + pyGTK and Glade, falling back to C/GTK+ if you ever need it. A week or two of learning and you can even use code you wrote in C/C++ from within Python programs (check out [http://docs.python.org)](http://docs.python.org)). Python also runs on everything from your typical PC to your Zaurus, Playstation, and IBM mainframes (full list on the Python download pages). Just make sure to not hard-code things like paths and you should be fine. Also, no cross compiling for all the architectures because Python byte-compiles on the fly.

If you are worried about jumping into more than one new thing at once, remember that GTK+ has plenty of language bindings available, so you can use the language you already know to become more familiar with GTK+.

---

### Post by dolson on 2005-03-20
Thanks for all of the thoughts so far. I've done a very simple app in C++ and GTK, where I click the button and it sets the window title and launches gnome-calculator, and it was easier than I thought it would be. This is a good starting point, and I think I'm well on my way to writing applications that rival those that I wrote in my Windows days.

If it gets too complex, or when I feel I'm ready, I'll tackle Python. I tried learning it once but that effort was fruitless, just like my futile attempts to produce something decent with Blender. Eventually I'd like to know how to get around in it at least, as it seems to be very popular and fairly straight-forward.

---

### Post by TjaBBe on 2005-03-22
I would go for Glade + Anjuta. As it is just C/C++ so you allready know the language. And you would be able to port your programs to windows ;). (I believe).

---

