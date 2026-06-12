---
title: "Quad-Ren 0.4"
date: 2009-04-12
forum: Programming Talk
---

### Post by hessiess on 2009-04-12
Quad-Ren is a resolution independent 2D graphics engine that aims to ease the development of bitmap-based applications, primarily games. Applications using Quad-Ren will function the same regardless of screen resolution or aspect ratio, windowed or fullscreen.

Version 0.4 adds a number of features, one being an event system, providing a cleaner method of reading user input. It also adds a new scene node, qr_line.

The example program has bean moved out of the main release into its own package, and 2 more examples have bean added, a simple "hello world" style program and an example of the usage of the event system.

There have also bean a number of bug fixes, most notably to the PNG loader, which will no longer load images without an alpha channel and are not a power of two.

QR 0.4 can be downloaded from [www.quad-ren.sourceforge.net.]("http://quad-ren.sourceforge.net")

---

### Post by jimi_hendrix on 2009-04-12
cool

does it work on windows too? i know you use sdl (or was it opengl) as a base but i am curious

---

### Post by hessiess on 2009-04-13
Should do if you want to compile it.

---

