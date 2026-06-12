---
title: "Boot problem with Windows XP after installing Xubuntu"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by Peter_Heft on 2013-10-31
My guess is that rewriting the partition in testdisk did the  trick,because the drive was still toast according to recovery console  after rewriting MBR.

Trying to get Xubuntu installed on 80gb HD, I allowed installer to put grub on 120gb HD, which has XP on it.  Got message "unable to install Grub". Could not get either OPs to boot. Could not get boot-repair to install in a live USB.  Installed Xubuntu 12.04 on 80gb HD, which will boot if HD in first position.  Boot-repair report link is below.

[http://paste.ubuntu.com/6338471/](http://paste.ubuntu.com/6338471/)



I do not have XP CDs.  I am guessing the MBR or bootsector can be repaired but am asking for help because I don't want to screw up again.
I have PLoP on a floppy, which got me able to boot the live USB.  I am thinking I can use that to boot XP if you can help me get it bootable.
Most of the files are backed up but it would help to be able to boot it again.
Thanks in advance for the help.

---

### Post by oldfred on 2013-10-31
Link did not work as posted - number is different than displayed number. Is this correct?
[http://paste.ubuntu.com/6338471/](http://paste.ubuntu.com/6338471/)

It shows grub in sda, your 80GB drive, but does not show any partitions at all on sdb.

What does testdisk say about sdb?

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
            Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Peter_Heft on 2013-11-01
Hi oldfred!  Thanks for the help. Sorry about the pastebin link, you found the right one.  Testdisk.log is attached.  120 Gb HD is not bootable, but looks to me like something is there.  Would just the MBR have been overwritten or more?  Please advise how to proceed.
Thanks

---

### Post by oldfred on 2013-11-03
Testdisk seems to find one large NTFS partition on your 120GB drive. Did you try writing it to drive or from Windows run chkdsk?

---

### Post by Peter_Heft on 2013-11-03
Thanks oldfred.  While looking for best option to fix this from Xubuntu: lilo, testdisk or boot-repair, I found a tutorial for using a bootable xp recovery console cd on bleeping computer.  It is amazing what you can find if you keep looking. I am going to give that a try.  I'll return to report how it went.  I didn't include a link to bc in case it's not legal.
Thanks.

---

### Post by Peter_Heft on 2013-11-04
Not much success with xp recovery console.  Listsvc returned nothing.  Chkdsk found one or more unrecoverable problems. Fixmbr let me write generic win MBR. Fixboot couldn't find the drive.  I ran testdisk again and it is a bit less scary. I did rewrite the partition while in there. It looks like the files are there, the booting is shot. Will the [Advanced] option filesystm utilities do the trick?  How?   Thanks.  You had asked if I had "written it to drive" not sure what you mean.  I ran the recovery console from a bootable CD.  Result above. I took a look at the advanced options and it must be time to restore the NTFS boot sector from its backup (**Backup BS**) .  Will report back.

---

### Post by Peter_Heft on 2013-11-04
That wasn't quite as sucessful as I had hoped.  Backup boot sector was identical to the primary, so that wasn't possible.  Rebuilding a boot sector produced the message; Extrapolated boot sector and current boot sector are identical. Evidently it has a valid boot sector, even if not valid for windows, but I can't see it from Xubuntu either.  Please help, I'm stuck.

---

### Post by Peter_Heft on 2013-11-04
My guess is that rewriting the partition in testdisk did the trick,because the drive was still toast according to recovery console after rewriting MBR.  I have a kind of dual boot system.  HD "a" has Xubuntu on it and will boot since bios looks there. HD "b" has XP on it and will boot if selected in PLoP on the floppy.  Neither OS can see the other HD which is easy to live with.  Now I get to fix the video problems.  Thanks for pointing me in the right direction, I hope I can remember half of what I learned. Peter

---

### Post by oldfred on 2013-11-04
Is this an older system with IDE drives and jumpers not BIOS selection of boot device. Then only the primary master is bootable. Or you may have a somewhat newer IDE with cable select but not have correct cable or jumper setting?

       with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Peter_Heft on 2013-11-05
It is the old system and used to have jumpers but when I added the 120 GB drive, I believe the directions from Western Digital said to junk the jumpers. The reason I was looking at Linux was that XP is going to be unsupported soon.  I am liking what I have seen so far.  Thanks again for the help.

---

### Post by Peter_Heft on 2013-11-05
Sorry, sometimes I'm a bit slow.  You were saying that I need the jumpers for this setup.  I was in XP yesterday when I saw your post.  I haven't been able to boot into Xubuntu since.  Today the Xubuntu HD was in first position and  jumpered as master, The XP drive was second and jumered as slave and bios booted it once. Bios won't recognize either HD since that boot. I have put XP drive first in line and jumpered it for master.  Xubuntu second and Jumpered for slave.  Bios can't detect.  I am now in a live Wary Puppy because it loads fast and I still had it on a usb.  Wary can see both drives and the files on them. What did I manage to screw up now?

It seems to be time for a rescue CD/USB with testdisk and boot-repair on it. Could you recommend some such thing.  I looked and found too many but nothing that did what I wanted.  I  could not get boot-repair to install in a live USB of Xubuntu earlier so would like to try a live usb with with the repair apps included.  Wary seems to have totally different apps.
Please help. Thanks. Peter

---

### Post by oldfred on 2013-11-05
I always hated the little jumpers and as soon as SATA was only a few dollars more than IDE, I converted to new motherboard and SATA drives. Then software controls everything.

Double check wiring & jumpers. Back in PATA days I could not open case without slightly bumping one of those wide cables. Sometimes it would look connected and might even power up, but when pushed it went in further and worked. So I always double & triple checked connections. 

I think the repair cds that are gparted and parted magic include more than just gparted.
       [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

I have current versions of both on my flash drive, but have not booted them recently. Before system booted with flash drives I used to burn a new CD of several repairCD just in case.

      
 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Peter_Heft on 2013-11-07
Thanks again for the response and help.  I checked all of the ribbon connections and noticed that the 2 hard drives are not connected as I had remembered.  They used to be on the same cable. One of the IT guys at work put XP on this machine a few years ago, it came with Millennium junk. He evidently changed a few things. There are 4 connectors on the motherboard. Primary IDE has the 120 GB XP HD plugged into it. Secondary IDE has the Floppy and the digital drives.  Primary ATA100 is open.  Secondary ATA100 has the 80 GB drive with Xubuntu. Bios detects no primary master or slave  drives, but I think it detects the drive with xp on it as secondary. Can't check right now, chkdisk is slowly repairing. After enough clues the mystery makes some sense. Should both drives be on the same cable plugged into primary ATA?  Does the order matter?  The default repair that boot-repair would make is rewrite Grub2 onto the boot sector(?) of the Ubuntu drive. Might that make the drive bootable?  I eagerly await your response and this PC being willing to boot both OSs.

---

### Post by oldfred on 2013-11-07
Most of my old motherboards only had two PATA or IDE connectors. But my last one did have a BIOS that supported cable select, so you could choose boot drive from BIOS, not just with jumpers on hard drive. But jumpers had to be set to cable select and you have to have the 80 conductor cable or the one with three different colors for each connector. I once tried to use a 40 conduction cable that came with a CD for a hard drive and wondered why it would not boot.
So does BIOS support cable select or setting boot drive in BIOS?

---

### Post by Peter_Heft on 2013-11-07
Thanks, oldfred.  Speaking of old motherboards, I bought this PC in November of 2000. It came with a 20 GB HD. The mb user's manual says to connect drives on one cable with the slave between board and master. Non UltraDMA/100 / UltraDMA/66 devices should  be connected to the secondary IDE connector.  The manual talks about using the cable with the 3 different colored connectors, but this one is black on both ends with gray in the middle. They are 40 pin 80 conducter cables. You may configure two hard discs to both be masters with 2 cables, one for primary, one for secondary connector. You may install one os on an IDE drive and another on an SCSI drive.  There is no mention of cable select. Boot drive is set in BIOS. Floppy, IDE HD, ATAPI CD-ROM or other which includes SCSI/Onboard ATA boot device.
How does this work since both drives are SCSI? Do they get chained together on one secondary connector? BIOS should let me pick which one to boot. One of the drives had been hooked up to a primary connector, which is not recommended in the manual, but it used to work.
Thanks again in advance,
Peter

---

### Post by oldfred on 2013-11-07
Are you sure drives are not just IDE? I am not familiar with real SCSI drives as those were server drives not desktop and used totally different connectors.

It seems you may just have 40 conductor cables. It might be worthwhile to buy new 80 conductor cables, but if system is that old I hate to even spend any money on it.

---

### Post by elliotn on 2013-11-07
IDEs and jumpers are sometimes confusing. try playing around with then and u will get it right

---

### Post by Peter_Heft on 2013-11-08
The boot-repair log in the first post seemed like a good place to look for what kind of drives they were and on lines 402 and 413 it says ATA...........(scsi).  The cables and connectors are IDE, so what does that (scsi) mean.
I got XP to boot again after chaining them together and plugging them into the primary connector where the optical drives used to be. I didn't think it was going to work because no primary drives were detected, possibly secondaries but it went by too fast to see what was there.  The next message said that BIOS 100 was not being started because no drives had been detected. And then I saw the XP logo and it booted. The boot order in BIOS was still set for floppy then CD then installed SCSI from the previous try.  It may be just another one-time boot but we will have to wait till later, it is too late to continue now.
Thanks again for your help.
Peter

---

### Post by oldfred on 2013-11-08
In Linux they consolidated the ATA and SCSI disk drivers into one about 4 or 5 years ago. It used to be hda (ATA) or sda(SCSI), but now most Linux systems just use sda for all drives.
A few distributions may still use hda for drives, but still seem to have the consolidated or standard Linux driver.

---

### Post by Peter_Heft on 2013-11-08
I now have a dual boot system with Xubuntu on sda and XP on sdb.  Spent way too much time trying find a way to get boot-repair installed in a live CD or USB to try to fix the boot for Xubuntu, nothing worked.  Gave up and reinstalled Xubuntu.  It offered me the choice of overwriting the existing which was on sda, so it ended up where I wanted it.  What would the install have done for a dual install with XP using up 75% of sdb and sda empty?
The IDE (yes) hard drives were a bit slow when plugged into the primary ide connector so I moved them to the primary ultra 100 IDE connector which matches the HD speed.  Now on to getting to know Xubuntu.
Thanks for all the help.
Peter

---

### Post by oldfred on 2013-11-08
Glad you got it working. :)

---

### Post by Peter_Heft on 2013-11-11
WE got it going.  Thank you for your help!

---

