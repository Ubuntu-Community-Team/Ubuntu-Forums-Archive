---
title: "CPU 100% all the time."
date: 2008-07-19
forum: New to Ubuntu
---

### Post by XxUn70ucHaBlExX on 2008-07-19
My cpu is at a constant 100% for some reason. I can't figure out why. Can anyone help please?

Screenshot post:

[http://img380.imageshack.us/img380/4959/cpu100gx2.png](http://img380.imageshack.us/img380/4959/cpu100gx2.png)

=[

---

### Post by iaculallad on 2008-07-19
> **XxUn70ucHaBlExX said:**
> My cpu is at a constant 100% for some reason. I can't figure out why. Can anyone help please?

Screenshot post:

[http://img380.imageshack.us/img380/4959/cpu100gx2.png](http://img380.imageshack.us/img380/4959/cpu100gx2.png)

=[

Try to view what applications are eating your CPU resources:

On terminal:

```
top
```

GUI:

System->Administrator->System Monitor, in the "Process" tab.

---

### Post by XxUn70ucHaBlExX on 2008-07-19
Okay I took a screenshot of that.

Screenshot: 
[http://img91.imageshack.us/img91/8617/screenshotqd5.png](http://img91.imageshack.us/img91/8617/screenshotqd5.png)

---

### Post by sharks on 2008-07-19
i think its Firefox

---

### Post by hyper_ch on 2008-07-19
rather it's gnash - the opensource flash replacement... you might be better off installin flash instead of gnash

---

### Post by sharks on 2008-07-19
i think ur eyecandy (theme) takes it.

---

### Post by iaculallad on 2008-07-19
Yap, it's GNASH running on background (Sleeping status). (And before uninstalling it) Try to kill the process name and try running a website built with flash files and try to observe if it eats up your CPU resources.

```
sudo killall gtk-gnash
```

---

### Post by XxUn70ucHaBlExX on 2008-07-19
Wow thank you so much everyone! I really do appreciate all of the help I have been getting over the past few days. Even though I killed gnash my flash and youtube is working, so all is well.

---

