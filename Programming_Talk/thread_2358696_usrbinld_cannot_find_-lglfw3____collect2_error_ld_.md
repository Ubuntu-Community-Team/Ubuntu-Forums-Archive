---
title: "/usr/bin/ld: cannot find -lglfw3    collect2: error: ld returned 1 exit status"
date: 2017-04-16
forum: Programming Talk
---

### Post by Rahul04789 on 2017-04-16
Hi All,

I compiled an OpenGL (.cpp) programme and I got the following error:

compilation: # g++ ex1.cpp -o ex1 -lGLEW -lglfw3 -lGL -lX11 -lXi -lXrandr -lXxf86vm -lXinerama -lXcursor -lrt -lm -pthread -ldl -std=c++11

error:

/usr/bin/ld: cannot find -lglfw3
collect2: error: ld returned 1 exit status

I have already installed libglew-dev package.

Regards,

---

### Post by steeldriver on 2017-04-16
What about **libglfw3-dev** ?

---

### Post by Rahul04789 on 2017-04-17
Yes libglfw3-dev is also installed.

---

### Post by &amp;KyT$0P# on 2017-04-17
I had a similar problem compiling software, and the issue was that I was doing a static build which needed libraries that weren't available in [FONT=Courier New].a[/FONT] format.

Could something like this be happening to you?

Also, does directly running [FONT=Courier New]ld[/FONT] (adding your own custom [FONT=Courier New]ld[/FONT] flags) give any insight? -
```
ld -lglfw3 --verbose
```

---

