---
title: "Can I add Windows XP to already installed Ubuntu &amp; dual-boot?"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-03-15
I have already installed Ubuntu and have downloaded several apps (WINE, PdfShuffler, JAVA, UbuntuOne, etc). I have also installed Lubuntu. I can presently dual boot to Lubuntu or Ubuntu. I would like to be able to boot into Windows XP too, I have the TOSHIBA Windows XP Recovery/Applications & Drivers DVD that came with the new PC.   

I would like to avoid having to reinstall Ubuntu & Lubuntu -- too much work. 

QUESTION: Can I add Windows XP to the already installed versions of Ubuntu & dual-boot? Or do I have to erase Ubuntu & Lubuntu in order to install Windows first, then install Ubuntu and/or Lubuntu after Windows?

Thank you,

RM

---

### Post by mikewhatever on 2014-03-15
It depends on what the recovery DVD actually does. Some of them wipe the HDD clean and reinstall XP without asking question. If that's the case with yours, then yes, you'll need to redo it all. 
It might be easier to back up the Ubuntu partition with Clonezilla or [TAR]("https://help.ubuntu.com/community/BackupYourSystem/TAR"), and then restor it after XP is in place.

---

### Post by AbleTassie on 2014-03-15
Thanks Mike, I think my WIndows XP Recovery DVD in general does wipe the HDD clean; I am not sure I can use it in any other way. I have an external 160 GB hard drive (USB connection) that has 102.GB free (57.9 GB used). The Ubuntu part of my 100 GB internal hard drive has 41.6 GB available and 5.8 GB used. The Lubuntu part of my internal (100GB) hard drive has 46GB free (i.e., 9.6% full). So that's about 10 to 11 GB of files for both Ubuntu and Lubuntu combined. 

QUESTION(s) #1: I suppose I could use TAR with my external 160GB hard drive couldn't I? 

I do not think I can boot off my USB port however, if this is necessary. The TOSHIBA BIOS boot screen gives me the following boot options: 1)HDD, 2)CD/DVD, 3)FDD (floppy disk drive) and 4)LAN. I do not have an FDD (floppy disk drive), one never came with the PC when I bought it new. Not sure why TOSHIBA includes FDD as an option. I do not think that selecting FDD will allow a USB port boot. 

QUESTION(s) #2: I was reading some of the other related archived threads and it looked like maybe I could make image copies of the Ubuntu and Lubuntu files and then use these image files in some way to create a multiboot option. Would this be any easier than TAR? Is Clonezilla any easier than TAR? Where can I find info on Clonezilla?

Thank you,

R.

---

### Post by Mark Phelps on 2014-03-15
Most of the XP-era OEM restore disks do erase and restore the entire hard drive.  So, yours working that way is not unusual.

An easy-to-use backup/restore program is RedoBackup.  It uses menus and a minimum number of clicks to do backups and restores. Not as flexible as Clonezilla but a whole lot easier to use.

You don't have the USB boot option -- and you're right, selecting FDD will not boot from USB.  You would have to boot from CD/DVD.

When you make an image copy, you are basically making a compressed image of the partition you select.  You can then restore that entire partition from the saved backup.  That doesn't, in and of itself, create any multiboot options.

---

### Post by monkeybrain20122 on 2014-03-15
Put XP in virtualbox and disable networking. Its support ends in April, it is time to get rid of XP not to put it in a dual boot as a viral magnet. :)

---

### Post by SeijiSensei on 2014-03-15
I second VirtualBox over a dual-boot arrangement, unless you intend to use Windows for gaming.  In that case, you'll have problems with games that only work with video cards that support 3D acceleration.  I cannot get Final Fantasy XIV to run on Windows 7 in a VirtualBox virtual machine because the game will not work with the emulated graphics adapter. The machine itself has an ATI Radeon 6770M, but the virtual machine sees only an emulated Intel graphics adapter.

---

### Post by Barkester on 2014-03-16
Fresh reinstall everything. There's probably another way, but unless you're a proffessional, forget it and it would probably be more hassle even to them. Windows demand the first partitions, (7, I think) period. Likely you'd spend many hours as I did searching for a simpler answer. Coulda had the job done in that time and ended up reinstalling all anyway.

   Believe me, Fresh reinstall IS the easy way. Good luck.

---

### Post by AbleTassie on 2014-03-16
Thanks Mark. Unfortunately my CD/DVD drive only burns CDs, it reads DVDs, but does not burn DVDs. The Ubuntu and Lubuntu files are both bigger than 700 MB -- too big for a CD. Thus I am not sure I can use RedoBackup unless I can somehow: **option 1)** use my external USB 160GB hard drive as an intermediary or **option 2)** run a cable (ethernet or USB) from my laptop to a library computer. 

