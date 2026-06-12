---
title: "Salvage data from HDD (ST4000DM000) pulled from dead NAS (Seagate Central)"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by samosater on 2014-01-14
Dear gnu/linuxers;

I had a Seagate Central NAS (STCG4000100) which failed after six months of use, before I could even attempt to backup its data to another device. Since the data (1.8TB or so) is far more valuable to me than the NAS unit itself, I decided to pull the HDD (ST4000DM000) out, forfeit the warranty entirely and plug it on a modest desktop. These are the basic specs:

[I]        CPU
            Intel Pentium D 820 
            SmithField 90nm Technology 
        RAM 
            4,00GB Dual-Channel DDR2 @ 332MHz (5-5-5-15) 
        Motherboard 
            Intel Corporation D945GCNL (LGA 775) 
        Graphics 
            T27B350 (1920x1080@60Hz) 
            1024MB NVIDIA GeForce 9500 GT (ASUStek Computer Inc)
        Storage 
[B]            149GB Samsung HD161HJ ATA Device (SATA)
            1863GB Seagate ST32000542AS ATA Device (SATA)
            3800GB Seagate ST4000DM000 ATA Device (SATA)[/B]
        Optical Drives 
            HL-DT-ST DVD-RAM GSA-H22N ATA Device 
        Audio 
             High Definition Audio Dev.[/I]

**HD161HJ** is partitioned as two volumes, one running Windows 7 Home Premum x64 SP1, the other running Ubuntu 13.10. **ST32000542AS** is an NTFS slave prepared to receive any data I can salvage from the ext4/lvm2 formatted **ST4000DM000** I pulled from the dead NAS, which requires that both are mounted with read and write permissions on Ubuntu. Although I am completely new to gnu/linux, I tried a few different ways of mounting it, none of which worked so far. I also fiddled with gparted and testdisk, though nasty freezes have made me give up the hasty DIY and ask for the help of more experienced users. Here are some screens of what I've got:

[Status of **HD161HJ**]("http://cubeupload.com/im/Samosater/SDAHD161HJ.jpg")

[Status of **ST32000542AS**]("http://cubeupload.com/im/Samosater/SDBST32000542AS.jpg")

[Status of **ST4000DM000**]("http://cubeupload.com/im/Samosater/SDCST4000DM000.jpg")

[Error message trying to mount ext4/lvm2 via GUI]("http://cubeupload.com/im/Samosater/Errormountingvg1lv1.jpg")

[Error message trying to mount ext4/lvm2 via terminal]("http://cubeupload.com/im/Samosater/errormessageontermin.jpg")

Thank you all for your time and attention.

---

### Post by ian-weisser on 2014-01-14
/dev/mapper isn't a real location.
Your disk seems to be LVM, not a normal partition.
I don't know the solution, since I don't use LVM...but that's why your mount command didn't work.

---

### Post by squakie on 2014-01-15
What happens when you just type:

mount -a


What is the output of:

ls /media/<youruseridhere>

What is the output of:

sudo blkid

What is the output of:

df -h

---

### Post by samosater on 2014-01-15
"mount -a" and "ls /media/samosater" show nothing; "sudo blkid" and "df -h" return some information:

