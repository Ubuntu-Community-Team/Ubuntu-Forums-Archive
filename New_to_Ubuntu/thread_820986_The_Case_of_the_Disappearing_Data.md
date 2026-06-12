---
title: "The Case of the Disappearing Data"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by smith_fan on 2008-06-06
I am hoping y'all can help me save a lot of important data that kinda got 'wiped' off of my 4GB Kingston Data Traveler flash drive.  When booted-up from a Gparted Live CD (v0.3.4-11), I told it to save a screen shot of my system's single internal 80GB hard drive's details to ask about at Acronis Forums.  I'm trying to triple-boot XP Pro, the pre-loaded Vista Home Basic (which totally SUCKS!), and Ubuntu on this laptop.  And I'm not sure how to partition.  So I saved a screen shot of the hard drive's configuration onto flash media to ask about it.  I, very stupidly, had it save it to a drive that was about 1/3rd filled with valuable data (mainly receipts of S/W purchases and other official records of various web submissions.)  When I booted back into Vista to compose my post, Windows asked me if I wanted it to prepare the new media I had inserted.:shock:  Ubuntu doesn't list the thing in Nautilus and Windows just wants to format it.  Gparted launched from within Ubuntu shows it as an unmounted 3.84 GB with an unknown file system as /dev/sdc with “---” under both the 'Used' and 'Unused' columns.  When I get information on that item,  the message box has stated, at the bottom:  “!  Warning:  Unable to detect filesystem.  Possible reasons are:
-The  filesystem is damaged
-The  filesystem is unknown to Gparted
-There is no  filesystem available (unformatted)
“
Am I screwed here or is there a way to salvage the data?  And can someone please explain to me what the heck happened?  I don't want to do something like that again—that sure doesn't encourage me to dabble in linux!  And yet, I'm sure it's probably far superior to Microsoft's products.

Thanks a lot!,
~D~

---

### Post by Sef on 2008-06-06
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") to recover your data.

With Ubuntu Live CD:  Applications > Accessories > Terminal

type or paste in this code:

```
sudo fdisk -l
``` small L, then paste the results here.

---

### Post by cariboo on 2008-06-06
There are lots of for pay utilities in windows that will recover your missing data but if you want a free utility I would suggest **Testdisk** you can get a Ubuntu Rescue Remix  ISO with instructions here:

[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

Jim

---

### Post by smith_fan on 2008-06-06
Having done nothing yet regarding the TestDisk app you both suggested, here are the result you asked for, Sef:

darin@Belinda:~$ sudo fdisk -l
[sudo] password for darin:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x505471ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2151        8412    50299514    7  HPFS/NTFS
/dev/sda3            8413        9729    10578800+   7  HPFS/NTFS
/dev/sda4             193        2150    15727635    5  Extended
/dev/sda5             193        2076    15133198+  83  Linux
/dev/sda6            2077        2150      594373+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584    7  HPFS/NTFS
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 50)

Disk /dev/sdc: 4127 MB, 4127195136 bytes
16 heads, 32 sectors/track, 15744 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x3836671f

Does that tell ya what you were wanting, bud?

I appreciate your suggestions of recovery programs!:)

Anybody have good advice for multi-booting--I'm kinda bewildered?
~D~

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       15744     4030448    7  HPFS/NTFS
darin@Belinda:~$

---

### Post by cariboo on 2008-06-07
For your first time just use the defaults and everything will be set up automatically. Once every thing is isntalled you will see a boot menu where you have a choice of Ubuntu, memtest or Windows. If you don't see the menu just hit the escape key and there it is.

Jim

---

