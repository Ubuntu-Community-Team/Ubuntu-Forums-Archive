---
title: "New User: Problem with install"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Jeff895 on 2008-05-01
I partitioned my hard drive with Norton Partition Magic for 30 Gb free space and labeled it
I:Linux

When I installed Ubuntu it installed on that drive. I now have 19.2 GB free on it.

After installing I reboot (my pc says shutting down for 20 minutes and then i unplug). Upon reboot it asks me if i want to boot xp or ubuntu. I choose ubuntu.

I then get this error:
find--set-root--ignore-floppies /ubuntu/disks/boot/grub/menu.1st
Error 15: File Not Found

So I rebooted went into windows setup, deselected my supposed floppy drive, rebooted, and same error.

I googled the error but i cant make sense of it. Ill keep looking of course. Thanks again for any further help.

Also for any future reference I have no experience in Linux but am determined to get it going. Will keep a close eye on my post.

---

### Post by mac9416 on 2008-05-01
Man, I'm a newb too but I hate you haven't got any replies yet so I'll offer you what advice I have.
I have a gift for misreading posts but it seems to me you:
[LIST=1]
[*]Resized your Windows partition with a Windows program
[*]Installed Ubuntu
[*]Rebooted The computer (which hung in the process)
[*]When you had to force it to reboot and tried to start Ubuntu and it failed
[/LIST]
This is where I got confused. You "rebooted went into windows setup, deselected my supposed floppy drive"? I'm not sure what you mean but maybe it doesn't matter.:)

Then you rebooted and got the same error.

Well if I were you I would reboot into Windows and reformat your hard drive into one large Windows partition (I'm not sure if that's possible or safe but I still want to TRY and help:)) then boot your Ubuntuu live cd. Once booted I would install Ubuntu, using the installation program's partitioner to do the dirty work.

I guess what I meant to say earlier is that I think you may have a corrupted installation and that you should reinstall.
May be more of a hindrance than a help but that's my two cents worth.

Good luck!:cool:

-mac

---

