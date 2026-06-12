---
title: "Scribes - a new text editor for Gnome?"
date: 2005-09-21
forum: Packaging and Compiling Programs
---

### Post by PuleX on 2005-09-21
Hi all, 

I'm playing with my Breezy preview install, and while looking for great Gnome software I found this new text editor for Gnome: Scribes
[http://scribes.sourceforge.net/index.html](http://scribes.sourceforge.net/index.html) 

It's currently at 0.1, but it looks promising. I may try to package it for ubuntu.  :)

---

### Post by rwabel on 2005-09-22
[QUOTE=PuleX]Hi all, 

I'm playing with my Breezy preview install, and while looking for great Gnome software I found this new text editor for Gnome: Scribes
[http://scribes.sourceforge.net/index.html](http://scribes.sourceforge.net/index.html) 

It's currently at 0.1, but it looks promising. I may try to package it for ubuntu.  :)[/QUOTE]
 I like it too. it's simple and fast

---

### Post by Sykil on 2005-09-29
Sweet! I've been wanting to try it out. :)

---

### Post by sas on 2005-10-23
0.2 has just been released. I really like it, I'm using it instead of gedit these days. I considered trying to packaging 0.1, but couldn't find any instructions for packaging a python app that uses setup.py anywhere.

---

### Post by esj on 2005-10-23
[QUOTE=sas]0.2 has just been released. I really like it, I'm using it instead of gedit these days. I considered trying to packaging 0.1, but couldn't find any instructions for packaging a python app that uses setup.py anywhere.[/QUOTE]

yes, yes.  Please share this packaging information.  I desperately want to set up my antispam system (camram.org) as a package for ubuntu.  one of the big challenges is figuring out how to automatically change/modify the postfix configuration.  I may need to leave that as a human mediated task.

---

### Post by teeler on 2005-10-30
Hey guys, how can you get this thing to compile? I get

> running install
error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)


When i try to install, I'm sorta new to Ubuntu, I tried looking for that makefile but theres soooooooooo many listings for python2.4 i just gave up.
Am i missing a package? Is there like a python-source or something? ;)

---

### Post by teeler on 2005-10-30
nanananana! 

> 
sudo apt-get install python-dev


/me loves answering his own problems, even if it only happens once every 14 years.

---

### Post by denisesballs on 2006-01-19
[QUOTE=teeler]Hey guys, how can you get this thing to compile? I get



When i try to install, I'm sorta new to Ubuntu, I tried looking for that makefile but theres soooooooooo many listings for python2.4 i just gave up.
Am i missing a package? Is there like a python-source or something? ;)[/QUOTE]

you need python2.4-dev

---

