---
title: "where did the gear gone?"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by macakcira on 2013-11-03
Hi, I'm a pro Ubuntu user. I had a gear on the top right corner and now it's missing and I don't know how to turn off computer properly without it...

---

### Post by mobile3 on 2013-11-03
ctrl +alt +del keys, i have the same sometimes on 1310

---

### Post by darksdarkson on 2013-11-03
Hi, there. I believe this is a problem with Unity. Go look at [this thread]("http://ubuntuforums.org/showthread.php?t=1907593") for how to fix it. I hope that helps.

---

### Post by macakcira on 2013-11-03
> **mobile3 said:**
> ctrl +alt +del keys, i have the same sometimes on 1310

Thanks, after I logged off with ctrl-alt-del it came back! Don't know why it disappeared..

---

### Post by grahammechanical on 2013-11-03
It is not easy to get to System Settings without the power/cog icon but right clicking on the desktop and selecting Change Desktop Background will get us to system Settings. By the way I had this issue with 13.10 a few times during the last days of its development cycle and I was not using a Nivida driver. 

I found that a reboot usually fixed it. There are commands that will let us shutdown or restart. Open a terminal with Ctrl+Alt+T or a Linux command line prompt with Ctrl+Alt+f2 and type

```
sudo shutdown -r now
```
```
sudo shutdown -h now
```

-r = restart
-h = halt.

Regards.

---

