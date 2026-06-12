---
title: "Sometimes my Desktop goes blank"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by CrimpJiggler on 2011-12-18
Every now and again all the icons on my desktop disappear for some reason. Sometimes when this happens, the topbar and bottom bar disappears too and this was a real pain but eventually I figured out that gnome-panel is the process that controls the topbar and bottom bar in Ubuntu and that to get them back, I just need to run gnome-terminal. What process controls the desktop icons? The desktops background is still there, its just the icons that are missing. When I restart the computer it will go back to normal but I wanna figure out how to get the icons back without restarting the comp.

---

### Post by durand on 2011-12-18
Its called nautilus, which is also the file manager. If you open a folder, it will bring your icons back. Otherwise, press alt + f2 and run nautilus. This isn't supposed to happen though so its crashing for one reason or another...

---

### Post by BC59 on 2011-12-18
What version of Ubuntu you are using and what type of Graphics card? Did you install the proprietary drivers?

---

### Post by CrimpJiggler on 2011-12-18
durand: Ah right, that makes sense. Next time it happens I'll kill nautilus and restart it. Opening a folder doesn't bring the desktop icons back though. This always happens when I'm using nautilus to read or write to an external harddrive. Just before I started this thread, nautilus crashed and prevented me from unmounting the external harddrive and I couldn't even stop it with the kill command. On another thread, someone suggested I run "killall -9 nautilus" so I'll try that next time.

BC59: I'm running Ubuntu 11.04 but this has been happening for years so the issue isn't just this version. I didn't install any drivers as far as I know. As for my graphics card, heres what lspci says:
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)


---

### Post by BC59 on 2011-12-18
Your graphics card having compatibility problems with Compiz. If you are using special effects just uninstall them to avoid the crashes.
The easy way to reset the desktop and get back the icons is to run on a terminal CTRL+ALT+T:

```
unity --reset
```
and if not working
```
unity --reset-icons
```

---

