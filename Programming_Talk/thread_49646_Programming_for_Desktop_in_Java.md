---
title: "Programming for Desktop in Java"
date: 2005-07-17
forum: Programming Talk
---

### Post by index_0@ya.com on 2005-07-17
Hi thr.
          Thx for reading my post.I wanted to program a Desktop Tool for linux like Kde , in Java. 
1>The problem is i dont know whr the boot sequence terminates after which Gnome or Kde starts loading . 
2> After stopping thr, Can i install  X11 and write a simple Jframe program to get any GUI interface? if not wht should i do.. pls help

Waiting eagerly for an ans..

---

### Post by LordHunter317 on 2005-07-17
First off, the scope of something like KDE is absolutely massive, requring mulitple dedicated full-time developers.

You should decide what application(s) you want first, then consider this some more.  Plus, Java may make some things terribly difficult.

You won't be able to write a window manager in Java, for example, without writing a ton of JNI stuff to link to the X11 libraries.  At which point, the value of writing it in Java becomes rather questionable.

As far as the boot sequence, it's not relevant.  USers can start whatever window managers and X applications they want, and graphical login is handled differently (and something you can't do in Java either, see above).

---

### Post by index_0@ya.com on 2005-07-17
hi thr.
     Thx for ur reply ... Well i 'm going try out the lang feature and not to really beat kde!! ..I wanted to test the graphical applications tht goes straight off after the linux startup .
wht if i installed X11 and from the console(without booting to gui like kde or gnome seesion ) can i start Java gui (simple!!) apps ?  wht should i do if not .

waiting eagerly..

---

