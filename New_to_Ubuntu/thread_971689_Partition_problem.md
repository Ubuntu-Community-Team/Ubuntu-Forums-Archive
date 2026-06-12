---
title: "Partition problem"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by EdwinHunt on 2008-11-05
Hi,

I downloaded Ubuntu 8.04 and tried to install in in Windows XP. All went well until it refused to partition properly.
When I next tried to start the computer I could get up neither XP nor Ubuntu. As afr as I could gather, the partitioning is messed up.
What can I do?  I know nothing about such things.

Thanks,
Edwin Hunt.

---

### Post by Cypher on 2008-11-05
Were you trying to install XP inside WUBI on XP, or running the Ubuntu Live CD and then ran the installer from there?

If you already had Win XP installed, was it taking up ALL the space on the HD? If so, you should've first re-sized the XP partition to create some free space and then created the partition for Ubuntu.

It is very easy for the partitioning to go badly and mess up your existing XP installation, as you've discovered. A quick query here with your current partition scheme would've yielded the right steps.

In your machine's current state, if you have the Ubuntu 8.04 Live CD, boot into it and when you're at the desktop, go to Applications->Accessories->Terminal and type the command
```

sudo fdisk -l

```
This will show all the partitions on all of your HD's right now, tell us what that looks like and with your knowledge of how XP looked before all of this, we can attempt to figure out what has happened..

---

### Post by mapes12 on 2008-11-05
Or if you want to use an easy GUI based partition application burn a GParted Live CD and boot your machine from the CD. Get it from here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It also enables a screen shot to be taken which you can attach to a post here for further help and guidance.

---

