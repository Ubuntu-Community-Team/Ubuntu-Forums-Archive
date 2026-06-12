---
title: "Any willing to take a noob programer under their wings and teach him the basics"
date: 2009-02-27
forum: Programming Talk
---

### Post by beattyml1 on 2009-02-27
I am somewhat new to linux (maybe about 6 months) but I have decided that it will probably my platform of choice unless things change dramatically in the OS market, I have had some programming experience in a few different languages, and I'm starting to be interested in helping out/put a few ideas into practice, and I was wondering if someone would be willing to teach some of the basics of programing for linux.  I am currently working through my second semester of C++ and have learned some basic C# on the job, (also did a major project in VB for work but there is no VB for linux to my knowledge).  I have had some experience with the basic GUI design in VS but don't really know what I'm doing as far as the GTK goes.

I am interested in both CLI and GTK, QT is ok but since I use gnome I figure its best to program for gnome.
Some of the things I am interested in learning are:
[LIST]
[*]How to interact with CLI (I know how to recieve arguments but not options in windows CLI as far as a starting point goes)
[*]How to create a basic GTK GUI and connect it with code (I realize that it will probably be a while before I get to the point where I am doing GUI programming)
[*]How to effectively use the linux filesystem in my finished application/command
[*]How to compile and package a release that will able to installed and used by others
[/LIST]

---

### Post by geirha on 2009-02-27
getopt for parsing arguments [http://www.gnu.org/software/libtool/manual/libc/Getopt.html](http://www.gnu.org/software/libtool/manual/libc/Getopt.html)

and this tutorial shows you how to make a simple gtk app.
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

### Post by beattyml1 on 2009-03-03
Thanks for the help I'll take a look at this stuff when I get some free time:)

---

### Post by SledgeHammer_999 on 2009-03-03
Since you mention C++ then you should know about [GTKmm](www.gtkmm.org). GTKmm has C++ bindings for GTK so it will make your life easier(although in some cases you'll to have a look to the GTK docs too).

---

