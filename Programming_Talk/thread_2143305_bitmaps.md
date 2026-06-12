---
title: "bitmaps"
date: 2013-05-08
forum: Programming Talk
---

### Post by thedardanius on 2013-05-08
in linux, i try to load a bitmap as my icon for my xlib application.
However, the bitmap is not a valid type deducted from the error values returned.
So what is an xlib bitmap, how do you create these bitmaps?
Apparently they are not the same as normal bmps.

---

### Post by ofnuts on 2013-05-09
[http://www.tronche.com/gui/x/xlib/utilities/manipulating-bitmaps.html](http://www.tronche.com/gui/x/xlib/utilities/manipulating-bitmaps.html)

But when you read between the lines, there is  distinction betwen pixmap (what xlib really uses) and bitmap (data files in a specific format) and there may be way to produce pixmaps from other formats.

And this: [http://stackoverflow.com/questions/346323/xorg-loading-an-image](http://stackoverflow.com/questions/346323/xorg-loading-an-image)

---

### Post by thedardanius on 2013-05-09
then if I want to draw a bitmap xlib myself, which program should i use?
Paint? Gimp?

---

### Post by ofnuts on 2013-05-09
The XBM (Xli b BitMap?) format produced by Gimp seems to match the description in the link above.  But this is a strict "bit map": one bit per pixel (nor color or even grayscale)

---

### Post by xytron on 2013-05-10
> **thedardanius said:**
> then if I want to draw a bitmap xlib myself, which program should i use?
Paint? Gimp?

I think you want icons for your program.

What I would do is create your icons as .ico files (you could even do this in Windows) and then use GIMP to save them as .xpm files which are x pix maps.

X pix maps are used mainly for creating icon pixmaps and they support transparent color.


Once you have your icons use the function XpmCreatePixmapFromData() to load them into your program.

Note that everything that you want to display in an X program needs a window so even an icon will be painted on its own  small window.

Therefore you must create a window for each icon (make those windows the same size as your icons)  and then display those windows (icons) in the usual way inside your main window.

If you want to create something like a toolbar, put your icons windows inside a larger window and then put that window on your main (largest) window.

---

### Post by thedardanius on 2013-05-10
hey

is there any way to load pixmaps without use of external libraries? My goal is to use pure xlib, X11. So can you implemented it yourself?

---

### Post by xytron on 2013-05-10
> **thedardanius said:**
> hey

is there any way to load pixmaps without use of external libraries? My goal is to use pure xlib, X11. So can you implemented it yourself?

You don't have to use an external library to load pix maps.

only include the xpm header file like this;

#include <X11/xpm.h>

as you can see xpm.h is part of the x11 libraries so you are still using pure X11.

---

### Post by thedardanius on 2013-05-10
it cant find the header at mine.
I can find other x11 headers though, so its not a path problem...

edit:

apt-get install libxpm-dev..

missed that. now i got it if it is right

---

### Post by thedardanius on 2013-05-10
guys,

i installed successfully the libxpm-dev package.
However, my compiler (gcc, in this case g++) cant link to the library, causing undefined reference to xpm_a_function
I dont know where my libraries are located, and im not using commandline compiling, but codeblocks IDE.
Please help!

---

### Post by xytron on 2013-05-10
> **thedardanius said:**
> guys,

i installed successfully the libxpm-dev package.
However, my compiler (gcc, in this case g++) cant link to the library, causing undefined reference to xpm_a_function
I dont know where my libraries are located, and im not using commandline compiling, but codeblocks IDE.
Please help!


I can't help with Codeblocks I haven't used it.

Make sure your are including  Xpm in your compile to link so the gcc commnand line is something like;

gcc  -lX11   -lXpm   myprogram.c

Codeblocks should let you specify which libraries to link to someplace.

---

### Post by thedardanius on 2013-05-10
then do you know where xpm lib is situated? absolute path is what I need to fill in in the linker options.

---

### Post by thedardanius on 2013-05-10
I seperatly downloaded libxpm.so or sth like that. The undefined refernece of xpmfunctions are gone, but suddenly, undefined references to __fxstat and so appear. I read somewhere this has to do with the libc version it was compiled for. What should I do? Im lost. The library doesn't work in one or another way.

---

