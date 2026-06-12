---
title: "Using gedit external tools for building project"
date: 2012-09-05
forum: Programming Talk
---

### Post by siz on 2012-09-05
Hey,

I am using gedit as a light and fast IDE for c/c++ and it works great, however when using the Build function it has under external tools it doesn't seem to use the Makfile in parent directory.

For example:
/
/Makefile
/folder1/Makefile
/folder2/file.c 

If I build from file.c it finds folder1/Makefile and executes that, when it should find /Makefile instead..

Is there anyone who has a script that finds the correct parent directory, or maybe a plugin where you can set the parent directory?

I have never been good at scripting, and new to c/c++ so that's why I ask.

If I've posted in the wrong section I apologize :oops:

---

### Post by conradin on 2012-09-06
I had no idea that gedit had such options! 
Consider looking into the gedit config file, 
~/.gconf/apps/gnome-settings/gedit/%gconf.xml
(or something like that)

--side note: geany... light and fast, and I use it as my text editor.

---

