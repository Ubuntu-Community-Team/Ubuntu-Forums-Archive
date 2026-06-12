---
title: "[SOLVED] OpenGL issue"
date: 2007-07-22
forum: Programming Talk
---

### Post by gustavocm on 2007-07-22
Hi
I compiled an OpenGL code i got from [NeHe]("http://nehe.gamedev.net"), everything went fine, but when i tried to run it i got the message:

```

Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
XF86VidModeExtension-Version 32767.850104872
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Segmentation fault (core dumped)

```

it is compiled with these options:
**-L/usr/X11R6/lib -lGL -lGLU -lXxf86vm**

What can i do to solve this problem?

---

### Post by AlexThomson_NZ on 2007-07-22
Do you need the -lXxf86vm bit on the end of the compile options?

---

### Post by hod139 on 2007-07-22
Are you using the closed source video drivers or the open source?  What video card?  What is the code that is causing the error?

---

### Post by gustavocm on 2007-07-24
> Do you need the -lXxf86vm bit on the end of the compile options?

yes, i need it

> Are you using the closed source video drivers or the open source? What video card? What is the code that is causing the error?

I have an ATI radeon xpress 200M. I installed it with the Restricted Driver Manager. Maybe this is the problem. What can i do?

---

### Post by slavik on 2007-07-24
append DISPLAY=:0 before running the program, seems to be like you have a glx session running

---

### Post by gustavocm on 2007-07-25
that's it!
thank you

---

