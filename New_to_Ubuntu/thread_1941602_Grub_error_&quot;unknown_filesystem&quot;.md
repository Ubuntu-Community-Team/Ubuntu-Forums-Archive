---
title: "Grub error: &quot;unknown filesystem&quot;"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by ljl16 on 2012-03-16
Hey guys,
 I messed up. I was tweaking my partitions and resizing them and once I restarted I must have messed up with my grub, since it displays the infamous "error: unknown filesystem; grub rescue>".
 Since I read in other posts that each case is rather unique, [here]("http://pastebin.com/Us3iiw3M") is the results of running the boot_info_script.sh.

 Any ideas? Basically my system is as follows: 
[IMG]http://i.imgur.com/7jF8y.png[/IMG]

Two HDDs, one for windows (sda1) and another for several uses (sda2): a ntfs data partition (sda5), linux partition in ext4 (sda6), linux swap (sda7) and some allocated data.
I tried resizing the sda6 for linux in gparted via ubuntu livecd, but it won't allow me to.

Any input on how can I fix all this?

Cheers,

---

### Post by varunendra on 2012-03-16
Hi,

It seems you are right AND you are wrong. Right in that you've really messed up! Wrong in that you've messed up only grub..

Actually you seem to have messed up the whole ubuntu installation itself. Sorry for the bad news, but a default Ubuntu installation (even the lightest variations like "Lubuntu") can't fit in a 1GB partition which you currently have as sda6. The result of Boot Info script confirms the same- the partition has only /etc/fstab file in the partition, and no other files required to boot - meaning either you didn't manage to install ubuntu correctly, or you have lost everything important on that partition somehow.

As such, neither you can recover the installation, nor can you do a fresh one in that size. You need at least 5GB to do a default Ubuntu installation. Recommended size is 20-26 GB.

You also seem to have a slight misunderstanding about your hard-disk/partition layout:
> **ljl16 said:**
> Two HDDs, one for windows (sda1) and another for several uses (sda2): a ntfs data partition (sda5), linux partition in ext4 (sda6), linux swap (sda7) and some allocated data.
I tried resizing the sda6 for linux in gparted via ubuntu livecd, but it won't allow me to.

Maybe you have understood correctly, just explained it incorrectly. sda**1**, sda**2**,.... etc. stand for 'partitions', not hard disks (those are sd**a**, sd**b**, etc.)
As per the screenshot, the boot info result and your description, the 'other' (500GB) hard disk seems to be untouched. Both your windows and (attempted) Linux installations reside on sda.

That was the information part, which suggests that you can't recover the ubuntu installation, nor can do a fresh one on that size (I wish I'm wrong, but am afraid I'm not). What you can do is:

[LIST]
[*]Either install Ubuntu on the 500GB hard drive on appropriately sized partitions, or
[*]resize sda5 (a bit risky for data) to gain space for sda6 > expand sda6 to more than 6GB > do a fresh installation.
[/LIST]
It is always a good idea to back up data before playing with partition manipulation tools like gparted, and do the partitioning, resizing before proceeding with the installation.


If you need assistance with partitioning/installation, please tell us what you want to do now.

---

### Post by tbhatia4 on 2012-03-16
> **ljl16 said:**
> Hey guys,
 I messed up. I was tweaking my partitions and resizing them and once I restarted I must have messed up with my grub, since it displays the infamous "error: unknown filesystem; grub rescue>".
 Since I read in other posts that each case is rather unique, [here]("http://pastebin.com/Us3iiw3M") is the results of running the boot_info_script.sh.

 Any ideas? Basically my system is as follows: 
[IMG]http://i.imgur.com/7jF8y.png[/IMG]

Two HDDs, one for windows (sda1) and another for several uses (sda2): a ntfs data partition (sda5), linux partition in ext4 (sda6), linux swap (sda7) and some allocated data.
I tried resizing the sda6 for linux in gparted via ubuntu livecd, but it won't allow me to.

Any input on how can I fix all this?

Cheers,

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
install this using a live session
run boot repair
if you are using a dual boot then select advanced feature and check windows nt at bottom 
then reboot

---

### Post by ljl16 on 2012-03-16
Hey guys,
 Thanks for all the answers and support. What I finally did was boot up an ubuntu livecd and install it fresh new (it detected the windows partition as well). Automatically, the install suggested me to partition part of the data partition for ubuntu (about 17GBs).
 I installed it and when booting, my Windows was accessible again :).

Thanks!!!

---

### Post by varunendra on 2012-03-16
Great!
Please mark it as [Solved] now that it is.

---

### Post by tbhatia4 on 2012-03-17
> **ljl16 said:**
> Hey guys,
 Thanks for all the answers and support. What I finally did was boot up an ubuntu livecd and install it fresh new (it detected the windows partition as well). Automatically, the install suggested me to partition part of the data partition for ubuntu (about 17GBs).
 I installed it and when booting, my Windows was accessible again :).

Thanks!!!

great mark the thread solved

---

