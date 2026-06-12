---
title: "rc.local, SVGALIB, auto start program"
date: 2011-02-10
forum: Programming Talk
---

### Post by sunruh on 2011-02-10
I have an embedded PC104 application where I am trying to get my program to start automatically at power up. The program contains a graphical user interface, using an old SVGALIB (no longer supported). It works fine if I start it after log in.

But when I put the path in rc.local, it will only run if I disable all the graphical stuff. The program bunts if it looks ahead and sees the call to vga_setmode(), where I set it for 480 x 640 resolution.

I have also noticed on programs I can get to run from rc.local, the printf() and getchar() function do not work.  I don't need these, but suspect it is a related problem.

---

### Post by NIT006.5 on 2011-02-20
> **sunruh said:**
> 
I have also noticed on programs I can get to run from rc.local, the printf() and getchar() function do not work.  I don't need these, but suspect it is a related problem.

I would also really love a solution to this, because I also need printf to work from a script which is called from rc.local. After several days of driving myself insane, I'm still no closer to finding out why it won't work.

---

