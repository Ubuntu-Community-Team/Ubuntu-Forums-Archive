---
title: "program with frame buffer"
date: 2009-11-06
forum: Programming Talk
---

### Post by lwhat on 2009-11-06
Ubuntu 9.10, I have /dev/fb0.
I try a tutorial c source code, and it works on the
embedded board, and works on the PC in my lab as well,
but on my own PC (Ubuntu 9.10) I met the following problem
 
fd=open("/dev/fb0",O_RDWR);    is OK
 
ioctl(fd,FBIOGET_VSCREENINFO,&vinfo);  always error

My task is to draw a point or line,
and I know something about frame buffer.
 
sorry for my poor  English

---

