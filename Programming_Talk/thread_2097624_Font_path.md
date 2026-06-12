---
title: "Font path"
date: 2012-12-23
forum: Programming Talk
---

### Post by garth_thompson on 2012-12-23
While trying to change fonts in a c program I get font not found using fixed fonts, how do I set the font path for gcc. When I use xset -q it show the path that my fonts are in.

---

### Post by Bachstelze on 2012-12-23
There is no such thing as "the font path for gcc". You are probably using soem kind of GUI library, so state which one and post some code.

---

### Post by garth_thompson on 2012-12-23
I am compiling using gcc with lX11 the code compiles but when run tell be can not find my font. the code to set the font is:


 #include <X11/Xlib.h>
  3 #include <X11/Xutil.h>
  4 #include <X11/Xresource.h>
  5 #include <stdio.h>
  6 #include <stdlib.h>
  7 #include <string.h>
  8 
  9 GC setup(Display * dpy, int argc, char ** argv, int *width_r, int *height_r,
 10         XFontStruct **font_r){
 11     int width, height;
 12     int screen_num;
 13     unsigned long background, border;
 14     Window win;
 15     GC pen;
 16     XGCValues values;
 17 
 18     char * fontname;
 19     XFontStruct *font;
 20     Colormap cmap;
 21     XColor xc, xc2;
 23     screen_num = DefaultScreen(dpy);
 24 
 25     cmap = DefaultColormap(dpy, screen_num);
 26 
 27     XAllocNamedColor(dpy, cmap, "DarkGreen", &xc, &xc2);
 28     background = xc.pixel;
 29     XAllocNamedColor(dpy, cmap, "LightGreen", &xc, &xc2);
 30     border = xc.pixel;
 31     XAllocNamedColor(dpy, cmap, "Red", &xc, &xc2);
 32     values.foreground = xc.pixel;
 33 
 34     fontname = "Ubuntu-L";
 35     font = XLoadQueryFont(dpy, fontname);
 36     if (!font) {
 37         fprintf(stderr, "unable to load preferred font: %s using fixed\n", f    ontname);
 38         font = XLoadQueryFont(dpy, "fixed");
 39     }

when the program runs font is not set so the if statement set the font to fixed trying to find a way to get the compiler to find my font.

---

