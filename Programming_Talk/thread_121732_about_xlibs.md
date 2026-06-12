---
title: "about xlibs"
date: 2006-01-25
forum: Programming Talk
---

### Post by teko80 on 2006-01-25
I have installed xlibs 6.8.2-10. Is correct this package substitutes xlib?
And the question is where are the xlib header files? I didnt found it in /usr/include/X11. There is only two directories in it (bitmaps and pixmaps) without files with .h suffix.

---

### Post by asimon on 2006-01-26
[QUOTE=teko80]I have installed xlibs 6.8.2-10. Is correct this package substitutes xlib?[/quote]
Actually, the correct package is [libx11-6](http://packages.ubuntu.com/breezy/libs/libx11-6). [xlibs](http://packages.ubuntu.com/breezy/libs/xlibs) is only a transitional package to ensure a smooth upgrade from hoary to breezy. You should be able to safely remove this package (if you have Breezy installed).

[QUOTE=teko80]
And the question is where are the xlib header files? I didnt found it in /usr/include/X11. There is only two directories in it (bitmaps and pixmaps) without files with .h suffix.[/QUOTE]
For the headers you need to install libx11-dev. This is a standard with all debian/ubuntu library packages. Header files are always packaged in a seperate package ending with -dev.

---

