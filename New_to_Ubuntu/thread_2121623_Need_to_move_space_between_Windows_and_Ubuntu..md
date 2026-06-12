---
title: "Need to move space between Windows and Ubuntu."
date: 2013-03-02
forum: New to Ubuntu
---

### Post by KafkaAron on 2013-03-02
Hello everyone. I am currently running Ubuntu and Windows 7 alongside each other in a dual boot system. I need to expand the amount of space on Windows, as I did not give enough space the first time through. How do I move hard drive space from Ubuntu to Windows? I am not an expert in hard drive matters, so please explain every step in detail! Here is a screenshot of my gparted. Thanks.
[ATTACH=CONFIG]239643[/ATTACH]

---

### Post by eigilw on 2013-03-02
> **KafkaAron said:**
> Hello everyone. I am currently running Ubuntu and Windows 7 alongside each other in a dual boot system. I need to expand the amount of space on Windows, as I did not give enough space the first time through. How do I move hard drive space from Ubuntu to Windows? I am not an expert in hard drive matters, so please explain every step in detail! Here is a screenshot of my gparted. Thanks.
[ATTACH=CONFIG]239643[/ATTACH]
HI there.
As the very first thing you must back up your data. Change of partitions are not guaranteed to avoid loss of data. That is a must.
Then you start with minimizing your partition with too much space by pointing at it and drag to the new size or enter the number. Ensure the empty space i before the partition.
Then you will have some free space at the end of the short partition which you then can expand.
The window will show the new situation, but nothing physically happens until you press enter.
Good luck

---

### Post by Mr. Shannon on 2013-03-02
To add a couple things.  You need to do the resize from a LiveCD as I am pretty sure Ubuntu will get mad at you if you try to resize the partition it is booted from.  Because Gparted will have to move your Linux partition to give windows more space it will probably take a very long time, so be patient.  Extending the windows partition should not take hardly any time however as no data has to be moved.

---

### Post by zrdc28 on 2013-03-02
if you do this you better be sure you have a backup,** next you must** defragment windows about 2 times, next you need to chkdsk /f windows. If you don't do those
you will most likely have a failed situation. I think there is a gui on windows 7 for the chkdsk be careful .

---

### Post by Mr. Shannon on 2013-03-02
It might actually be safer to use Gparted only to shrink/move the Ubuntu partion and then boot into windows and expand your C drive from there.  Just make sure not to expand the widnows partion over top of your Ubuntu partition.

---

### Post by Mark Phelps on 2013-03-02
I presume you want to "move" space from sda6 to sda3 -- right?

If so, do the following:
1) Boot into Ubuntu LiveCD or LiveUSB and use GParted to shrink sda6.  You have to be booted OUTSIDE of your current Ubuntu installation because you can't change partitions are are in use.
2) Reboot -- but into Win7, and use ONLY the Win7 Disk Management utility to expand the "C" "drive" (actually, a partition, not a drive -- but that is a different subject ...) to take up the space now unallocated.  Win7 will need to reboot to do this, so let it.
3) When done, reboot again into Win7 -- to let it make any needed filesystem adjustments
4) Reboot into Ubuntu

All should be OK now.

Note, if you use Gparted to resize the Win7 partition, it MIGHT work, but it might also corrupt Win7 boot.  So, use ONLY the Win7 Disk Management tool to do this.

---

### Post by KafkaAron on 2013-03-02
Thanks everyone! Very fast responses was expecting days lol.

---

