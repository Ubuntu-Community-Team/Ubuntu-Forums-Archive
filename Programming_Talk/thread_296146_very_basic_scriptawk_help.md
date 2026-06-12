---
title: "very basic script/awk help"
date: 2006-11-09
forum: Programming Talk
---

### Post by canter690 on 2006-11-09
Hoping this is the appropriate forum.  My programming/scripting skills very basic and I am struggling in trying to complete a simple image management task.

Task:
I have a collection of images in numerous directories under a main directory - eg Pictures.

Each image/file most likely has a unique name eg IMG003.JPG

I want to change the name of each file to the format YYYYMMDD-HHMMSS.JPG (taken from the dateandtime data within the exif header) and the store each file in a directory structure which looks like Pictures/YYYY/MM/DD

I have used jhead (a utility found in the repositories to manipulate the exif information of an image) to do the renames 
eg "find . -type f -exec jhead  -n%Y%m%d-%H%M%S {} \;" 
and started with some basic awk to strip out the YYMMDD part of the name but thats about as far as I have been able to get and would really like some assistance.

I figure this would be a useful utility for others and was hoping that this thread could become the start of this simple little program. 

It could be as simple as a shell script or perl but leave that open.

Anyone interested in contributing and helping out ?

Cheers

---

### Post by ciscosurfer on 2006-11-09
You can always try **KRename**, which can be found in the universe repository.  It runs in a GUI and has a KDE feel (uses the Qt toolkit).

If you want something that's command line, you can check the man pages for **rename **or [B]mrename (you need to install mrename).

GPRename[/B], is also very good, is GUI-based and you can grab it at [gnomefiles.org]("http://www.gnomefiles.org/app.php/GPRename") or [sourceforge.net]("http://prdownloads.sourceforge.net/gprename/gprename-1.7.tar.bz2?download"); it's based on Gtk-Perl so you need to have both Perl and libgtk-perl installed to run it.  Installation is straightforward and it's easy to run.

You might also find these helpful:
[http://ubuntuforums.org/showthread.php?t=111350&highlight=batch+rename](http://ubuntuforums.org/showthread.php?t=111350&highlight=batch+rename)
[http://ubuntuforums.org/showthread.php?t=170890&highlight=batch+rename](http://ubuntuforums.org/showthread.php?t=170890&highlight=batch+rename)
[http://ubuntuforums.org/showthread.php?t=163921&highlight=batch+rename](http://ubuntuforums.org/showthread.php?t=163921&highlight=batch+rename)
[http://ubuntuforums.org/showthread.php?t=57189&highlight=batch+rename](http://ubuntuforums.org/showthread.php?t=57189&highlight=batch+rename)

Issuing the following in a terminal should also give you good results (programs to download)```
aptitude search rename
```I hope this information is helpful for you.

---

