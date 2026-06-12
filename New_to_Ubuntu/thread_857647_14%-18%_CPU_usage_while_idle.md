---
title: "14%-18% CPU usage while idle?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by kool_kat_os on 2008-07-12
I have a Intel Pentium 4 2.8 GHz Hyperthreaded ....and when im idle system monitor shows my that my cpu usage for both core's is 14 to 18 percent.

Is that normal? sometimes it gets higher.

here is a screenshot...

[[IMG]http://img187.imageshack.us/img187/8246/screenshotzb5.th.png[/IMG]](http://img187.imageshack.us/my.php?image=screenshotzb5.png)

(does anyone know how to make is so it only captures the title bar and the windows...?If i press alt it only captures the inside of the windows ...not hte title bar.






Thanks

---

### Post by sdennie on 2008-07-12
There is a bug with the gnome-system-monitor where it uses a lot of CPU to report the CPU usage.  Try instead running top or htop in a terminal.

---

### Post by ibuclaw on 2008-07-12
+1 Vor...

Why do you always beat me on these threads? ;)

If you want to know your wattage and interrupts while idle, use powertop.

But, first, test that your CPU is compatible.
```
test -d /sys/devices/system/cpu/cpu0/cpufreq && echo YES || echo NO
```
If the above gives the answer "YES", then install powertop
```
sudo apt-get install powertop
```
And run it for a minute.
```
sudo powertop -t 60 -d
```
else ignore the above, because it won't be of much use to you.

Regards
Iain

---

### Post by kool_kat_os on 2008-07-12
it says no :-(

---

### Post by kool_kat_os on 2008-07-12
here's the output of "top"

---

### Post by sdennie on 2008-07-12
That seems perfectly normal for an idle system.  You may also want to try htop in a terminal:

```

sudo apt-get install htop
htop

```

---

### Post by kool_kat_os on 2008-07-12
Whats different about htop?

---

### Post by alienexplorers on 2008-07-12
Don't worry to much my old machine runs at 60 to 70% cpu usage when idle.  Not bad LOL.

---

### Post by sdennie on 2008-07-12
> **kool_kat_os said:**
> Whats different about htop?

It's a bit more colorful and some people find it more useful and easier to read.

---

### Post by kool_kat_os on 2008-07-12
oooooo.....htop is colorful

EDIT: oh..you already said that :-)

---

### Post by kool_kat_os on 2008-07-12
ok...now i have another mystery i wanna solve...

in this screenshot...im running superpi...but only one core is getting used...why is that?

---

### Post by sdennie on 2008-07-12
The application must be single threaded.  Applications have to written a certain way to utilize more than one core.  There may be a command line option to make it utilize more than one core though.

---

### Post by kool_kat_os on 2008-07-12
ok...i gotta find it...ON TO GOOGLE!

---

### Post by ibuclaw on 2008-07-12
[EDIT]
Bah, forget it... ;)

---

