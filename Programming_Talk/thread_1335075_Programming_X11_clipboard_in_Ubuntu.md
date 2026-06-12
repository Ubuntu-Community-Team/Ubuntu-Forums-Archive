---
title: "Programming X11 clipboard in Ubuntu"
date: 2009-11-23
forum: Programming Talk
---

### Post by Zeemvel on 2009-11-23
Hi,

I made a program that can use the X11 clipboard to paste an image. This programs works good on Archlinux with KDE.

I get an "Atom" which has "image/png" as name, and in Archlinux with KDE this atom has data that is binary data of a PNG image (beginning with those 8 bytes with which every PNG file starts and so on).

In Ubuntu with Gnome, if I press print screen, I get a dialog with a "copy to clipboard" button.

If I press that and run a test program to see which "Atoms" are there, the list is:

TARGETS
MULTIPLE
image/tiff
image/jpeg
image/x-MS-bmp
image/x-bmp
image/bmp
image/png
SAVE_TARGETS
TIMESTAMP

If I then take the one called "image/png" and use the data inside, the data is only 4 bytes in size and definatly not a PNG image.

What's going on here? How can you get the image of the clipboard with Ubuntu?

I'm using C++.

EDIT: btw, this only happens with the print screen thing of gnome. When copying a selection in kolourpaint or gimp, it can be decoded fine with my thingie.

EDIT2: A funny thing is, some Java programs start acting weird too if I use the clipboard in them after having used the Gnome screenshot tool. Is there maybe a bug in the gnome screenshot tool's Copy to clipboard button?

---

### Post by HansdeGoede on 2010-10-05
Hi,

A "bit" late, but I just stumbled over this post. What is happening is that the gnome printscreen tool is sending the image data in small chunks using the INCR property update method, see:
[http://tronche.com/gui/x/icccm/sec-2.html#s-2.7.2](http://tronche.com/gui/x/icccm/sec-2.html#s-2.7.2)

This exactly matches the fact that you are only getting 4 bytes.

Regards,

Hans

---

