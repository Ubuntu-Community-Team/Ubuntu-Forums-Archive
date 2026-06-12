---
title: "[SOLVED] Packaging a .deb from a binary file"
date: 2008-07-31
forum: Packaging and Compiling Programs
---

### Post by Diabolis on 2008-07-31
I'm trying to make a .deb file.

This is what I have:
```
ls -R | grep ./
./debian:
./debian/DEBIAN:
./debian/DEBIAN/usr:
./debian/DEBIAN/usr/bin:
./debian/DEBIAN/usr/share:
./debian/DEBIAN/usr/share/applications:
./debian/DEBIAN/usr/share/conkygui:
./debian/DEBIAN/usr/share/conkygui/bin:
./debian/DEBIAN/usr/share/conkygui/lib:
./debian/DEBIAN/usr/share/doc:
./debian/DEBIAN/usr/share/doc/conkygui:
./debian/DEBIAN/usr/share/pixmaps:

```

To build the .deb I type:
```
dpkg --build debian/ conkygui_v12_all.deb
dpkg-deb: building package `conkygui' in `conkygui_v12_all.deb'.
```

Then I try to install it:
```
dpkg: error processing conkygui_v12_all.deb (--install):
 package control info rmdir of `usr' didn't say not a dir: Directory not empty
Errors were encountered while processing:
 conkygui_v12_all.deb
```

From what I have read, this error could be related to the directories structure that I'm using (not sure). But I don't find the error...

---

### Post by Diabolis on 2008-07-31
The directories structure was messed up, after correcting it, this is what I got:
```
./debian:
./debian/DEBIAN:
./debian/usr:
./debian/usr/bin:
./debian/usr/share:
./debian/usr/share/applications:
./debian/usr/share/conkygui:
./debian/usr/share/conkygui/bin:
./debian/usr/share/conkygui/lib:
./debian/usr/share/doc:
./debian/usr/share/doc/conkygui:
./debian/usr/share/pixmaps:
```

I repeated the same steps to build the package and then tried to install it. Of course, something went wrong, that is why I'm posting back.

```
sudo dpkg --install conkygui_v12_all.deb
dpkg: error processing conkygui_v12_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 conkygui_v12_all.deb

```

---

### Post by Diabolis on 2008-08-01
It finally worked. The problem was a desktop configuration file not well made.

I would give a thanks to myself if I could.

---

### Post by Diabolis on 2009-05-21
> How did you solve the issue you had before while building the .deb?

I am having the same exact issue, and can't figure it out.

[Your previous post]("http://ubuntuforums.org/showpost.php?p=5503569&postcount=3")


Desktop configuration files (.desktop files) are the equivalent to Windows shortcuts. I can't remmeber which was the problem exactly, but you can search for how to make a well formed .desktop file.

---

### Post by Ectara on 2009-05-21
My .deb does not use .desktop files, rather simply installs a library and two symlinks into the /usr/lib/ folder. Not quite sure what the problem is. Currently trying to work with the debian package tester applications.

---

