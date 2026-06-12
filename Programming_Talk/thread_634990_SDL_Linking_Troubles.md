---
title: "SDL Linking Troubles"
date: 2007-12-08
forum: Programming Talk
---

### Post by FlyingIsFun1217 on 2007-12-08
Hey!

I've been using SDL in windows for quite a while now on my project. After finally figuring out why the wireless connection wasn't working in Xubuntu (it was set to wep instead of wpa!), I'm trying to get it set up in Xubuntu.

I've gone through the setup process described in [this guide]("http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development"), with the Code::Blocks project that I was using on windows (modified to look more like the SDL template in Xubuntu). Funny thing is though, I seem to get OpenGL linking errors, even when I get no errors about failed linking!

> :: === SGT, default ===
obj/Release/main.o:: In function `SGE::draw()':
main.cpp:(.text+0xcd):: undefined reference to `glClearColor'
main.cpp:(.text+0xd9):: undefined reference to `glClear'
main.cpp:(.text+0xde):: undefined reference to `glLoadIdentity'
main.cpp:(.text+0xea):: undefined reference to `glMatrixMode'
main.cpp:(.text+0xef):: undefined reference to `glLoadIdentity'
main.cpp:(.text+0x15a):: undefined reference to `glOrtho'
main.cpp:(.text+0x166):: undefined reference to `glMatrixMode'
main.cpp:(.text+0x16b):: undefined reference to `glLoadIdentity'
main.cpp:(.text+0x177):: undefined reference to `glPointSize'
main.cpp:(.text+0x183):: undefined reference to `glBegin'
main.cpp:(.text+0x193):: undefined reference to `glVertex3f'
main.cpp:(.text+0x1ba):: undefined reference to `glVertex3f'
main.cpp:(.text+0x1e0):: undefined reference to `glVertex3f'
main.cpp:(.text+0x209):: undefined reference to `glVertex3f'
main.cpp:(.text+0x231):: undefined reference to `glVertex3f'
main.cpp:(.text+0x236):: undefined reference to `glEnd'
obj/Release/main.o:: In function `util::logInfo()':
main.cpp:(.text+0xa22):: undefined reference to `glGetString'
main.cpp:(.text+0xa5a):: undefined reference to `glGetString'
main.cpp:(.text+0xa92):: undefined reference to `glGetString'
:: === Build finished: 19 errors, 0 warnings ===


Any thoughts to this? Thanks!

FlyingIsFun1217

---

### Post by Wybiral on 2007-12-08
Make sure you have the Mesa OpenGL development files (you can get them from synaptic). Are you using Code::Blocks to compile it?

---

### Post by Auria on 2007-12-08
You need to link against OpenGL (lib name : GL, e.g. -lGL IIRC)

---

### Post by FlyingIsFun1217 on 2007-12-08
Interesting...

It shows '`sdl-config --libs`' under 'Other Linker Options'.
How can I add OpenGL?

FlyingIsFun1217

---

### Post by geirha on 2007-12-08
```
`sdl-config --libs` -lGL
``` should do it

---

### Post by FlyingIsFun1217 on 2007-12-08
Thanks, that seemed to do the trick!

FlyingIsFun1217

---

