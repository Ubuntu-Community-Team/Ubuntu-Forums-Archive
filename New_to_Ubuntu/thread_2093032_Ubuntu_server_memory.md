---
title: "Ubuntu server memory"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by Jackjack770 on 2012-12-09
I've installed ubuntu set onto an old computer and the memory isn't very much so I want add a external hard via USB to the computer. Can you tell the computer to direct info from other computer to the hard drive or can I extend  the memory on the hard drive to the computer's hard drive

---

### Post by Bashing-om on 2012-12-09
Jackjack770; Hi ! And Welcome again to the forum.

I am concerned that you are suffering a misconception. The amount of ram installed on the mother board has very little at all to do with hard drives. Albeit, it is always a good thing to install all the ram you possibly can, I have NEVER encountered a situation of having to much ram ( I think ubuntu currently can address 64 megs of ram).

adding a hard drive to the system:[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
auto mount via /etc/fstab:[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I recommend that you study these links; any additional questions, by all means post back !

[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by tgalati4 on 2012-12-09
You can create a swap partition on the hard drive using:

```
gksudo gparted
```

Then when booted you can add that swap to the system:

```
sudo swapon /dev/sda2
```

Of course, change the partition identifier if not sda2.

---