**For option 1)** I guess I would make an image copy of the Lubuntu and Ubuntu partitions and store them on my external USB 160 GB hard drive. Then maybe I can use RedoBackup to put the Lubuntu & Ubuntu images back on my internal hard drive from my external USB 160 GB hard drive.

**For option 2)** I guess I would somehow connect my laptop to a library library computer and use RedoBackup to burn copy of the image of each Ubuntu partition onto a DVD in the library's DVD burner.

The only other way I can see to use RedoBackup or Clonzilla, etc is to somehow burn a DVD image for both Ubuntu & Lubuntu from my 160 GB USB external hard drive using a library computer. Then use each of those DVDs to create a multiboot option after installing Winows XP.

QUESTION: But I am not sure I can use my external 160GB USB hard drive as an intermediary in this way. Can I?

I am not sure I can use a library computer as dscribed above either. Can I?

Thanks,

R.

---

### Post by AbleTassie on 2014-03-16
> **monkeybrain20122 said:**
> Put XP in virtualbox and disable networking. Its support ends in April, it is time to get rid of XP not to put it in a dual boot as a viral magnet. :)

Thanks Monkeybrain (and SeijiSensei),

Unfortunately my PC only has 1.25 GB of RAM memory. This is too little for virtualbox, isn't it? I know Windows XP support ends in April. But I don't think I can use Ubuntu or any other Linux variant as a substitute for what I want to do -- I tried and it failed. I would only use Windows XP for this one internet activity and Ubuntu for everything else, especially internet.

Thanks,
R.

---

### Post by monkeybrain20122 on 2014-03-16
> **RMcGinnis said:**
> Thanks Monkeybrain (and SeijiSensei),

Unfortunately my PC only has 1.25 GB of RAM memory. This is too little for virtualbox, isn't it? I know Windows XP support ends in April. But I don't think I can use Ubuntu or any other Linux variant as a substitute for what I want to do -- I tried and it failed. I would only use Windows XP for this one internet activity and Ubuntu for everything else, especially internet.

Thanks,
R.

Using XP on the internet is exactly what you shouldn't do after April. Maybe you can post your problem and see if there are alternative solutions. It is time to put XP out of misery.

---

### Post by JKyleOKC on 2014-03-16
> **RMcGinnis said:**
> Unfortunately my CD/DVD drive only burns CDs, it reads DVDs, but does not burn DVDs.Can your machine boot from a USB port? Most recent models can do this, but many machines from the XP era don't have that capability. If yours can boot from USB, you could use an 8-GB flash drive instead of burning a DVD; even 4 GB might be large enough since I don't think the live DVD is actually that large, but DVDs can hold up to 4.7 GB so an 8-GB drive would be safer.

You're correct that 1.25 GB of RAM isn't enough for comfortable virtualization, although I have in the past run VirtualBox on a machine with even less than that much. It worked, but was far too slow to be comfortable because the VM kept swappiung back and forth to disk. I consider 3 GB to be the bare minimum now; the host system needs at least 1 GB for itself, and most VMs seem to like having a full GB also. The third one is for a safety factor!

---

### Post by mikewhatever on 2014-03-16
> **RMcGinnis said:**
> 

QUESTION(s) #1: I suppose I could use TAR with my external 160GB hard drive couldn't I? 

I do not think I can boot off my USB port however, if this is necessary. The TOSHIBA BIOS boot screen gives me the following boot options: 1)HDD, 2)CD/DVD, 3)FDD (floppy disk drive) and 4)LAN. I do not have an FDD (floppy disk drive), one never came with the PC when I bought it new. Not sure why TOSHIBA includes FDD as an option. I do not think that selecting FDD will allow a USB port boot. 

You'll need some kind of external storage to hold the backups. A 160GB HDD sounds good, and you won't need to boot from it.

> 
QUESTION(s) #2: I was reading some of the other related archived threads and it looked like maybe I could make image copies of the Ubuntu and Lubuntu files and then use these image files in some way to create a multiboot option. Would this be any easier than TAR? Is Clonezilla any easier than TAR? Where can I find info on Clonezilla?


Not sure what you've read, but I suspect it won't be "easy" either way, especially if it's your first time. The easiest option would be to reinstall everything, and start afresh.

---

### Post by AbleTassie on 2014-03-16
> **monkeybrain20122 said:**
> Using XP on the internet is exactly what you shouldn't do after April. _**Maybe you can post your problem and see if there are alternative solutions.**_ It is time to put XP out of misery.

