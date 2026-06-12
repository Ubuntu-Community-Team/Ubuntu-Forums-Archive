---
title: "how to know which prog are nessary in a session"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by blake7 on 2008-09-01
hi is thier a way of just running the minmum programs from boot
how can i tell which progams iam useing and which are just thier from a past moment.

like what is compiz, jockey, paclt load...... and nautilus.

is thier  away i can copy and past running programs just so that i can do this prosses quicker.

thank
ps is thier a default minimum program at start up so i can

---

### Post by cwsnyder on 2008-09-01
Linux does not load a lot of programs in the background, as Windows does.  For example, in my startup, only the system clock, shutdown wizard, volume control,network connection and Bluetooth connection, start.  You could eliminate the system clock, but why would you do this if you have more than 128 M of RAM?

Are you trying to start your system in a configuration with less than 512 M of RAM?  Have you looked at Xubuntu?

To your specific questions: Compiz is an display manager for Gnome or KDE which adds specific gee-whiz nice stuff in making the display look nicer.  Nautilus is the Gnome specific file manager program which will start up when you click one of the destinations in the Places menu.  I am not familiar with jockey or paclt load.

Most of the time involved in the boot process is involved in checking your hardware and seeing if there have been any changes.

There are distributions which do not check the hardware, because you have to re-compile your GNU/Linux kernel when you change anything significant, such as Gentoo.  I haven't heard that they are significantly faster in booting, however.  You could start with the source for Ubuntu and re-compile to eliminate parts of the hardware driver files not needed for your system, if you wish.  Or you could simply try a distribution like Damn Small Linux, Feather Linux, Puppy Linux, or NimbleX which uses a very small memory footprint and do, therefore, boot faster.  They do so at the cost of reduced function.

cwsnyder

---

### Post by blake7 on 2008-09-01
it really because i like to be intouch with whats going on and i like to be effectent, where possible..

thank you for your time

---

### Post by unutbu on 2008-09-01
Here is a guide for turning off certain processes that are run at boot time:
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

If you type```

pstree
``` or
```

ps auxw
```
you will see a list of all the processes currently running on the system. System>Administration>System Monitor also works.

System>Preferences>Sessions shows which programs are started when you log in. None of them are strictly necessary -- but you may wish to keep some of them like "Volume Manager" if you wish USB flash drives to be automounted.

---

