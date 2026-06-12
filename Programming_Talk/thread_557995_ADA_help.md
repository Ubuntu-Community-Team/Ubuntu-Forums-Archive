---
title: "ADA help"
date: 2007-09-23
forum: Programming Talk
---

### Post by Havek on 2007-09-23
I went through the process of installing ADA but have come across a problem.  Right now i use jGrasp because thats what my professor prefers us to use.  Now my jGrasp will compile an ADA 95 code, but gives me warnings and can't find my .ads when compiling ADA 2005 code.  Did i only install ada 95 and how to i go about installing ada 2005?

---

### Post by samjh on 2007-09-23
If you do:
```
sudo apt-get install gnat
```
that will give you the latest GNAT Ada compiler, which includes full support for Ada 86, 95, and 2005.

I've never used jGrasp, so I cannot help you as far as the workings of that IDE/editor is concerned.

To compile an Ada source file via command line, do something like this:
```
gnat make myprogram.adb
```where myprogram.adb is your source file.

---

### Post by Havek on 2007-09-23
Thank you, if that does install the latest one then i already had it installed.  I am just confused as to why jGrasp can't find the .ads when they are in the same directory?  Do you know of any other IDE that support ADA?

---

### Post by samjh on 2007-09-24
> **Havek said:**
> Thank you, if that does install the latest one then i already had it installed.  I am just confused as to why jGrasp can't find the .ads when they are in the same directory?  Do you know of any other IDE that support ADA?

If you're using Ubuntu, Gedit supports Ada.  It is part of the standard software install for Ubuntu.

One of my favourite editors for both *nix and Windows is Scite.  You can install it on Ubuntu by doing```
sudo apt-get install scite
```Alternatively, you can obtain an executable for Windows at [http://scintilla.sourceforge.net/SciTEDownload.html](http://scintilla.sourceforge.net/SciTEDownload.html)

The most powerful Ada IDE is GPS (GNAT Programming Studio), which can be installed on Ubuntu with this command:```
sudo apt-get install gnat-gps
```However I think a full-blown IDE for what seems to be an introductory Ada course is probably too much.  Learning gnat on the command-line is relatively easy.

---

