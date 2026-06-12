---
title: "Im trying to read a pixel colour from the gnome desktop"
date: 2011-06-16
forum: Programming Talk
---

### Post by sensational on 2011-06-16
Hi,


Im after a very simple  way of doing a get pixel on the current gnome desktop.
Ideally in c.

The very best solution would be if I could insert say 4 of 5 lines of assembly code into my c code and then capture the  returned colour values in a variable.

All of the graphic libs ive been looking at like xlib.h and vga.h support the idea of defining a screen and the writing to and reading from it. The is not what im after.

I want to be able to open up a browser with in my current gnome desktop and read the colours of the pixels in the browser window.

Somebody suggested I use opengl. I have also notice there is a robot class in java with getpixel. 
Im not sure if any of these would do what im after ?

Mark.

---

### Post by ziekfiguur on 2011-06-17
As far as I know OpenGL is just for creating graphics, so that's not what you're looking for.
The Java thing might work, another option is to check out the source-code of a program like gnome-screenshot and see how they do it.

---

### Post by Petrolea on 2011-06-17
> **sensational said:**
> Hi,


Im after a very simple  way of doing a get pixel on the current gnome desktop.
Ideally in c.

The very best solution would be if I could insert say 4 of 5 lines of assembly code into my c code and then capture the  returned colour values in a variable.

All of the graphic libs ive been looking at like xlib.h and vga.h support the idea of defining a screen and the writing to and reading from it. The is not what im after.

I want to be able to open up a browser with in my current gnome desktop and read the colours of the pixels in the browser window.

Somebody suggested I use opengl. I have also notice there is a robot class in java with getpixel. 
Im not sure if any of these would do what im after ?

Mark.

Maybe this thread on LinuxForums will help [http://www.linuxforums.org/forum/programming-scripting/60218-how-extract-read-pixel-color-information-bitmap-file.html](http://www.linuxforums.org/forum/programming-scripting/60218-how-extract-read-pixel-color-information-bitmap-file.html)

Or do as the post above me said. Download the source of gnome-screenshot utility, and see how they capture pixels on the screen.

If you can't find nothing else, then this should work:
1. Capture the whole screen (there are tutorials on how to do it with C/C++)
2. Extract pixel from the screenshot (then you might also want to delete the file containing screenhost)

It isn't the most efficient way, but it shouldn't be as hard as reading the pixel directly from screen (which would go pretty "low", since you would have to read from frame buffer).

---

### Post by SeijiSensei on 2011-06-17
You might take a look at how this function is implemented in other pieces of software like the [GIMP]("http://www.gimp.org/source/").  The KDE utility [KColorChooser]("http://www.kde.org/applications/graphics/kcolorchooser/development") also returns the color value of individual pixels.  That might be a better choice of examples since it's limited to precisely the function you're looking to implement.

---