samosater@samosater-desktop:~$ mount -a
mount: only root can do that
samosater@samosater-desktop:~$ sudo su
[sudo] password for samosater: 
root@samosater-desktop:/home/samosater# mount -a
root@samosater-desktop:/home/samosater# ls /media/samosater
root@samosater-desktop:/home/samosater# blkid
/dev/sda1: LABEL="Reservado pelo Sistema" UUID="4EA8CE17A8CDFE09" TYPE="ntfs" 
/dev/sda2: UUID="F606D02B06CFEAA7" TYPE="ntfs" 
/dev/sda5: UUID="d1bc6539-890d-44a2-b519-65f9ef984f1a" TYPE="ext4" 
/dev/sda6: UUID="8048ab59-148d-4c5e-b9e0-0c522e57654a" TYPE="swap" 
/dev/sdc1: UUID="2f773555-a4fe-47b0-89ce-520c109356a4" TYPE="ext2" 
/dev/sdc2: UUID="2f6618a1-5f4a-4fba-b722-255c86948a4a" TYPE="ext2" 
/dev/sdc3: UUID="fdc5efa3-421d-46ca-a610-a0cfbef2ef36" TYPE="ext4" 
/dev/sdc4: UUID="f8918749-2336-432f-ad8b-8982835f3fb5" TYPE="ext4" 
/dev/sdc5: LABEL="Config" UUID="8cec364b-7cd1-4304-ad40-dad6cca4599a" TYPE="ext4" 
/dev/sdc6: LABEL="Swap" UUID="39feb9d2-1ca5-4f6e-9d41-860acb042f8a" TYPE="swap" 
/dev/sdc7: LABEL="Update" UUID="5c6a0262-82d7-4164-a690-5d73b838ca4b" TYPE="ext4" 
/dev/sdc8: UUID="SeXtsc-euZZ-880v-WApk-OQdg-plUK-SohmMH" TYPE="LVM2_member" 
/dev/sdb5: LABEL="Rotativo" UUID="0EF42F25F42F0E91" TYPE="ntfs" 
/dev/mapper/vg1-lv1: LABEL="Data" UUID="d43d8959-8970-4097-bb25-7afe90ceb805" TYPE="ext4" 
root@samosater-desktop:/home/samosater# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        67G  3,6G   60G   6% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            1,6G  8,0K  1,6G   1% /dev
tmpfs           326M  1,1M  325M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,6G   76K  1,6G   1% /run/shm
none            100M   36K  100M   1% /run/user

---

### Post by Bucky Ball on 2014-01-15
Try:

sudo mount -a

(PS: Generally 'sudo' is used to issue commands as root rather than changing to root permanently with 'sudo su'. You're best to avoid that. ;))

---

### Post by samosater on 2014-01-15
Thanks, Bucky Ball;

"sudo mount-a", "ls/media/samosater" and "sudo ls /media/samosater" still don't show anything:

samosater@samosater-desktop:~$ sudo mount -a
[sudo] password for samosater: 
samosater@samosater-desktop:~$ sudo ls /media/samosater
samosater@samosater-desktop:~$

---

### Post by Bucky Ball on 2014-01-15
'sudo mount -a' won't show anything but should mount anything it can in the way of partitions.

---

### Post by samosater on 2014-01-15
It didn't. When I clicked my /Data folder it returned with an error message:

Error mounting /dev/dm-0 at /media/samosater/Data: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-0" "/media/samosater/Data"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

"dmesg | tail" gives me this:

samosater@samosater-desktop:~$ dmesg | tail
[ 3665.884042] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3665.884053] ata4.00: failed command: READ DMA
[ 3665.884062] ata4.00: cmd c8/00:02:82:49:a1/00:00:00:00:00/e0 tag 0 dma 1024 in
[ 3665.884062]          res 40/00:ff:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
[ 3665.884066] ata4.00: status: { DRDY }
[ 3667.788023] ata4: soft resetting link
[ 3667.984362] ata4.00: configured for UDMA/100
[ 3667.984372] ata4.00: device reported invalid CHS sector 0
[ 3667.984385] ata4: EH complete
[ 3668.004976] EXT4-fs (dm-0): bad block size 65536
samosater@samosater-desktop:~$

---

