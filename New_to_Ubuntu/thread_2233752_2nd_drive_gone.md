---
title: "2nd drive gone"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by GettingNowhere on 2014-07-10
I installed Ubuntu 14.04 over Windows XP on a computer with two internal hard drives.  I put the important files onto drive D and installed Ubuntu onto drive C.

I now have no second drive.  It appears Ubuntu has made the other drive a swap drive and presumably wiped it clean.
Am I correct, because, if I am, I will be looking for another job tomorrow.

```
andy@andy-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00038fe4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484202495   242100224   83  Linux
/dev/sda2       484204542   488396799     2096129    5  Extended
/dev/sda5       484204544   488396799     2096128   82  Linux swap / Solaris


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=dd7df36e-7f59-4c0c-ba0b-55e77b3a145f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27fd68c9-80d8-411a-8afa-9b06f9b79e89 none            swap    sw              0       0
andy@andy-desktop:~$ blkid
andy@andy-desktop:~$ sudo blkid
/dev/sda1: UUID="dd7df36e-7f59-4c0c-ba0b-55e77b3a145f" TYPE="ext4" 
/dev/sda5: UUID="27fd68c9-80d8-411a-8afa-9b06f9b79e89" TYPE="swap" 
```
andy@andy-desktop:~$ 

I really need those important files back.

---

### Post by sandyd on 2014-07-10
> **GettingNowhere said:**
> I installed Ubuntu 14.04 over Windows XP on a computer with two internal hard drives.  I put the important files onto drive D and installed Ubuntu onto drive C.

I now have no second drive.  It appears Ubuntu has made the other drive a swap drive and presumably wiped it clean.
Am I correct, because, if I am, I will be looking for another job tomorrow.

andy@andy-desktop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00038fe4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484202495   242100224   83  Linux
/dev/sda2       484204542   488396799     2096129    5  Extended
/dev/sda5       484204544   488396799     2096128   82  Linux swap / Solaris


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=dd7df36e-7f59-4c0c-ba0b-55e77b3a145f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=27fd68c9-80d8-411a-8afa-9b06f9b79e89 none            swap    sw              0       0
andy@andy-desktop:~$ blkid
andy@andy-desktop:~$ sudo blkid
/dev/sda1: UUID="dd7df36e-7f59-4c0c-ba0b-55e77b3a145f" TYPE="ext4" 
/dev/sda5: UUID="27fd68c9-80d8-411a-8afa-9b06f9b79e89" TYPE="swap" 
andy@andy-desktop:~$ 

I really need those important files back.

The output above shows that you only have one drive installed on the computer. Are there actually two physical drives on the computer, or are C/D simply partitions on the same drive?

---

### Post by Bucky Ball on 2014-07-10
Doubt that it's wiped clean. It's not even showing so we wouldn't know! ;)

Don't panic yet. Did you fiddle in the box at all? This might seem like a stupid question, but would definitely not be the first time it's happened; the second drive is still plugged in firmly at the motherboard and drive?

If it was there, it should be showing as drive sdb, wiped or not. I know you said this in your first post:

> I installed Ubuntu 14.04 over Windows XP on a computer with two internal hard drives. 

Reiterating what sandyd asked and just to confirm; there are two physical drives and not two partitions on the one drive?

* I think I might have answered that question. If you are thinking Ubuntu has turned wiped the 'drive' because of this line in the output:

```
/dev/sda5 484204544 488396799 2096128 82 Linux swap / Solaris
```

... then you are talking partitions, not drives. That is sda5, which means it is a *partition* on the sda *drive*, as are sda1 and sda2 (sda5 is actually a logical partition inside the extended partition sda2). If you had a second drive it would be identified as sdb and the partitions as sdb1 and so on. ;)

If that is the only drive in the box, yes, looks like it's wiped. I would stop using it immediately and start researching how to recover the data if that is the case (continuing to use it will lessen or kill your chances of retrieving the data). Post a new thread about it if that is the case or change the name of the thread to reflect the current situation.

---

### Post by sudodus on 2014-07-10
I'm very sorry, but I'm afraid there is a misunderstanding of the term 'drive'. Windows uses it where linux uses the term partition. Linux uses drive for a whole physical device, for example a hard disk drive or a USB pendrive.

C: and D: in Windows are two linux partitions. They can be situated on the same hard disk drive, or C: can be on /dev/sda and D: can be on /dev/sdb (one on each drive).

In your case Ubuntu is installed in the first drive /dev/sda in the two partitions /dev/sda1 (the root partition) and /dev/sda5 (the swap partitions). /dev/sda2 is an extended partition (a container). Ubuntu finds no second drive.

So I think you have only one hard disk drive. There were two partitions on it, C: and D:, and now you have overwritten it with Ubuntu, when you were thinking that there were two drives, and you only were overwriting one of them.

-o-

If you have a backup of the previous content with Windows and all the files, there is some hard work, but it is straight-forward to restore the system. Otherwise you have to resort to some recovery tools.

If the content is very important to save, make a cloned copy of the drive, and work with the recovery tools on the cloned copy. Use ***ddrescue*** for the cloning.

Try ***Testdisk*** to recover the file system of Windows, and if no go, try ***PhotoRec*** to recover the file content of the important files without a file system.

See this link

[http://www.cgsecurity.org](http://www.cgsecurity.org)

---

### Post by yancek on 2014-07-10
There are countless tutorials on installing Ubuntu and other Linux distributions freely available online.  It doesn't appear you spent much if any time reading them before doing the install.  I'd have to agree with the posts above, you had one drive with two partitions and because you were unfamiliar with the naming conventions I guess the only left to say is Good Luck on your job hunt.

---

### Post by GettingNowhere on 2014-07-10
You're right.  There's only one physical hard drive.
So it was partitioned.
Does that mean I've lost the lot?

---

### Post by Bucky Ball on 2014-07-10
Please re-read the bottom of post #3. You need to stop using that drive immediately if you want to retrieve data from it.

---

### Post by sudodus on 2014-07-10
> **Bucky Ball said:**
> Please re-read the bottom of post #3. You need to stop using that drive immediately if you want to retrieve data from it.

+1

And start learning ***ddrescue, testdisk ***and*** photorec***. If the files are very important, work on a cloned copy of the overwritten drive.

---

### Post by sandyd on 2014-07-10
I would probably suggest booting from a livecd after youve shut down, and see if you can use testdisk/photorec to recover your files.
There are a few guides around including [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) to help you get started

---

### Post by GettingNowhere on 2014-07-10
Well, thanks everyone. Yes Bucky, I did as you said.
Took the disk out and stuck it on another Linux beast that I loaded with PhotoRec (I found out that PhotoRec and Testdisk now come in the same bundle).
It was Photorec that saved the files and I'm still employed (at least for another day).
All because I was told there were two drives, and I didn't check to see.
Oh well!
Much appreciated.

---

### Post by sudodus on 2014-07-11
I'm glad, you were able to save the important files :-)

---