_**Here is my problem:**_ I was not able to do a document desktop sharing interview using a large government organzation's (LGO's) WebEx account. This was a big deal for me. Based on reading the error message I got, the failure was apparently due to the version of JAVA I am using. The LGO's protocols and firewall require that a person use their WebEx account, not the person's own WebEx account for such an interview.  

I had previously downloaded and installed the version of JAVA recommended on this forum ([http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)) and it has _generally_ worked well with Ubuntu and Lubuntu. I have been able to do three activities with Ubuntu & Lubuntu that require JAVA: **1)** log onto my free WebEx account and do desktop document sharing using my own account, **2)** & **3)** I can access 2 secure portions of the LGO's website that require a digital certificate and password.  

My only apparent failure due to JAVA was with the LGO doing a desktop document sharing interview using *_their_* WebEx account. A colleague was able to join the meeting using Windows. So I think I'd like to try the usual version of JAVA with Windows XP to see if I can do a desktop document sharing interview with the LGO.  

I think the most foolproof way of giving this a try is by dual booting, rather than virtualbox. And I've heard that I really don't have the RAM for virtualboxing. Is this true?

Thanks,

RM

---

### Post by AbleTassie on 2014-03-16
> **JKyleOKC said:**
> Can your machine boot from a USB port?  I don't think it can boot from the USB port.

R.

---

### Post by AbleTassie on 2014-03-16
> **RMcGinnis said:**
> Thanks Mark. Unfortunately my CD/DVD drive only burns CDs, it reads DVDs, but does not burn DVDs. The Ubuntu and Lubuntu files are both bigger than 700 MB -- too big for a CD. R.

I guess the Ubuntu and Lubuntu files are too big for a DVD too. They are each around 5 GB. So maybe people really don't use DVDs in these type of processes like I thought. But maybe an image would be compressed enough so they could be written to a DVD? I am not sure.

Maybe I can use my 160GB external USB drive and RedoBackup would write an image of each Ubuntu partition to the external drive. Then perhaps RedoBackup would allow me to copy the Ubuntu partitions back on the internal hard drive in their own partitions after Windows is installed.

What do you guys think?

Thanks,

R.

---

### Post by monkeybrain20122 on 2014-03-16
I can't really tell you anything about the Java problem, wonder if the document sharing thingy works with Mac.

If you want to copy and restore the whole linux install the easiest way is to use fsarchiver. It is in the Ubuntu repository.

Basically you need only two commands and it is better than clonezilla because clonzilla requires the partition to restore to to be >= the original one even if source partition is mostly empty. This is a show stopper for clonezilla if you copy and restore between different devices or repartition your drive. clonezilla would work if the clone is just for backup and only restored to the same partition, but not if you want to transfer it or repartition because the target partition may very well be smaller than the source partition.

[http://ubuntuforums.org/showthread.php?t=2205907&page=2](http://ubuntuforums.org/showthread.php?t=2205907&page=2)

**Edited:** If you cannot boot from a ubuntu live usb to install fsarchiver, just get the rescue cd with fsarchicer already on it. It is smaller than the ubuntu iso too. 
[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

---

### Post by AbleTassie on 2014-03-16
> **mikewhatever said:**
> You'll need some kind of external storage to hold the backups. A 160GB HDD sounds good, and you won't need to boot from it.

Not sure what you've read, but I suspect it won't be "easy" either way, especially if it's your first time. The easiest option would be to reinstall everything, and start afresh. 

Thanks Mike Do you think that RedoBackup would allow me to use the  external HDD to copy the Ubuntu partitions onto it and not boot from it  as well?

It won't be all that easy to reinstall all the plugins for Ubuntu. It will take time. Do you have much experience with RedoBackup? Would it really be that much harder to use TAR, Clonezilla or RedoBackup compared to reinstalling everything from scratch?

Thanks,

R.

---

### Post by electrohandyman501 on 2014-03-16
R. Something else you might want to look into before you spend too much more time with XP, the LGO agency that you are wanting to work with, after April, will they allow you to connect using an XP Machine?
In the gvmt org I work for, we have been directed to replace/remove any/all XP (or older) machines from active network connections. No longer allowed to use for any network required activity.

---

### Post by AbleTassie on 2014-03-16
[SIZE=3]Thanks Handyman,

What about Windows Vista? Does the LGO you work for still want to interact with Windows Vista? I am talking about the US Govt. Is this the US govt you are talking about? Would they normally tell somebody what operating system and plug-ins (e.g., JAVA) are likely to be problematic if a person asked?  

I might be able to install Windows Vista on this machine if Windows XP becomes a pariah.

Thanks,

R.
[/SIZE]

---

### Post by AbleTassie on 2014-03-19
Thanks to everybody: Mark, Monkeybrain, Handyman, Jim, Barkester, Seiji and any others I missed.

Great advice!

R.

---

