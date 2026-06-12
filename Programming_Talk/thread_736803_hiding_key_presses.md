---
title: "hiding key presses"
date: 2008-03-27
forum: Programming Talk
---

### Post by nzadLithium on 2008-03-27
Hey

I'm trying to write/modify a program. It directly accesses the keys by reading the input device eg /dev/input/event2

This program is then using what it receives so it can forward different key signals to another program. Only problem is that one of the keys i want to detect then forward a different keycode is the F1 key. However every time i press F1 the ubuntu help program starts. Is there anyway i can block this while the program is running but then still have the ubuntu help program come up by f1 when my program finishes?

I just found out the program kills my hacky program whenever i press a button in it with seg fault errors. It seems what i need to do is stop any programs running from registering the f1, f2, f3, f4, f5, shift and enter keys. (those are all the keys that my hacky program needs :) )

ty

---

