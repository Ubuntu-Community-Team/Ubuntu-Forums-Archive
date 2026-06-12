---
title: "Programming in Gtk/Qt"
date: 2007-06-01
forum: Programming Talk
---

### Post by Tachyon_ on 2007-06-01
Hi all,

I'm thinking of learning Linux GUI-programming and I'm now facing the decision between all wonderfull libaries. I have been looking into many toolkits and done some research. Most of the comparasions date back to the beginning of 2000, so I'd like to hear your experiences. Qt and Gtk are the ones I'm interested in as I might want to help coding KDE or Gnome or both in the future. I don't dislike any desktop environment, so the main thing would be the differences in developing for them. Of course, you are free to suggest some others as well. This is not a "gtk vs. qt"-battle, instead I would like to hear about their differences as well as your experiences so I could pick the one for me.

Some stuff I found:
[Interesting poll "Gtk or Qt: Do You Care?"]("http://www.linuxappfinder.com/poll/gtk_or_qt"), which suggest that choosing a GUI toolkit doesn't matter much to user, and both are as popular.
[Nice examples of one application done in C,C++ and python using Gtk&Qt]("http://phil.freehackers.org/kde/cmp-toolkits.html")
[Technicall QT newsgroup discusion about them dating back to 2002.]("http://lists.trolltech.com/qt-interest/2002-08/thread00000-0.html")

If you have the time, I would be interested in these factors:

**Widget set**
I'd like to have a rich widget set and would prefer all-in-one solution

**Language**
I have some experience in BASIC, C++/C, Java and Python. I dont find OO or pointers confusing, so that's not an issue. I would assume that doing GUI-stuff with OO (Qt?) is more convient. Less code, more fun?

**Difficulty**
The difficulty is not such an issue for me with C++, but I'm conserned if doing smaller code with it really makes the development time more short or fun, but does it require much more thinking and playing around in a small project?

**Python**
I really like this language, and would prefer it over C/C++ at the time being, so ***I would really, really appreciate pyGtk and pyQt experiences***. Also the active development of these is important for me. I dl:ed some examples, but found both of these quite badly documented. Just me?

**Crossplatform**
I don't have a windows operating system, but others might want to know. As far as I found out, both of them work?

**Community**
KDE and Gnome have both their sites and application resources like we have this forum. But the support and community is really important, I would think that both of them have their fans and communities?

**Legal stuff**
I found about qt-issue, which is now solved, right? I'm not planning to do anything commercial, instead, I would like to help gpl-projects in future so choosing gtk/qt doesn't really matter? One issue is however, with gnome, the website has stuff like don't do this or that, and* "Do not use GNOME logos unless you have explicit written permission to do so."*, KDE, however, says only that *"The KDE logo can be used freely as long as it is not used to refer to products other than KDE itself."* Is this spirit a fundamental issue that reflects to the programs as well?

I hope my english was readable, thank you very much in advance!

---

### Post by seamless on 2007-06-01
[QUOTE="Tachyon_"]Widget set
I'd like to have a rich widget set and would prefer all-in-one solution[/QUOTE]
GTK and Qt both offer extensive widget sets.

[QUOTE="Tachyon_"]Language
I have some experience in BASIC, C++/C, Java and Python. I dont find OO or pointers confusing, so that's not an issue. I would assume that doing GUI-stuff with OO (Qt?) is more convient. Less code, more fun?[/QUOTE]
GTK has bindings for just about every language, more so than Qt. GTKmm specifically is a C++ binding so OOP with GTK is a non-issue. Unless you want to use straight C of course.

[QUOTE="Tachyon_"]Difficulty
The difficulty is not such an issue for me with C++, but I'm conserned if doing smaller code with it really makes the development time more short or fun, but does it require much more thinking and playing around in a small project?[/QUOTE]
Python would be a good choice. As far as GTK vs Qt in difficulty, both have extensive APIs and will allow you to do pretty much what ever you want without much trouble. However Qt does have much better and more extensive documentation. Qt also offers the assistant program which gives you an offline browser for all of the documentation, including code samples. 

[QUOTE="Tachyon_"]Crossplatform
I don't have a windows operating system, but others might want to know. As far as I found out, both of them work?[/QUOTE]
Both are fully crossplatform. The only requirement is you don't use things like hard coded paths in your application.

[QUOTE="Tachyon_"]Community
KDE and Gnome have both their sites and application resources like we have this forum. But the support and community is really important, I would think that both of them have their fans and communities?[/QUOTE]
Both are large and active.

[QUOTE="Tachyon_"]Legal stuff
I found about qt-issue, which is now solved, right? I'm not planning to do anything commercial, instead, I would like to help gpl-projects in future so choosing gtk/qt doesn't really matter? One issue is however, with gnome, the website has stuff like don't do this or that, and "Do not use GNOME logos unless you have explicit written permission to do so.", KDE, however, says only that "The KDE logo can be used freely as long as it is not used to refer to products other than KDE itself." Is this spirit a fundamental issue that reflects to the programs as well?[/QUOTE]
The Qt issue was solved a long time ago. Qt is dual licensed under the GPL and a commercial license (if you want to use it for commercial development). You can use GTK or Qt if you want to write GPL code without a problem. The written permission and use the logo mainly has to do with trademark law in countries like the US. If someone uses your logo without permission you can loose the trademark by not actively trying to protect it. Still you should have permission to use the official logo before using it in your project as a matter of courtesy. Also it is not in the spirit of the program itself it is actually taking the physical logo as seen on the website and using it in your application.

---

### Post by loell on 2007-06-01
you might like to have a look on **wxwidgets** too

cross platform , has wide extensive widgets , and you never have to worry about look and feel ;)

---

### Post by pmasiar on 2007-06-01
Start with finding a project you want to participate, and learn library (and language) they use.

Another cool newcomer is Sugar GUI, used in OLPC - laptop.org . OLPC and Ubuntu prefer Python.

---

