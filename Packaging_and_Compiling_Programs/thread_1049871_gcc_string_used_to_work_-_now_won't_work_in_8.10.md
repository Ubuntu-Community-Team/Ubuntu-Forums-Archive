---
title: "gcc string used to work - now won't work in 8.10"
date: 2009-01-25
forum: Packaging and Compiling Programs
---

### Post by anewguy on 2009-01-25
I have a shell script which I used to compile a program of mine, but when I had to delete and later re-install 8.10 (along with it's 250+ updates) the script no longer works. The line from the script the fails is:


gcc -Wall -g -o cvsutil_gtk *.c `pkg-config --cflags --libs gtk+-2.0 libglade-2.0` -lusb


It errors out saying it can find gtk+-2.0 and libglade-2.0 and that I need to change the pkg-config search path.  I have looked and no longer see gtk+-2.0, nor do I see libglade-2.0 (not sure I need it anyway).  I would really like 2 things:

- an explanation and fix for why it fails now (worked before in 8.10, but I had remove it for a while)

- some kind of guidance on how to make this "update" proof - it ran in 7.10, 8.04 and 8.10 before until now.

Thank you in advance!
Dave :)

---

### Post by jpkotta on 2009-01-25
You need to install the -dev packages for those libraries.  Use your favorite package manager to search for packages like libgtk2.0-dev, libglade2-dev, libusb-dev, etc.

It should always be update proof, because updates should keep packages installed, only bump the versions.  No way to make it reinstall proof, because a reinstall won't install -dev packages.

---

### Post by anewguy on 2009-01-25
> **jpkotta said:**
> You need to install the -dev packages for those libraries.  Use your favorite package manager to search for packages like libgtk2.0-dev, libglade2-dev, libusb-dev, etc.

It should always be update proof, because updates should keep packages installed, only bump the versions.  No way to make it reinstall proof, because a reinstall won't install -dev packages.


Thanks for the reply.  I believe I already have all the libs installed:

glade 2.12.1-0ubuntu1
glade-3 3.4.5-0ubuntu1
glade-common 2.12.2-0ubuntu
glade-doc 2.12.2-0ubuntu1
glade-gnome3 3.4.5-0ubuntu1

didn't install glade-gnome, as it says it will remove glade2

libgladeui-1-7
libgladeui-1-dev


libgtk1.2-dev
libgtk2.0-dev

libusb-0.1-4
libusb++-0.1-4c2
libusb-dev
libusb++-dev


Note that gtk+-2.0 no longer shows in the package manager, and looking in /usr/lib and /usr/include, there is nothing there for it, only 1.2 and 2.0.  Putting gtk2.0 in the gcc string still results in the same failure.

Glade I'm not too worried about, as I really don't think I need it - only the GTK stuff.

Libusb should still work, but can't get far enough into a compilation to see if it finds the header.

The way I understand things, the gcc line I currently have says to look for includes in /usr/include/gtk+-2.0 and in /usr/include/glade-2.0 (unless I somehow now need to set an include path I didn't have to set before).  the header file for GTK is in the path /usr/include/gtk-2.0/gtk, and the include lines in the C code look like #include <gtk/gtk.h>.  This would indicate I need to change the gcc line to gtk-2.0
but that doesn't work either.  There is no glade-2 in the include or lib folders in /usr.  Glade-3 is /usr/lib, but it doesn't seem to work either.

So, the biggest thing I'm fighting at this point, just to try to get the compilation started, is getting it to find gtk/gtk.h.  

Like I said, this all worked before including in 8.10.  I had to remove 8.10 for work purposes (job was temp, now done, so I've re-installed 8.10).  The only thing I can think of that might have changed is the 250+ updates.  I didn't try the compile with just the "bare" 8.10 as loaded.

This has me confused and worried.  It's supposed to be an open-source project, so others need a clean way to compile as well.  It's cross-platform - runs with GTK in Windows XP Pro and at least USED to run in ubuntu 8.10.  Just need to get it back working 8.10.

Any help is appreciated!!

Dave :)

---

### Post by bruce89 on 2009-01-25
> **anewguy said:**
> 
glade 2.12.1-0ubuntu1
glade-3 3.4.5-0ubuntu1
glade-common 2.12.2-0ubuntu
glade-doc 2.12.2-0ubuntu1
glade-gnome3 3.4.5-0ubuntu1

libgtk1.2-dev
libgtk2.0-dev

libusb-0.1-4
libusb++-0.1-4c2
libusb-dev
libusb++-dev


You need to install libglade2-dev, not glade itself. Also, you don't need the ancient libgtk1.2-dev or the C++ bindings to libusb.

---

### Post by anewguy on 2009-01-25
Actually, I found I didn't need glade in the thing at all - I think it was left over from my very first gtk program following a tutorial on the web.  I still don't really understand some of this much, but I found if I just plain removed the reference to glade on the gcc line, everything worked fine.  I had to check my windows build procedure, because I got to thinking "hey, I don't have glade in windows", and sure enough I didn't reference there and the same code worked fine - so I just removed it here.

I've tried looking at the man pages, etc., but right now I'm just too stupid on some of this - I really wish I knew how to make a configure script and makefile for this whole mess.  I ran pkg-config gtk+-2.0 to see what it output, so I knew then the gtk+-2.0 must have still been valid - gave me a clue that the glade part might have been messing up the whole include string (i.e., if one of the paths not found, NO path is generated for the entire string, including the gtk stuff).

So, thanks for the help!!  Everything is back to working now.  I wanted to leave the c++ stuff in (like the libusb++_dev) since at some point I want to try to get a handle on C++.  Had a course years ago on the differences, but it only handled things like stdin/out, etc., nothing on object orientation, etc..  So I hope to learn someday.  My regular C is so lousy now (too many years with out using it - 12 to be exact) that I need to re-learn half of it yet.

Thanks everyone!!

Dave :)

In addition, there is no libglade2-dev in my synaptic package manager.

---

