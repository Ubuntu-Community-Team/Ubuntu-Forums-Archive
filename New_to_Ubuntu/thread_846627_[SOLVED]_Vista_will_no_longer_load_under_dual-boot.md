---
title: "[SOLVED] Vista will no longer load under dual-boot."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by AllPowerfulOz on 2008-07-01
Hi guys. Just installed Ubuntu onto my Dad's laptop and so far Ubuntu's working fine. Vista, however, is not. In the boot menu I get a choice of;
Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest86+
Other operating systems:
Windows Vista/Longhorn (loader)

When I run Vista I get the message;
[INDENT]Windows error recovery
Windows failed to start. A recent hardware or software change might be the cause.

If windows files have been damaged or configured incorrectly, Startup Repair can help diagnose and fix the problem. If power was interrupted during startup, choose start windows normally.
(Use arrow keys to highlight your choice.)

Launch startup repair
Start windows normally[/INDENT]

If I select startup repair, windows seems to start loading but an error message appears saying "The installed program cannot start. Click OK to turn off the computer."

If I select start windows normally, it starts to load up until the Blue screen of death flashes and disappears. I can't read the error message as it goes away too quickly.

When I run sudo fdisk -l I get:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64d63c35
Device Boot       Start       End      Blocks       Id       System
/dev/sda1             1       192     1536000       27       Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *       192      7434   58173828+        7    HPFS/NTFS
/dev/sda3         12352     19011   53483398+        7    HPFS/NTFS
/dev/sda4         19012     24321   42652575         5    Extended
/dev/sda5         19012     24098   40861296        83    Linux
/dev/sda6         24099     24321    1791216        82    Linux swap / Solaris
```

I think the problem may have something to do with "Partition 1 does not end on cylinder boundary." but honestly have no idea.

I'd like to be able to save Windows and Ubuntu, but Windows takes priority. It *has* to be working. Any help give will be hugely appreciated. Thanks in advance.

---

### Post by sea_monkey987 on 2008-07-01
did you resize the vista partition with the ubuntu live cd or gparted?
If so, check this page - [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by bumanie on 2008-07-01
I suspect that the windows mbr is corrupted. With vista you will have to use the recovery disk that you should have got with the computer to do a rep[air on the mbr. The recovery disk is quite easy to use. If you don't have a recovery disc, you may have to use something like super grub disc or testdisk to write a windows-like mbr to your ntfs partition. Not sure whether ntfsprogs has a tool for fixing windows mbr.

---

### Post by AllPowerfulOz on 2008-07-01
It came with a Toshiba backup disc, but that erases all the had disks which I want to avoid. How would I create a windows-like mbr?

EDIT: Will the windows anytime upgrade disc do?

---

### Post by sea_monkey987 on 2008-07-01
> **AllPowerfulOz said:**
> It came with a Toshiba backup disc, but that erases all the had disks which I want to avoid. How would I create a windows-like mbr?

EDIT: Will the windows anytime upgrade disc do?

I really don't think restoring the mbr would fix it since you installed grub (that nuked the windows code from the MBR; however the almost-same code is still there in the windows partition).  I'm not sure the anytime upgrade disc would work but here's a link to an iso to download the vista recovery disc [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Of course, I could be wrong.  The problem may indeed be in the MBR.  So, I really need to know if you resized any partitions using the ubuntu or gparted.

---

### Post by AllPowerfulOz on 2008-07-01
I know it's kind of rude, but bump.

Also, could [this](http://sathyasays.com/2007/06/12/vista-ubuntu-dual-boot/) be the problem and solution?

EDIT: Thanks Seamonkey! I resized the partitions using the live CD. I'll try the vista recovery disc and see how it goes.

---

### Post by sea_monkey987 on 2008-07-01
Also look here [http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/) for the well-known error that occurs when you resize a vista partition using the live cd.  While the procedures there should work, BACKUP YOUR DATA!!!  Messing with hard drive partitions can damage them (however remote the probability).  You don't want to be stuck with an unbootable and unreadable hard drive.  You can mount your windows partition from the ubuntu OS to backup.

---

### Post by bumanie on 2008-07-01
Strange back-up disc if it destroys everything!! Must be M$'s or toshiba's form of a joke.
As I said, I only suspect that it is the mbr - could be something else. You can use [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") (think it's in the repositories as well) or wait and see if someone else has a better solution. Make a mistake with testdisk and you'll probably destroy data anyway, so read documentation carefully before doing anything. Super grub disk is [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) - it has a 'fix windows boot' function. 
What you describe does sound like a corrupt mbr - as you can imagine it's hard when one can't see things themselves. My understanding was if you invoke the recovery partition, everything gets wiped and you are left with a 'raw OS', but if you use a M$ rescue disc, it should attempt to rewrite the bootloader or recover whatever else it finds wrong. I, however have minimal experience with vista - I find it very slow and tedious and thus use ubuntu only. [Neosmart]("http://neosmart.net/blog/2008/how-to-repair-the-windows-vista-bootloader/") have a section that may help, look there too. I remembered reading about neosmart having a vista repair cd/dvd from when vista was still in testing stage. Good luck. Hope something works and you keep all your data.

---

### Post by sea_monkey987 on 2008-07-01
> **bumanie said:**
> Strange back-up disc if it destroys everything!! Must be M$'s or toshiba's form of a joke.
It won't destroy everything.  The data can still be there, just the indexes pointing to the data can get corrupted.  I say this because I have had the startup repair go on forever - I had to manually unplug the power cord.   I ended up doing a complete reinstall.  Anyway, startup repair should fix the problem as bumanie's solution and howtogeek's solution are essentially the same:  boot into the recovery disc and run the startup repair

EDT: I just realized you were referring to the Toshiba disc-not the vista disc.

---

### Post by AllPowerfulOz on 2008-07-01
Thanks guys. I'm almost 100% certain that resizing the partition was what caused the problems. I'm gonna sleep now (1:30am here) whilst that recovery disc is downloading. Thanks again. ;)

---

### Post by AllPowerfulOz on 2008-07-02
Hmm... I've run the Vista recovery disc, and when it gets to the screen where I select the operating system to restore, there are none listed. Just tells me "If you do not see your operating system listed, click load drivers to load drivers for your hard disk." Anyone know where those drivers are? Or should I try supergrub instead?

EDIT: Never mind. Got it to work. Thanks again you two. ;)

---

