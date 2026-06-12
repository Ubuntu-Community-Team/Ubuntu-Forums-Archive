---
title: "manually mount external drive on ubuntu 13.04 vm"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by linux.girl on 2013-05-14
Hi everyone,

My 2TB My Book western digital external drive died after a tiny bump from my elbow. I bought a new  one, 4 TB. I connected it to my computer (host Ubuntu 13.04 64 bit), and it  seemed ok - until I tried to connect it to my virutal machines, where I  mostly need it - and it simply doesnt work. I have a windows xp machine  and an ubuntu 13.04 64 bit machine and the new 4tb is not recognized in  both. In the ubuntu it simply doesnt show, no messages, anything. I'm starting to get desperate with all my WD drives giving these problems - I thought about trying to mount the drive manually on my ubuntu vm. The old drive that I had used to automount without any problems. And this one mounts ok in the host, so I dont understand why it is not showing in the vm. How do I try to manually mount this drive? Any other suggestions what could be the problem, what else I could try to do? Any log files I can look at to see what the problem could be?

Thanks in advance,

linux.girl

---

### Post by oldfred on 2013-05-14
XP will not work with gpt partitioning. Or you can only make the drive 2TB if you want to use it with XP as MBR partitioning has a max of 2TB.

Download in Ubuntu gdisk and run gdisk on your new drive. Was drive already partitioned and formatted? We have seen a lot of users just copy data without partitioning to new very large drives.

sudo apt-get install gdisk
       sudo gdisk -l /dev/sdb

 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by linux.girl on 2013-05-14
Hi oldfred,

The disk came formatted with NTFS and I used it right away. The ubuntu host sees it fine, but the Ubuntu VM doesn't - do you think it is because of the size? Would the ubuntu vm has the same problem as xp vm, i.e., unable to cope 4 TB?

Should I make two NTFS partitions of 2 TB?

Thanks!

linux.girl

> **oldfred said:**
> XP will not work with gpt partitioning. Or you can only make the drive 2TB if you want to use it with XP as MBR partitioning has a max of 2TB.

Download in Ubuntu gdisk and run gdisk on your new drive. Was drive already partitioned and formatted? We have seen a lot of users just copy data without partitioning to new very large drives.

sudo apt-get install gdisk
       sudo gdisk -l /dev/sdb

 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

 MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

---

### Post by oldfred on 2013-05-14
It would still have to be gpt to have two partitions of 2TB each. The limit is the internal size of MBR tables. MBR was designed over 30 years ago and even 2TB was not even thought of for PCs.
And there is no driver for XP with gpt and since XP will not be supported in less than a year there will not be.
If you really have to have XP and really have to have lots of data then you just should get a 2TB drive.

---

### Post by linux.girl on 2013-05-14
So let's say I want to use it only on the Ubuntu vm and not in the XP - is there a way to do it? 

> **oldfred said:**
> It would still have to be gpt to have two partitions of 2TB each. The limit is the internal size of MBR tables. MBR was designed over 30 years ago and even 2TB was not even thought of for PCs.
And there is no driver for XP with gpt and since XP will not be supported in less than a year there will not be.
If you really have to have XP and really have to have lots of data then you just should get a 2TB drive.

---

### Post by oldfred on 2013-05-14
I do not know anything about VMs.
From Ubuntu does gdisk see drive correctly?

I found this, so gpt support in VM must be new.
[http://www.v-front.de/2013/04/release-vmware-converter-51-finally.html](http://www.v-front.de/2013/04/release-vmware-converter-51-finally.html)

---

### Post by linux.girl on 2013-05-14
Hi oldfred, yes, in the host gdisk sees the drive correctly, the only problem is when trying to see it on my ubuntu vm.

---

### Post by linux.girl on 2013-05-15
Another question: I tried to format the drive, and now it appears under a different name - instead of /media/myhome/MyBook, it appears as /media/myhome/bunch of random numbers.

Is there a way to change the random numbers back to the name MyBook?

Thanks!

---

### Post by linux.girl on 2013-05-15
Found the answer: ntfslabel /dev/sdc1 MyBook

thanks :-)

---

### Post by linux.girl on 2013-05-15
@oldfred,

Finally solved the problem: workstation 8 does not support usb 3.0 connections (it does some, but not all) - so the solution was to connect the western digital drive to a usb 2.0 port.

Thanks a lot for all your help, I learned a lot!

---