### Post by steeldriver on 2014-01-15
Provided the volume group is active (which your GUI output says it is) and the ext4 filesystem is not corrupt, I think you *should* be able to mount it via the /dev/mapper/ link - it looks to me like you just mistyped it** (b**g1-lv1 instead of instead of **v**g1-lv1

```
sudo mount -t ext4 -o ro /dev/mapper/vg1-lv1 /mnt
```

---

### Post by samosater on 2014-01-15
The error code is similar:

samosater@samosater-desktop:~$ sudo mount -t ext4 -o ro /dev/mapper/vg1-lv1 /mnt
[sudo] password for samosater: 
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

samosater@samosater-desktop:~$

---

### Post by ian-weisser on 2014-01-15
Mounting an LVM partition: [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by samosater on 2014-01-15
Thanks. I'm reading through that tutorial now... over and over. =p

Do I really need to reinstall Ubuntu on HD161HJ? Can it be done from the present installation? What about preserving and mounting the data on the ST4000DM000 slave?

---

### Post by squakie on 2014-01-15
> **Bucky Ball said:**
> Try:

sudo mount -a

(PS: Generally 'sudo' is used to issue commands as root rather than changing to root permanently with 'sudo su'. You're best to avoid that. ;))
Thanks for catching that! ;)

---

### Post by steeldriver on 2014-01-15
I don't think there's anything wrong with the way you are trying to mount the volume - maybe the filesystem was not cleanly unmounted? what does the team think about an fsck?

---

### Post by squakie on 2014-01-16
Hummmm.....a dumb question I'm sure, but did you install the lvm package?  I looked in synaptic on my 13.10 desktop and by default the lvm package itself is not installed.  It looks like some sort of supporting library(ies) may be, but not the actual lvm package.  I know squat about lvms, so someone may correct me, but if that package isn't installed I would try installing it first:

sudo apt-get install lvm2

Also - was this volume part of a volume set, or was this a volum onto itself?  If part of a volume set I would think that could pose a problem if the other volume(s) aren't present.  Again, someone will correct me if I'm way off base here.

---

### Post by samosater on 2014-01-16
It was already installed, but I did it anyway:

samosater@samosater-desktop:~$ sudo apt-get install lvm2
[sudo] password for samosater: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
samosater@samosater-desktop:~$ 

[STCG4000100]("http://www.seagate.com/www-content/product-content/goflex-fam/seagate-central/en-us/docs/seagate-central-ds1773-1-1212-us.pdf") is a pretty basic single HDD  (the ST4000DM000) NAS. It was natively structured like [this]("http://cubeupload.com/im/Samosater/SDCST4000DM000.jpg").

---

### Post by Bucky Ball on 2014-01-16
> **samosater said:**
> 
```
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```


Run:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by samosater on 2014-01-16
Oops! You're right. I won't flood the topic with all the code that came out, but now i got:

samosater@samosater-desktop:~$ sudo apt-get install lvm2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lvm2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
samosater@samosater-desktop:~$ ^C
samosater@samosater-desktop:~$

---

### Post by Bucky Ball on 2014-01-16
Well, you have the latest lvm2 then and an updated machine! ;)

---

### Post by samosater on 2014-01-16
Cool. 

Still can't mount ST4000DM000, though.

---

### Post by steeldriver on 2014-01-16
EDIT: you may be facing the same issue as here --> [http://ubuntuforums.org/showthread.php?t=2198460&page=2&p=12903047#post12903047](http://ubuntuforums.org/showthread.php?t=2198460&page=2&p=12903047#post12903047)

---

### Post by samosater on 2014-01-19
Thanks. A lot of info now. It seems that fuse-ext2 can solve this. I'll update you folks soon.

---

### Post by samosater on 2014-01-19
This looks so promising:

samosater@samosater-desktop:~$ sudo fuseext2 -o ro -o sync_read /dev/mapper/vg1-lv1 /mnt
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: enter [do_probe (do_probe.c:30)]

fuse-umfuse-ext2: leave [do_probe (do_probe.c:55)]
fuse-umfuse-ext2: opts.device: /dev/mapper/vg1-lv1 [main (fuse-ext2.c:358)]
fuse-umfuse-ext2: opts.mnt_point: /mnt [main (fuse-ext2.c:359)]
fuse-umfuse-ext2: opts.volname: Data [main (fuse-ext2.c:360)]
fuse-umfuse-ext2: opts.options: ro,sync_read [main (fuse-ext2.c:361)]
fuse-umfuse-ext2: parsed_options: sync_read,ro,fsname=/dev/mapper/vg1-lv1 [main (fuse-ext2.c:362)]
fuse-umfuse-ext2: mounting read-only [main (fuse-ext2.c:378)]
samosater@samosater-desktop:~$ 


Nautilus says I don't have the parmissions for that directory.

---

### Post by steeldriver on 2014-01-19
from the command line, can you see anything using ls?

```
ls -l /mnt
```

---

### Post by samosater on 2014-01-19
samosater@samosater-desktop:~$ ls -l /mnt
ls: cannot access /mnt: Permission denied
samosater@samosater-desktop:~$ sudo ls -l /mnt
[sudo] password for samosater: 
total 640
drwxr-xr-x  3 root      root       65536 Jul 16  2013 anonftp
drwxr-xr-x  3 root      root       65536 Jul 16  2013 dbd
drwxrwxrwx  2 samosater samosater  65536 Jul 16  2013 ***
drwxrwxrwx  2 samosater samosater  65536 Jul 16  2013 ***.tm
drwx------  2 root      root      131072 Jul 16  2013 lost+found
drwx------  2 root      root       65536 Jul 17  2013 mt-daapd
drwxrwsr-x 10 nobody    nogroup    65536 Dez  5 02:33 Public
drwxr-xr-x  5 root      root       65536 Jul 16  2013 twonky
drwxr-xr-x  5 root      root       65536 Jul 16  2013 TwonkyData
samosater@samosater-desktop:~$ 

the 'Public' folder has everything.

---

### Post by steeldriver on 2014-01-19
so you should be able to read (and copy data off) the device - if you need to do that graphically, use

```
gksudo nautilus
```
or
```
gksu nautilus
```

etc. (KDE has kdesudo I think) depending on which Ubuntu you are running

---

### Post by samosater on 2014-01-19
Thanks, steeldriver.

Got into the sudoed Nautilus, but ended up using the terminal (gotta tame this beast). ](*,)

samosater@samosater-desktop:~$ sudo cp -r /mnt/Public /media/samosater/Rotativo

Now the prompt blinks on an on... this will take a long time, it seems. I'll update ASAP.

---

### Post by samosater on 2014-01-19
Almost there. The only problem there is that it took some 4 hours to copy 60MB. I've been reading that fuseext2 (!!) might be the culprit. Is there a way around it?

---

### Post by steeldriver on 2014-01-19
sorry I know nothing about fuseext2 beyond the couple of links I posted in the other thread - I'm not sure why the sync_read mount option was suggested there, or whether that could have an impact on read bandwidth - there also appears to be a large_read mount option which sounds like it *might* make  a difference but I'm just guessing

---

### Post by samosater on 2014-01-21
**Many many many thanks folks**.

Fuse-ext2 may be slooooooow... but it did save the day here.

I'd start a new thread when I got tired of trying to make it read faster. BTW '-o large_read' is not accepted.

Anyway, even if it took me a few months 24/7 (as it probably will) to get this data back it's well worth the trouble.

Until then, lots of Linux to study, and a RAID1 or something like that for the near future.

---

### Post by tony58 on 2014-08-16
Hello
I am having the same problem with a failed Seagate Central device. 
I am not sure how to solve this problem and I am not clear, reagarding, how you good folks solved the problem. Currently, I have data recovery software that I am using via Windows; however, the meta data lacks the same meaning when the drive was in the Seagate Central enclousure. Are there a series of commands that I need to enter via command line in Ubuntu?

---

### Post by Bucky Ball on 2014-08-18
Hi Tony58. May I suggest that you will improve your chances of support by starting a new thread regarding your problems. This thread is over six months old and pretty much dead. Good luck.

---

### Post by rengeko on 2014-11-22
I have a question for the OP, how did you crack the case of the NAS?  I don't see any screws, so I'm not sure how to open it.  I have an adapter,  but until I can get it open, no use.

---

### Post by Bucky Ball on 2014-11-23
> **rengeko said:**
> I have a question for the OP, how did you crack the case of the NAS?  I don't see any screws, so I'm not sure how to open it.  I have an adapter,  but until I can get it open, no use.

Welcome. Please post a new thread regarding your current issue. No life here. Good luck. ;)

---

