---
title: "Emerald makes the interface sluggish"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by shivkrish22 on 2008-07-28
I have installed emerald as the window decorator now. However i see that the window animations and the GUI in general has become sluggish(specifically in firefox when switching between tabs). 
I am running Ubuntu 8.04 on a Vostro 1500 laptop (2 gb RAM, nVidia 8400m GS, driver version 169.12) I have updated to the latest compiz-fusion (0.7.6) 

Can someone help me out?

---

### Post by SunnyRabbiera on 2008-07-28
Eh its probably because you have the newer compiz, its usually best to use the software in the repositories instead of going with versions that are not.
Latest doesnt always mean greatest.

---

### Post by shivkrish22 on 2008-07-28
The thing is that I had the same problem with the version of compiz in the repositories and hoped that the newer version might be better.

---

### Post by SunnyRabbiera on 2008-07-28
Ah, well that will do it.
Its possible that emerald and compiz just dont want to co operate on your system, sometimes applications have minds of their own... I have seen it

---

### Post by droazen on 2008-09-06
This was a known bug in the nvidia driver that has now been fixed. However, the nvidia-glx-new driver in the Hardy repos is a bit out-of-date and doesn't contain the fix. The easiest way to obtain the latest driver is:

```
1. sudo apt-get install envyng-gtk
2. go to system tools, and start "EnvyNG"
3. click "nvidia", then select "Install the Nvidia Driver (Automatic Hardware Detection)"
4. reboot

```

After you reboot, you should no longer see any lag when switching tabs in firefox with emerald running.

Reference:[https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/144216/comments/39]("https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/144216/comments/39")

---

### Post by knix on 2008-09-06
> **droazen said:**
> This was a known bug in the nvidia driver that has now been fixed. However, the nvidia-glx-new driver in the Hardy repos is a bit out-of-date and doesn't contain the fix. The easiest way to obtain the latest driver is:

```
1. sudo apt-get install envyng-gtk
2. go to system tools, and start "EnvyNG"
3. click "nvidia", then select "Install the Nvidia Driver (Automatic Hardware Detection)"
4. reboot

```

After you reboot, you should no longer see any lag when switching tabs in firefox with emerald running.

Reference:[https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/144216/comments/39]("https://bugs.launchpad.net/ubuntu/+source/emerald/+bug/144216/comments/39")

good point, but look at date...

---

### Post by Crafty Kisses on 2008-09-06
Post the results of this command: ```
top
```

---

