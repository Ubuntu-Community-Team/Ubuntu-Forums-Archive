---
title: "Program Files"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by icyest on 2008-11-23
What's the Linux equivalent of the famous "Program Files" directory that windows has? I installed a program called MPlayer through Applications>Add/Remove, and now I cant find it under "Sound & Video"

---

### Post by OutOfReach on 2008-11-23
Program files are usually scattered around various places, mainly /usr/share/
and executables, which launch the program, is usually in /usr/bin (which might be what your looking for)

I know there is a command in Ubuntu to list the installed files for a program, but I don't use Ubuntu so maybe someone else can provide that command.

---

### Post by nhasian on 2008-11-23
OutOfReach,

I think your talking about *dpkg*.

for example if you want to know what package the program */bin/bash* comes from you would use:

```
dpkg -S /bin/bash
```

it will tell you the package is called bash.  then to see all the files that come in the package bash you would enter type:

```
dpkg -L bash
```



> **OutOfReach said:**
> I know there is a command in Ubuntu to list the installed files for a program, but I don't use Ubuntu so maybe someone else can provide that command.

---

### Post by Michael.Godawski on 2008-11-23
You can also find all files belonging to an application through the synaptic package manager.
 
Just open it up, right click on an installed application, go to properties, and then go to 
Installed Files.

---

### Post by zvacet on 2008-11-23
@ **icyest**

System>preferences>main menu and there on the left side select **sound & video** and on the right side **new item**.Launcher will pop up and under **command**  put **gmplayer %F** and icon is under **usr/share/pixmaps** .Of course you will give your program a name Mplayer.

---

### Post by Paqman on 2008-11-23
On Linux you don't need to know the full path to launch an application. You only need to know the name of the package, the system is clever enough to launch it with just that.

---

### Post by Zorgoth on 2008-11-23
Alt-F2, type the name of the application, and it will almost certainly run it.

---

