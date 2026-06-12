---
title: "Ubuntu 8.10 discrepancy"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Abhishek_12 on 2008-11-15
Hi Everyone ,

Few days back I posted [THIS]("http://ubuntuforums.org/showthread.php?t=975234") thread . Unfortunately I couldn't find solution to my problem

I have typed sudo fisk -l (ie sudo fdisk - L) . Strangely enough terminal was not sowing any partition .

I tried using Partition editor in System-->Administration-->Partition editor  , It also didn't detect any device.

[B]
Last night in my desperate attempt to install Ubuntu . I tried installing uBuntu 7.04 and it worked  .Gpart was showing all partitions . P.E had all choices

Now my query is that how should i install ubuntu 8.10 . Either I should first install ubuntu 8.04 and then upgrade  over it 

[CENTER] or[/CENTER]
 should i give Ununtu 8.10 cd one more try . (I have already downloaded the Image twice  and check disk returns no error of any sort]
[/B]

One more thing will android Sdk work fine with ubuntu 7.04

Thanks for ur time :).

---

### Post by shifty_powers on 2008-11-15
you could just try

```
sudo apt-get dist-upgrade
```

until you get to 8.10....

---

### Post by Abhishek_12 on 2008-11-15
Correct me if I'm wrong .Isn't support for 7.04 has finished ? . Is it possible to upgrade a distro to latest version when support for old distro is no longer provided .

---

### Post by overdrank on 2008-11-15
> **Abhishek_12 said:**
> Hi Everyone ,

Few days back I posted [THIS]("http://ubuntuforums.org/showthread.php?t=975234") thread . Unfortunately I couldn't find solution to my problem

I have typed sudo fisk -l (ie sudo fdisk - L) . Strangely enough terminal was not sowing any partition .

I tried using Partition editor in System-->Administration-->Partition editor  , It also didn't detect any device.

[B]
Last night in my desperate attempt to install Ubuntu . I tried installing uBuntu 7.04 and it worked  .Gpart was showing all partitions . P.E had all choices

Now my query is that how should i install ubuntu 8.10 . Either I should first install ubuntu 8.04 and then upgrade  over it 

[CENTER] or[/CENTER]
 should i give Ununtu 8.10 cd one more try . (I have already downloaded the Image twice  and check disk returns no error of any sort]
[/B]

One more thing will android Sdk work fine with ubuntu 7.04

Thanks for ur time :).
Hi and it may be possible to upgrade by using the alternate cd. Any reason why you are not wanting to us Hardy 8.04? As it is long term support LTS

> **Abhishek_12 said:**
> Correct me if I'm wrong .Isn't support for 7.04 has finished ? . Is it possible to upgrade a distro to latest version when support for old distro is no longer provided .

Hi and it is possible but not recommended. :)

---

### Post by Abhishek_12 on 2008-11-15
I'm currently working on an android application . 8.10 suits my need perfectly because of its new connectivity features .

Thanks for your time . I'll see to how should i proceed furthur.

---

### Post by ugm6hr on 2008-11-15
See this: [http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode](http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode)

This is a bit of a poor show for a LiveCD.

I think you should be able to install if you select Install from the boot menu (rather than Try without installing).

Otherwise, delete the Partition Magic partitions, and try using the "Guided - Use largest free space" option.

---

