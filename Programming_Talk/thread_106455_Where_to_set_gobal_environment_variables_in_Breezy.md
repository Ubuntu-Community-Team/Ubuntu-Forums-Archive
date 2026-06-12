---
title: "Where to set gobal environment variables in Breezy?"
date: 2005-12-20
forum: Programming Talk
---

### Post by mmcmonster on 2005-12-20
Hi.
  I just compiled wxWidgets, which put its libraries in /usr/local/lib.  I then compiled a program that used those libraries, which of course it could not find.  If I add /usr/local/lib to my LD_LIBRARY_PATH in my .bashrc, the program works fine if I fun it from a terminal window.

My question:
  In breezy, how can I add /usr/local/lib to the global LD_LIBRARY_PATH (for all users, without having them run the application from a terminal window (so adding to .bashrc is out))?

I tried adding the following to ~/.gnomerc, but it didn't work:
```
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
```

I tried adding the following to /etc/environment, but it didn't work:
```
export LD_LIBRARY_PATH=/usr/local/lib
```
I also tried the following in /etc/environment with no success.
```
LD_LIBRARY_PATH=/usr/local/lib
```

I also appended the following to /etc/profile with no luck:
```
export LD_LIBRARY_PATH=/usr/local/lib:$LD_LIBRARY_PATH
```

As you can see, I am pretty much at my wit's end.  Any ideas?

---

### Post by LordHunter317 on 2005-12-20
You shouldn't set LD_LIBRARY_PATH by default at all, but rather edit /etc/ld.so.conf and then run sudo ldconfig.

---

### Post by mmcmonster on 2005-12-20
Thank you! Thank you! Thank you!

I placed the following in /etc/ld.so.conf:
/lib
/usr/lib
/usr/X11R6/lib
/usr/local/lib

Everything works great now. :-)

I guess I just have to add what I want, and all the defaults will be added automatically? (eg: I don't have to worry about directories missing, right?)

---

