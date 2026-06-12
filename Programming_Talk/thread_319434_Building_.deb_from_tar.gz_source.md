---
title: "Building .deb from tar.gz source"
date: 2006-12-15
forum: Programming Talk
---

### Post by ahawks on 2006-12-15
There is a nice little GNOME applet called gnome-tla (terminal launcher applet) which reads the list of gnome-terminal profiles you have and the applet has a pull down menu allowing you to launch a specific profile easily. Great for working with remote systems, if you tell the profile to launch the command "ssh <host>"

Anyway, the .deb for it it worked in Dapper, but the dependency package names changed in Edgy, and the old maintainer of the .deb build seems to have disappeared..

So to the point: 

I have the source for gnome-tla.  It's written in python. 
The latest version of the source is 0.7
[http://sourceforge.net/project/showfiles.php?group_id=170654](http://sourceforge.net/project/showfiles.php?group_id=170654)

How can I build a .deb from this?   there is a debian/ folder in the source, with a control file. The tutorials I've tried to follow don't work, saying it needed DEBIAN, and then that the project name was missing in the control file. 

Can anyone either a) build a .deb and give it to the developer, or b) help me build the .deb.


Thanks!

---

### Post by yabbadabbadont on 2006-12-15
Make sure that you have build-essential installed (and the *-dev versions of all the package's dependencies) and also install "checkinstall".  Then follow the instructions for building the package from source, but don't do the "make install" step (usually the last step).  Instead, when you get to that point run, "checkinstall", instead.  You may have to answer some questions, but the default answers usually work.  It will then create a .deb file and install it for you.  After that, you can remove the package using Synaptic if you wish.

---

### Post by hod139 on 2006-12-15
If you are interested in getting it included into Ubuntu, check out the Ubuntu [MOTU wiki.]("https://wiki.ubuntu.com/MOTU/Packages/New") There is a lot of information about building packages there.  If you just want a deb for yourself, then checkinstall is the easiest way.

---

### Post by Azakus on 2006-12-17
If you run checkinstall without "sudo" then it just makes a package and doesn't install it. (Kind of a cheap trick, but it works).

---

### Post by kperkins on 2006-12-17
[http://maemo.org/platform/docs/pymaemo/python_maemo_howto.html](http://maemo.org/platform/docs/pymaemo/python_maemo_howto.html)

---

### Post by kperkins on 2006-12-17
Or download the deb here:
[http://keithperkins.net/files/gnome-terminal-launcher_0.4-0ubuntu1_i386.deb](http://keithperkins.net/files/gnome-terminal-launcher_0.4-0ubuntu1_i386.deb)
Took about 15 minutes because I had to edit the control file, and redo the deb. (called for python2.4-gtk2,and python2.4-gnome2, but edgy uses python packages without the 2.4 on the end.)
If you need the dif files, etc. I can upload them, too.

---

