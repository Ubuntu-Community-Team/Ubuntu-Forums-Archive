---
title: "GTKMM Help"
date: 2007-07-20
forum: Programming Talk
---

### Post by azan00 on 2007-07-20
Hello I am attempting to get GTKMM working... but the compiler cannot find gtkmm.h ...

As far as I know gtkmm is installed correctly, doing a pkg-config gtkmm-2.4 --cflags --libs works. But when I compile it with g++ gui.cpp -o gui `pkg-config gtkmm-2.4 --cflags --libs` I get the not found error.

I have been searching around for quite a while, but have not been able to fix it. My first conclusion was that I needed to set an environment variable, is that the case? Any help would be appreciated. :)

---

### Post by talowe on 2007-07-21
No environment variable needed here.  Some source code and exact error message from compiler might help to diagnose problem.

---

### Post by azan00 on 2007-07-21
Well this is weird, I got up this morning to recreate the error message to show you guys. But when I ran the same thing that had been giving me errors it works just fine. Must've just needed a reboot.

---

### Post by rekahsoft on 2007-07-21
It is recommended that you do not use gtkmm.h for larger programs because it included a couple Mb of headers. Include individual headers like so:```
#include<gtkmm/button.h>
#include<gtkmm/window.h>
```btw the easiest way to compile is:```
g++ -o main source.cc `pkg-config --cfags --libs gtkmm-2.4`
```

---

