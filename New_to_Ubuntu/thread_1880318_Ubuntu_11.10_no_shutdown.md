---
title: "Ubuntu 11.10 no shutdown"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by jimmyjim359 on 2011-11-13
:confused:Okay so i installed ubuntu through the update manager the first time i tried to shutdown the loading screen with the purple dots just kept going and going and going then it switched to a terminal like gui and words were popping up and saying PANIC OCCURED SWITCHING BACK TO TEXT CONSOLE. Very annoying. ANY help would be appriciated. Thanks

---

### Post by TeoBigusGeekus on 2011-11-13
Did this happen again?
Try shutting down from terminal with
```
sudo halt
```
or 
```
sudo shutdown -h now
```
to see if you get any error messages.

---

### Post by LinuxFan999 on 2011-11-13
> **jimmyjim359 said:**
> :confused:Okay so i installed ubuntu through the update manager the first time i tried to shutdown the loading screen with the purple dots just kept going and going and going then it switched to a terminal like gui and words were popping up and saying PANIC OCCURED SWITCHING BACK TO TEXT CONSOLE. Very annoying. ANY help would be appriciated. Thanks
I looked up that message, and it means something very bad, and it is usually preceded by "kernel panic..." Linux kernel 3.0 is very unstable. Please downgrade to 11.04 or 10.04.

---

### Post by lolpenguin on 2011-11-14
Your system went into kernel panic (Blue Screen of Death in Windows terminology) whislt it was shutting down. Linux 3 actuually isn't unstable. Sadly, I cannot help...

---

### Post by carlbastos on 2011-11-14
Instead of using the update manager to perform an upgrade, I would rather make a backup of my home and packages and go for a clean install. Less headaches and no Kernel Panics ;)

---

### Post by jimmyjim359 on 2011-11-15
Okay im an idiot, im not familiar with drives and all that crap. Can you give me a link or something step by step on how to reinstall or downgrade ubuntu 11.10?

---

### Post by jimmyjim359 on 2011-11-15
okay so i just reinstalled and now its doing the same thing

---

### Post by LinuxFan999 on 2011-11-17
> **jimmyjim359 said:**
> okay so i just reinstalled and now its doing the same thing
Downgrade to 11.04 then.

---

