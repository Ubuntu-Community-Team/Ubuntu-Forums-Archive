---
title: "Dash Crash"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by dmummert on 2013-02-19
Ubuntu 12.10.  Even from a fresh install, Dash will crash if moused-over.  Sometimes a program can be successfully launched, but most often the cursor freezes and that's the end.  The mouse still works.  From another post, I learned that [Alt-F2] also works, and will kick me out to a terminal - and being absolutely new to Linux, also not very useful to me.  I've learned ways around Dash (Cairo is great!), but there it sits - a landmine at the top of my monitor.

Graphicswise, I am using 8 year old motherboard-integrated Intel video.:frown:

---

### Post by thermion on 2013-02-19
With this kind of hardware, I recommend installing a different desktop.
[MATE]("http://mate-desktop.org/2012/10/16/mate-quantal-repo-available/") should run just fine on your system.

---

### Post by Frogs Hair on 2013-02-19
Try Ctrl + Alt + T to open a terminal and check for Unity support with the following command because of your older hardware.
```
/usr/lib/nux/unity_support_test -p
```

If there is a yes to all questions try to reset Unity 
```
setsid unity
```

---

### Post by dmummert on 2013-02-19
Well, the unity test gave yes answers to all questions, however compiz didn't like it and started Unity emulation in software.  

compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).

WARN  2013-02-19 18:24:40 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.

ERROR 2013-02-19 18:24:43 nux.gestures_subscription GesturesSubscription.cpp:364 Failed to set Geis subscription configuration com.canonical.oif.rotate.timeout

Soooooo - that didn't exactly fly.  But it did spit out lots of error lines.  There were 8 or more of the last error relating to nux.gestures.

---

### Post by mohanzeal on 2013-05-27
hey i was suffering with the same problem and i solved it!! check out this article it may help you [http://forzeal.com/ubuntu-dash-home-crash/](http://forzeal.com/ubuntu-dash-home-crash/)

---

