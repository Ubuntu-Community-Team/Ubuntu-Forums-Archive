---
title: "UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY"
date: 2019-08-06
forum: New to Ubuntu
---

### Post by igcd on 2019-08-06
Hello there.

I installed Lubuntu 16.04.6. I turned it off and rebooted it and got this message on start up. I have attached a picture of it.

What does this mean?

Why did it happen?

How can I fix it?

Any help will be greatly appreciated.

Cheers

---

### Post by Bashing-om on 2019-08-06
igcd; Well -

> 
I turned it off and rebooted


What means "I turned it off " ? If this is hitting the power button - the system is then still active- , and as such there can be a corrupted file system.

From the installer - a Live desktop ? 
if Live, boot the liveUSB in "try ubuntu" mode and at the desktop activate a terminal with key combo ctl+alt+t.
run then a file system check/repair ( the manual directive):
```

sudo parted -l

```
to verify that the target here is still and in fact mmcblk1p2

The actual check/repair:
```

sudo fsck /dev/mmcblk1p2

```

If it gives errors then we delve in deeper.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by guiverc on 2019-08-06
Firstly Lubuntu 16.04.6 is a flavor of Ubuntu and is now EOL; yes the base of Lubuntu is the same as Ubuntu 16.04 and thus is still supported, however the gui/desktop and applications of LXDE are EOL so won't receive any updates so you should at least consider release-upgrading to 18.04 for security reasons (this is not unique to Lubuntu applying to all flavors outside Kylin - see [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/))

When you "*turned it off*" was it using shutdown or gui tools - or just turned off via power point/switch?  A file system integrity issue usually occurs because of hardware failure or power being turned off thus no clean shutdown of your system. Many such events cannot be found as maybe just a power surge caused a circuit to spike writing a wrong value - `fsck` or file system checks will usually fix this (but it's a reminder that backups are worthwhile).

I would suggest booting a 'live' media (such as Lubuntu install media; it can be any recent version and any flavor ie. need not be Lubuntu, Xubuntu or Ubuntu would work equally well) and `fsck` your disk partitions. This can be done using command line, or gui (eg. `gparted` `kde partition manager` or like tools).  Once done you'll most likely find your system returns to booting normally, but but please consider release-upgrading :)

PS:  Use `ubuntu-support-status` (from command-line/bash) to see your package support status, it'll show the % of your installated packages that are no longer supported

---

### Post by igcd on 2019-08-06
Thank you for the help guys.

I did what Bashing-om suggested and it works now.

The server was turned off by pushing the Power Button, which is probably what caused it.

---

### Post by TheFu on 2019-08-06
> **igcd said:**
> The server was turned off by pushing the Power Button, which is probably what caused it.

Yeah - don't do that, ever.  Unix systems don't like it.

---

### Post by Bashing-om on 2019-08-06
igcd; Great :)

Glad was an easy fix - *could* have been much worse.

As this matter is now concluded:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by Skaperen on 2019-08-06
if you are new to Ubuntu and don't want to "dive into the deep end" i would recommend to just do the install all over again.  and this time, don't just turn it off.  instead, tell it to shutdown.  the filesystem will be totally complete, this way.  if you are given an option to reboot (i already forget what the install steps do) i suggest to take it.  in the future, Linux (the kernel part that runs the file systems) will be more resilient against just turning the computer off.  there will still be error messages when doing that, but it can take care of it automatically.  but, a fresh system install is more critical, so, it's best the the first 2 shutdowns are nice and clean.  do the same after every upgrade, too.

and now is your great opportunity to switch up to 18.04, the latest LTS.

are you installing from a CD-R or a USB memory stick?

---

