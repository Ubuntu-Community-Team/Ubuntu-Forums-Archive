---
title: "Using GTK in Windows"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by anewguy on 2008-10-17
I have a couple of programs I have written that use libusb and GTK in Ubuntu.  Does anyone have any experience there with using the GTK package for Windows and the libusb package for Windows?

Thanks in advance,
Dave :)

---

### Post by dgoosens on 2008-10-17
as you can see here:

[http://www.gtk.org/download.html]("http://www.gtk.org/download.html")

the GTK library is available for Windows...

---

### Post by anewguy on 2008-10-17
I was hoping to find someone who can guide me with the Windows syntax for using gcc (I installed mingw), libusb (have a Windows version installed) and GTK for Windows (I have it installed).  The things I have done with this in Ubuntu have just used simple make and make install, or I've cc'd them myself.

I'd like to know the Windows syntax for gcc when the source resides in the current folder, libusb is in folder "x" and GTK is in folder "y".

I know that cc *.c -o xxxx -l/x/libusb.lib;/y/GTK/ doesn't work.

Any additional help would be appreciated.

Dave :)

---

