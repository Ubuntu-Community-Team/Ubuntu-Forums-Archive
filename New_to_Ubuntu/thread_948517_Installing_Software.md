---
title: "Installing Software"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by Gloominati on 2008-10-15
Hello

I have learned already a lot of things in Ubuntu. There is just thing which really bothers me. Sometimes when I install software through Synaptic Package Manager, everything goes alright installation has been successfully completed but afterward I'm not able to find the exe. I just can't run the software i just installed. It happened to XMMS2 and WGET. Is there a universal guide or it's individual for every package?  

Thanks in advance

---

### Post by hyper_ch on 2008-10-15
(1) .exe don't run on linux ;)

(2) xmms2 and wget are command line utilities... so you want get an entry in your program's list - if you can't find an entry, it's to 99% a command line utility

---

### Post by Gloominati on 2008-10-15
> **hyper_ch said:**
> (1) .exe don't run on linux ;)

(2) xmms2 and wget are command line utilities... so you want get an entry in your program's list - if you can't find an entry, it's to 99% a command line utility

Programs like that don't have GUI?

---

### Post by LowSky on 2008-10-15
XMMS2 does have a GUI, but the package you installed may not automatically creat an icon for the menus.  Try opening a terminal and typing xmms2, the programs should start. Also you can always create your own icon it very easy, just righ click on the Applications menu and clcik on edit, form there you can edit the menu and even add or remove stuff without removing the software.

here infor on Wget
[http://www.gnu.org/software/wget/manual/wget.html](http://www.gnu.org/software/wget/manual/wget.html)

on Xmms2
[http://wiki.xmms2.xmms.se/wiki/Main_Page](http://wiki.xmms2.xmms.se/wiki/Main_Page)

---

### Post by SunnyRabbiera on 2008-10-15
> **Gloominati said:**
> Programs like that don't have GUI?

Some applications have one, some dont.
But if you need ones with graphical frontends we can show you what you need.
For a graphical frontend for wget I suggest installing gwget.
For xmms2 I would suggest using audacious instead as xmms is no longer supported for the most part.

---

### Post by Perfect Storm on 2008-10-15
or try audacious, it's in add/remove and synaptic package manager.

Or by command;

```
sudo apt-get install audacious audacious-plugins
```

---

### Post by oldos2er on 2008-10-15
Most user-installed executables end up in /usr/bin. Usually you just type the name of the program into a terminal (e.g. "wget"), and it will run.

---

### Post by Paqman on 2008-10-15
Couple of points:

[list]
[*]If you want to be sure that the app you're installing has a GUI, stick to Add/Remove instead of Synaptic. That's exactly what it's for.
[*]You don't need to actually locate the executable to launch an app on linux. For example, my Amarok executable is at /usr/bin/amarok, but I could launch it simply with the command "amarok" (no quotes) if I wanted. Linux is a lot tidier and cleverer than Windows about how it installs software.
[/list]

---

