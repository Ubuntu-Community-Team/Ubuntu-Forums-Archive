---
title: "Unable to compile openGL programs :("
date: 2008-08-20
forum: Programming Talk
---

### Post by mkartic on 2008-08-20
hey guys, am trying to learn openGL for doing a college project. I followed the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=375425&highlight=glut](http://ubuntuforums.org/showthread.php?t=375425&highlight=glut)

It got compiled fine, but when i try to run it, am getting errors! can someone help me out please?:confused:

jeez@jeez-desktop:~/Desktop/openGL$ g++ bla.cpp -lglut
jeez@jeez-desktop:~/Desktop/openGL$ ./a.out
freeglut (./a.out): OpenGL GLX extension not supported by display ':0.0'

thanks!

[edit]
[http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/](http://amazingrando.wordpress.com/2007/04/10/compiling-and-using-newest-nvidia-drivers-in-ubuntu-its-easier-than-you-think/)
I followed that link and my problem's now fixed! thanks guys :)

---

### Post by slavik on 2008-08-20
what video card and driver are you using and do you have direct rendering? (what does `glxinfo | grep direct` say?)

---

### Post by jespdj on 2008-08-21
> **mkartic said:**
> It got compiled fine, but when i try to run it, am getting errors! can someone help me out please?
Then why is the title of your post "Unable to **compile** OpenGL programs"?

---

### Post by mkartic on 2008-08-21
> **jespdj said:**
> Then why is the title of your post "Unable to **compile** OpenGL programs"?

fat help, thanks! :)


@slavik:
jeez@jeez-desktop:~/stuff/VTK/bin$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Same error! :(
And i tried installing vtk, and wen i tried running an example, i got the same error! I have an nVidia 8500GT gcard! 
how do i check the version of the driver??

---

### Post by Zugzwang on 2008-08-21
mkartic, this is the wrong forum for these problems as it appears as you didn't set up your graphic drivers correctly. Did you try installing the proprietary drivers? The respective menu entry is somewhere in the GNOME menu...

---

### Post by slavik on 2008-08-21
> **mkartic said:**
> fat help, thanks! :)


@slavik:
jeez@jeez-desktop:~/stuff/VTK/bin$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Same error! :(
And i tried installing vtk, and wen i tried running an example, i got the same error! I have an nVidia 8500GT gcard! 
how do i check the version of the driver??
what are the results of `grep driver /etc/X11/xorg.conf`

---

### Post by mordox on 2008-08-21
Try this:

[http://www.linuxforums.org/forum/linux-desktop-x-windows/32497-glx-extension-missing.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/32497-glx-extension-missing.html)



Also check if you have the correct driver selected in xorg.conf.   

U can let X -configure for X11 to detect the settings.

---

