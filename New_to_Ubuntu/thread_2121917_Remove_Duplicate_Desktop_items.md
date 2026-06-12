---
title: "Remove Duplicate Desktop items"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by Apurvam on 2013-03-03
Hello!

Few moments ago I installed Xubuntu 12.10 on my laptop. I'm beginner in Linux. 

I'm having 2 sets of icons named *'108 GB Volume'*  &  *'305 GB Volume*' on my desktop.

I tried to disable them by Desktop Settings --> Icons: uncheck "Removable Devices", but this only removes 2 icons.

I want clean desktop with only Home and Trash icons.

---

### Post by prodigy_ on 2013-03-03
Settings > Desktop > Icons:
[http://ubuntuforums.org/showthread.php?t=1782823&p=10942387&viewfull=1#post10942387](http://ubuntuforums.org/showthread.php?t=1782823&p=10942387&viewfull=1#post10942387)

---

### Post by Apurvam on 2013-03-03
This is what I tried in #1 post - removes 2 icons from 4.

If I'm not mistaken [this guy]("http://ubuntuforums.org/showthread.php?t=2104289&p=12452150#post12452150") had the same problem:
> Also, I have a pair of partitions (one FAT32 ~95GB and one ext4 ~48GB)  that are also showing on the desktop, though they don't seem to be  mounted, and I can't seem to get rid of them.

No solution there.

---

### Post by prodigy_ on 2013-03-03
Uncheck **Filesystem**. Does this help?

---

### Post by Apurvam on 2013-03-03
No.

Update1: It seems I found [solution]("http://ubuntuforums.org/showthread.php?t=2082109&p=12366521#post12366521"), but I don't understand what he meant in that post... Can anyone explain?

---

### Post by prodigy_ on 2013-03-03
I think you'll need to edit **/etc/udev/rules.d/10-hide-partitions.rules** file. Here's how: [http://ubuntuforums.org/showthread.php?t=2099951&p=12430740&viewfull=1#post12430740](http://ubuntuforums.org/showthread.php?t=2099951&p=12430740&viewfull=1#post12430740). **KERNEL=="sdxx"** should contain the name of the partition you're hiding. You can find names using **sudo fdisk -l** or **sudo parted -l** commands.

As for duplicates there's a [possible workaround on AskUbuntu](http://askubuntu.com/questions/207296/after-upgrade-to-xubuntu-12-10-i-have-2-mount-points-for-each-partition). Try it.

---

### Post by Apurvam on 2013-03-03
I fixed it by installing following updates:

[LIST]
[*]xfdesktop4-data (4.10.0-1ubuntu1,4.10.0-1ubuntu1.1) 
[*]xfdesktop4 (4.10.0-1ubuntu1,4.10.0-1ubuntu1.1) 
[/LIST]
 after that I restarted computer.

How can I close this thread?

---

### Post by Apurvam on 2013-03-04
bump

---

