---
title: "Deleted all partitions during install"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by neelix32 on 2013-01-14
I posted a question on askubuntu.com but I didn't get any answers on this, so I was hoping that I would have more luck here. Today I installed Ubuntu 12.10 on my laptop. While installing it I chose the option "Install Ubuntu over Windows" assuming that the installer would keep the partitions and really install Ubuntu over Windows (how stupid of me). So now I'm asking is there a way to recover the partition and files I lost during the installation? I tried testdisk, but I didn't know how to use it. Any help is appreciated. Thanks!

---

### Post by ajgreeny on 2013-01-14
From a live CD or USB please run the terminal command ```
sudo fdisk -l
```(that's a lower case L at the end) and tell us the output.  Depending on what happened in the installation you could possibly have separate data partitions still in existence.

---

### Post by neelix32 on 2013-01-14
I don't have internet on that computer now so here is a shortened version: 
```


Disk /dev/sda: 500.1GB, 500107862016

...

Device      Boot    Start             End             Blocks           Id     System
/dev/sda1    *      2048          49971           248832          83     Linux
/dev/sda2            501758      976771071    488134657      5      Extended
/dev/sda5            501758      976771071    488134657     8e     Linux LVM

...

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

...

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table




```

---

### Post by ajgreeny on 2013-01-14
OK, it looks as if you have indeed overwritten all your previous partitions and are now left with just three Ubuntu partitions.

Unfortunately, as far as I'm concerned, one of them is a LVM partition, and I do not have any experience or ability to assist you further with that, nor can I help with the two final comments about Disk /dev/mapper not containing a valid partition table.

Testdisk may still be an option, but I suggest you do not boot the computer from the internal disk to do anything as that will increase the risk of corruption of any files that have not already been damaged by activities so far.  Try testdisk again, after reading up how to use it, from a live CD and you will not reduce you chances any further.

---

### Post by oldfred on 2013-01-14
Stop using system, every thing you do is potentially overwriting your old data.

You also checked off to encrypt your system so it is LVM, I also do not know lvm and if test disk cannot see the LVM partitions, your backups are all you have.

If you had not encrypted it, you could recover some data with photorec. Not sure if photorec might still find old data but anything written encrypted will not be visible. Photorec is part of testdisk.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by Ghalebi on 2013-01-14
Same thing happened to me [http://ubuntuforums.org/showthread.php?t=2103633](http://ubuntuforums.org/showthread.php?t=2103633)

I believe there should be some consolidated "Read Before You Install Over Windows" post some where in this forum! This doesn't mean by anyway that it's not my fault, yes .. I should have asked before I install with that option!

---

### Post by oldfred on 2013-01-14
Third screen shot shows "Erase Disk". 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I think part of the issue is that Windows has from the beginning of time confused drives & partitions. A Windows user may think disk just means the Windows partition when it really means the entire hard drive.

Windows has always called both disk & partitions drives, c: drive , d: drive. But that does not tell you if d: drive is really a second partition on the first physical disk or the second disk.

---

