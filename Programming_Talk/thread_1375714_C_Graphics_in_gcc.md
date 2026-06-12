---
title: "C Graphics in gcc"
date: 2010-01-08
forum: Programming Talk
---

### Post by Krunal_p on 2010-01-08
Hi, I am not very familiar  with GCC. Can you please tell me how to do graphics programs in GCC like draw  circles,ellipse and all that stuff ?

Is there any equivalent header file of "Graphics.h" of TurboC in GCC?

:popcorn:

---

### Post by riksweeney on 2010-01-08
Have you done any C programming at all? Most people would probably use a framework such as SDL to do graphics.

---

### Post by PmDematagoda on 2010-01-08
[Cairo]("http://www.cairographics.org/documentation/") may be what you are looking for.

---

### Post by Krunal_p on 2010-01-08
thanks for telling abt cairo

---

### Post by wmcbrine on 2010-01-08
In short, there is no standard for graphics in C, and nothing gcc-specific, either. So you're looking at add-on libraries. SDL is one of the simplest to work with, although lines, circles, etc. aren't its strong suit (it's focused on blitting bitmaps). I've heard good things about Cairo, but I haven't tried it.

---

### Post by skullmunky on 2010-01-09
this one's C++, rather than C, but look at 

[http://www.openframeworks.cc/]("http://www.openframeworks.cc/")

---

