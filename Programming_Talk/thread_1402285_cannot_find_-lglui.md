---
title: "cannot find -lglui"
date: 2010-02-09
forum: Programming Talk
---

### Post by nitinrao on 2010-02-09
hi,
im trying to compile a cpp file, which makes use of OpenCV & openGL libraries. however, on giving this command :

**test@test-desktop:~/Desktop/server$ g++ -I/usr/include/GL -I/usr/local/include/opencv -L /usr/local/lib -lcxcore -lcv -lhighgui -lcvaux -lml -I/usr/X11R6/include -L/usr/X11R6/lib -o sample sample.cpp -lglui -lglut -lGLU -lGL -pthread**

i get the following error message :
[B]/usr/bin/ld: cannot find -lglui
collect2: ld returned 1 exit status[/B]

can anyone help me out?
thanks.

[solved]
had to install "libglui-dev" to make it work!

---

### Post by Bachstelze on 2010-02-09
You need, surprisingly rnough, [font=monospace]libglui-dev[/font]. ;)

*EDIT: eh, didn't see the edit...*

---

