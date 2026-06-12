---
title: "fdisk -l doesnt give any output"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by shan88 on 2011-12-25
i`m new to ubuntu.i installed ubuntu 11.04 as a dual boot with win7 now its works well.i wanted to get the out put of "fdisk -l" for another work.when i put fdisk -l in terminel it shows nothing.why is that.pls help me:(

---

### Post by The Cog on 2011-12-25
fdisk only works when run as root. To do this, put the word sudo in front of the command (SuperUser DO).
```
sudo fdisk -l
```

But don't use sudo for starting graphical applications as root as this can lead to strange problems. Instead, use **gksu**.

Be extra cautious when running anything with root privileges as a mistake has the power to trash the system.

---

### Post by BC59 on 2011-12-25
You have to run fdisk with root privileges.

```
sudo fdisk -l
```

---

### Post by shan88 on 2011-12-25
Thanx guys you save my life.Thanx again :)

---

