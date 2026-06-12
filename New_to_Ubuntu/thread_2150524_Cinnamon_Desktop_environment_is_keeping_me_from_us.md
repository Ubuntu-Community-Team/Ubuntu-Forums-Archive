---
title: "Cinnamon Desktop environment is keeping me from using my computer."
date: 2013-06-01
forum: New to Ubuntu
---

### Post by JohntheChristian on 2013-06-01
I've been using Cinnamon for the last few days with no error. However, yesterday I closed my laptop to go to work with cinnamon running. While at work i temporarily lost power (I don't know if my battery lasted the whole time or not). I came home to use laptop, and I get an error stating that the Cinnamon session cannot be loaded, and it will fallback to default session. I click OK, and then it informs me that gnome session also cannot be loaded. at this point it seems to reload linux and I come back to the same error. 

I have other Desktop environments installed (LXCE, XCFE) but I cannot get to the point where I can load them, because the computer tries to load into cinnamon which will not load. 

It seems I'm booting into linux but an error with my DE is not letting me use it. ANy idea how I can get out of this loop?

---

### Post by montag dp on 2013-06-01
Can you get to a console login?  You should be able to using CTRL+ALT+F1, and return using CTRL+ALT+F7.  If I were you, I'd go to the console and back up all my data on an external drive before doing anything else.

After that, and this is just me, but I would delete all the hidden folders that I don't need on my /home partition (that is, ones that don't contain program settings I wish to retain, like Thunderbird), and reinstall the OS while not formatting /home.  This allows you to retain all your files on /home when reinstalling, provided you do have a separate /home partition.

Note that you may not need to do a full reinstall.  Someone else may be able to guide you through removing the packages that are broken and then getting back the ones you need, but personally I'd just avoid all that hassle and reinstall.  No matter what you do, be sure to back up first!

---

### Post by vanadium on 2013-06-01
You may have incurred significant file system damage while losing power unexpectedly. One solution to this is to reinstalling without erasing your disk. However, while this will preserve the user data on disk, these data may also have been corrupted by the power failure.

Power outages are potentially dangerous. And this is not a linux-only risk. I have seen two times a totally havocked Windows system (unbootable) as a result of unexpected power outage. It is equally possible that a power outage passes without any damage to your file system. It just depends on the particular timing of the incident.

The best approach is to reinstall totally afresh. If there is important data of which you do not have a backup yet, rescue it first from the drive, e.g.  from a live session or a recovery prompt. Keep that data separate and only continue using it when you have verified it is not corrupt.

---

### Post by presence1960 on 2013-06-01
When you boot choose advanced ubuntu options > recovery mode. When recovery mode loads choose root. This will put you in a root shell. run ```
e2fsck /dev/sdXZ -y -f -v -c
```

where /dev/sdXZ is your ubuntu partition (/). Example: on my machine it would be /dev/sdb6 as that is my ubuntu OS partition. This will check your Ubuntu OS for errors which probably occured when the power was abruptly stopped. When complete run reboot.

---