### Post by herbster on 2008-05-01
See here: [http://sudan.ubuntuforums.com/showthread.php?t=759816](http://sudan.ubuntuforums.com/showthread.php?t=759816)

---

### Post by Jeff895 on 2008-05-01
> **herbster said:**
> See here: [http://sudan.ubuntuforums.com/showthread.php?t=759816](http://sudan.ubuntuforums.com/showthread.php?t=759816)

I'll have to reboot and check again but that doesn't seem to be the same error.  My error doesn't have the word install in it. 

I hope I don't come off as unappreciative but I am inexperienced and I came here as a last hope. Sending me links to other post that are familiar with code doesn't help me much. 

@Mac
I shut my pc off and turned it on with my copy of ubuntu 8.04 (which is an iso file on disc burned by decryptor) in my dvd drive.
I had kinda assumed it would boot from the disc but that didnt happen. Instead it went right into windows.

I also turned off the floppy drive by either hitting delete button or escape when the computer first turns on. I believe it took me into options.

---

### Post by Victormd on 2008-05-01
Ok, a few questions to try to help you...

1. when you partitioned, did you create a logic or extended partition? I've had problems with extended partitions.
2. did you format it using pqmagic or did you let the ubuntu install format it for you? If you want to use PQ Magic, use it to simply leave an unformated 30GB space.
3. did you create a swap partition for Ubuntu (~512Mb)? This is required
4. what type of install did you try? Using the live CD or alternate CD? The live CD is easiest but if it fails, you might want to try the alternate CD to install (text mode install)
5. what are some of your hardware components (i.e., graphics card)?

---

### Post by herbster on 2008-05-01
Jeff, you are not sounding unappreciative, but misunderstanding. In most cases, you're experiencing something that someone else has already encountered, and beginners more often than not do not search [efficiently], hence linking to a thread with a similar/exact same challenge. Did you actually read through the entire thread and attempt any of the solutions presented? Writing it off because of a tiny difference in the path, well, that won't do yourself much service.

---

### Post by Jeff895 on 2008-05-01
I guess I shouldn't worry about sounding unappreciative and more so about being impatient. I apologize, I have been trying to install linux for the past three days now. Its a little frustrating.

I will try to be as descriptive as possible:

My computer details are:

Intel Pentium 3 Processor 803 MHz
Motherboard: ASUSTeK Computer Inc. CUV4X REV 1.xx
Bios: Award Software Inc. Award Medallion Bios v6.0
Bus Type: PCI Bus
Ram: 576mb PC100
Video:Cirrus Logic 5446 Compatible Graphics Adaptor
Audio: Envy 24 Family Audio (WDM)
DVD: Pioneer DVR-111D

I have a 250 GB hard drive but was only able to use 127GB of it due to not initially installing Windows XP Pro with Service Pack 2. I installed service pack 2 and  relocated the missing 120GB by using Norton Partition Magic. 

Because I had the extra 120GB of space I partitioned the hard drive with Norton PM and created another hard disk named I:Linux. I then formatted it to NTFS. (this could be why I have an error, not sure. I still have 20GB free on my original hard drive listed as C:

these are the files on my ubuntu 8.04 disc
.disk
casper
dists
install
isolinux
pics
pool
preseed
autorun.inf
md5sum.txt
README.diskdefines
ubuntu
umenu.exe
wubi.exe

I ran wubi.exe and had the error.
I ran umenu.exe and had the error.

I then unistalled ubuntu again. I turned off my computer with my copy of Ubuntu 8.04 in my dvd drive. I expected Linux to boot up similiar to how windows does but no luck. Windows boots up.

When I try to install it again (using umenu.exe and wubi.exe) it then says it cant find the disc. Im sure Im being a complete noob and I will keep reading over the suggested link. If I can provide any more info I will be more than happy to.

---

### Post by ubnoobie on 2008-05-01
if you're installing using wubi, you don't need to partition the drive beforehand, just choose a drive in wubi with enough room for the desired ubuntu virtual disk size that leaves enough for your windows usage. wubi installs ubuntu using a virtual disk image stored on an existing windows partition (i.e. it's just a bunch of files and one very big one).

besides the thread link posted by herbster; see also, [_wubiguide: error 15_]("https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742") the raid part doesn't apply -- but considering your pc locked-up on a reboot and you had to cut the power, there may be filesystem errors. run a disk check in windows.

---

### Post by laffinet on 2008-05-01
> **Jeff895 said:**
> 
I ran wubi.exe and had the error.
I ran umenu.exe and had the error.


Which error did you get ? I'm a bit confused as to what exactly happened.

Did you initially install Ubuntu successfully ? You mentioned that on your first install the machine didn't shut down so you pulled the power plug. Is this correct ? What exactly did you do since then ? Please provide as much detail as possible

Have you tried booting into the live CD ? Have you set your computer to boot from CD-drive ? If so, what happens when you boot with the Ubuntu CD in the drive ?

---

### Post by warbread on 2008-05-02
> **Jeff895 said:**
> 

Because I had the extra 120GB of space I partitioned the hard drive with Norton PM and created another hard disk named I:Linux. I then formatted it to NTFS. (this could be why I have an error, not sure. I still have 20GB free on my original hard drive listed as C:



I'm not sure exactly how it works with a Wubi install.  Are supposed to be using an NTFS partition?  Normally, you want it to be EXT3.  There are other options, but EXT3 is the standard filesystem for Ubuntu.

---

### Post by Jeff895 on 2008-05-02
Thanks again for the attention.

Heres an update:

For the moment, I'm going to forget about wubi and only try to boot from live cd.

I did some searching around and saw a couple posts that mentioned they couldn't boot from drive. I restarted my computer and kept hitting esc. It gave me the option to finally boot from my dvd drive. I chose it.

Amazingly, I thought I finally had it.
The interface came up. I first chose to scan the disc for any errors. Came up clean.

I then chose English as my language and it seemed to be working. It then let me know that it set itself to a default low resolution. Which is fine.

Then I get this screen:

*Starting deferred execution scheduler atd   [ok]
*Starting periodic command scheduler crond   [ok]
*Checking battery state...                   [ok]
*Running local boot scripts (/etc/rc.local)  [ok]
_


I let it sit overnight to make sure I didn't tamper with the install. But I woke up to the same screen.

I am not partial to my hard drive labeled I:Linux. It was just an earlier attempt at making it work.

---

### Post by Jeff895 on 2008-05-02
Well, this past time of installing and reinstalling has created quite a problem for me. I seemed to messed it up for myself pretty good. Now when I start my computer it says error operating system not found.

My brother was telling me about this disc they used in school called boot magic that you would insert into your pc and it would save the day. All I find is norton and I dont really get how that would boot up from a disc.

For now, Ill just see if I can hook it up to another pc as a slave drive and hopefully backup from there. Although I backed up my media it never occurred to me to backup my photos. Live and Learn.

---

### Post by treggmo on 2008-05-02
Jeff895,
Don't delete that Windows disk yet. There are several posibilities for a fix. It could be a corrupted MBR or that your Windows partition is not marked as active(boot partition). Read this:

[http://support.microsoft.com/kb/321626](http://support.microsoft.com/kb/321626)

Bootable disks like ubcd4win or your Windows disk can help you correct this problem. Most PC Techs carry bootable disks and if you don't understand partitioning, a tech can recover your Windows system (if it wasn't deleted) and partition your disk in preparation for Ubuntu. They should't charge much. Call around.
I personally use the Alternate install CD after I have partitioned the disk and pre-formated to ext3 with a swap pertition also. I use gparted live cd to do this.
Don't give up. Get those photos back and get on with Ubuntu!
gparted can also re-mark your Windows partion as active.

---

### Post by Sef on 2008-05-02
> My brother was telling me about this disc they used in school called boot magic that you would insert into your pc and it would save the day. All I find is norton and I dont really get how that would boot up from a disc.

[Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") can install GRUB, the boot up manager.

> I partitioned my hard drive with Norton Partition Magic for 30 Gb free space and labeled it

Partition Magic and GNU/Linux tend not to get along.  Better to use [GParted]("http://gparted.sourceforge.net/").

---

### Post by redbob on 2008-05-02
Man, if you have a Live CD, you'll not need to slave your disc to another machine, coz Ubuntu Live Session will detect any USB device you could connect, since a Pendrive to even a HD Case. So you could back up your data files.

---

### Post by Jeff895 on 2008-05-03
Update: I borrowed a friends brand new 250 GB internal drive and installed my unlicensed XP Pro Sp2 on it. Hoping I could add my problematic drive as a slave and hopefully find my data on there. 

Instead it showed up as I:Linux 30GB. Obviously from when I had partitioned before. Its a shame the other 200GB didnt show up as I had hoped.


I was open to the UBCDWinv312 idea but read the instructions and it asked for a licensed copy of windows. Figures..Microsoft:(

I will call around to see if any techs can restore my drive.
I will leave the drive untouched for now.

I really thank you guys for all your help.
Have to admit i was starting to write off Linux.
But the encouragement here has convinced me I am missing
something without it.

---

