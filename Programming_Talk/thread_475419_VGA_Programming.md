---
title: "VGA Programming"
date: 2007-06-16
forum: Programming Talk
---

### Post by bsmith on 2007-06-16
Hi, I'm fairly new to Unix and Ubuntu, and I am just starting to figure out the programming tools included.

I'm coming from a Microsoft background and used to love programming software rendering engine's in good old screen mode 13h, I'm talking the 320x200 8bit indexed color mode.

Anyway, is there an easy way to directly switch to this mode and set up a frame buffer to plot my pixels, or is the only way to use SDL or some other library to handle the messy stuff.:D

Thanks for everything.

---

### Post by ankursethi on 2007-06-16
You could try Ncurses, but that wouldn't automatically get you into fullscreen mode (IE, it will work only inside a terminal). There's also SVGALIB. You can even try programming the framebuffer directly. although there's a library called DirectFB or something that can make things easier.

Check out Google and Wikipedia to know more about these.

---

### Post by the_unforgiven on 2007-06-16
@ankursethi,
No, svgalib is deprecated and mostly not supported anymore.
I don't know about directfb.

@bsmith, what you've been doing is real-mode VGA programming using VESA.
This no longer works in any OS - including Windows (although Windows simulates VESA calls for backward compatibility, but that is really a performance-killer) as almost all modern operating systems are protected mode. You need to use raw system calls to the underlying OS or a supported library that creates an API and hides the dirty work from you. SDL is a good choice and is cross platform.
There are other framebuffer libraries available as well. 
Here is more info on [DirectFB]("http://en.wikipedia.org/wiki/DirectFB").

HTH ;)

---

### Post by bsmith on 2007-06-16
Thanks for the reply s,

Whatever I had been doing was working with Windows XP, but when I switched to Vista I couldn't do anything, especially since my compiler wouldn't work, I think I'll try to learn SDL.

Thanks again.

---

