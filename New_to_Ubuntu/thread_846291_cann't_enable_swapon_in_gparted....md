---
title: "cann't enable swapon in gparted..."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by jammu_d_gr8 on 2008-07-01
friends am a newbee to Ubuntu....
as am new to this am so curious abt every thing in ubuntu.
Now what happened is, i made an ex3 partition of 7 gb and swap of 16gb(!!!) during initial instalation. and while surfing I found that swap shouldn't b more than 2gb(usually double the size of RAM, am using 1 gb ram). I decided to use gparted to do this. And i deleted this swap after doing "swapoff". Then created 2 gb swap and 14 gb ex3 partitions. THe problem is now i cann't enable swap or i cant do swapon using Gparted...
help me guys.....

---

### Post by plucky on 2008-07-01
> **jammu_d_gr8 said:**
> friends am a newbee to Ubuntu....
as am new to this am so curious abt every thing in ubuntu.
Now what happened is, i made an ex3 partition of 7 gb and swap of 16gb(!!!) during initial instalation. and while surfing I found that swap shouldn't b more than 2gb(usually double the size of RAM, am using 1 gb ram). I decided to use gparted to do this. And i deleted this swap after doing "swapoff". Then created 2 gb swap and 14 gb ex3 partitions. THe problem is now i cann't enable swap or i cant do swapon using Gparted...
help me guys.....

The UUID of the swap partition has probably changed.Open a terminal and post output of ```
cat /etc/fstab
sudo blkid
```

Check the UUID's for the swap partition are the same,if not change the UUID in the fstab file to match the one given by the blkid command.



Good Luck

---

### Post by jammu_d_gr8 on 2008-07-01
jamesh@jamesh-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=8a922c70-1f39-47e2-b0ea-573aa6c7a2ff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=8209dc26-d99c-40f2-92fe-8318d8c47adf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


jamesh@jamesh-desktop:~$ sudo blkid
[sudo] password for jamesh: 
/dev/sda1: UUID="32B0A115B0A0E119" TYPE="ntfs" 
/dev/sda5: UUID="B85090ED5090B39A" TYPE="ntfs" 
/dev/sda7: UUID="8a922c70-1f39-47e2-b0ea-573aa6c7a2ff" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="b242d32f-2556-4760-9182-c3d890ecd7ad" 
/dev/sda9: UUID="1d93b094-a571-4da0-bd0d-540fcb271920" SEC_TYPE="ext2" TYPE="ext3" 



 these qre the outputs
now how can i change uuid of "swap"
and change to what??(sda7 or sda9)???
help me friend.......

---

### Post by plucky on 2008-07-02
> UUID=8209dc26-d99c-40f2-92fe-8318d8c47adf none swap sw 0 0
/dev/sda8: TYPE="swap" UUID="b242d32f-2556-4760-9182-c3d890ecd7ad" 


See the difference?

To change the line,open a terminal and ```
sudo cp /etc/fstab /etc/fstab.old
``` This makes a copy of your fstab file just in case of mistakes.Then ```
gksudo gedit /etc/fstab
```

And change the line > UUID=8209dc26-d99c-40f2-92fe-8318d8c47adf none swap sw 0 0 to > UUID=b242d32f-2556-4760-9182-c3d890ecd7ad none swap sw 0 0

Then reboot

Good Luck

---

### Post by jammu_d_gr8 on 2008-07-03
did as u said still the problem persists
am getting "swapon: /dev/sda8: Invalid argument"

aftermaking changes d respective command shows

jamesh@jamesh-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=8a922c70-1f39-47e2-b0ea-573aa6c7a2ff /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=b242d32f-2556-4760-9182-c3d890ecd7ad none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


jamesh@jamesh-desktop:~$ sudo blkid
[sudo] password for jamesh: 
/dev/sda1: UUID="32B0A115B0A0E119" TYPE="ntfs" 
/dev/sda5: UUID="B85090ED5090B39A" TYPE="ntfs" 
/dev/sda7: UUID="8a922c70-1f39-47e2-b0ea-573aa6c7a2ff" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="b242d32f-2556-4760-9182-c3d890ecd7ad" 
/dev/sda9: UUID="61d275e5-84ed-4756-bcdf-136e02e3ce81" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="D2380D6D380D51C1" TYPE="ntfs" 


also i cant paste or save any files to the sda9 partition(me formated it as ex2 and ex3. in both cases it doesnt works).
wat about deletion the swap and sda9 and again creating them with gparted??(in that case give me a detailed tutor to use the feature currectly...)

thanks.......
with hope jamesh

---

### Post by plucky on 2008-07-03
> did as u said still the problem persists
am getting "swapon: /dev/sda8: Invalid argument"


**Try a reboot.**

> also i cant paste or save any files to the sda9 partition(me formated it as ex2 and ex3. in both cases it doesnt works).
wat about deletion the swap and sda9 and again creating them with gparted??(in that case give me a detailed tutor to use the feature currectly...)

Your sda9 partition is not mounted in your **fstab** file,so if you want to write to that partition you need to mount it first.

Take a look at this link for [Mounting a linux Partition](http://www.psychocats.net/ubuntu/mountlinux) and is also a good place to learn about partitioning.


Good Luck

---

### Post by jammu_d_gr8 on 2008-07-05
trhanx for ur replies guys....

---

