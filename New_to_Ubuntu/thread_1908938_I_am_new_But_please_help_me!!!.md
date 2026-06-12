---
title: "I am new But please help me!!!"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by jlsfagan on 2012-01-14
Hi I am new to this site and to linux. My name is Jess. I was looking for software to edit my videos on and came across Linux. I am interested in installing but I would like to have a look and play with it first to make sure. 
 
On to the issue:
 
I downloaded the image to my usb and then restarted my computer and followed the instructions I thought to a tee. Well if I had I would not be here anyways. I am currently downloading the image again. I want to see if it just did not download right the first time.
 
Well when my computer came up to boot I pressed F12 and then it promted me to press I think it was HDD usb I am not sure like I said I am retrying the whole process again.
 
Then after I selected this the first time it went to a black screen and would not load there was a mount error.
 
The next time I did it it worked and went to ubunto I rejoiced "it worked" and then I thought to soon becase it went to the black screen and promted me to press help if I had and issue so I did that the I got this error:
 
[ can not mount/dev/loop1 on/cow]

---

### Post by carl4926 on 2012-01-14
Why not use Unetbootin to create a bootable USB
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by flyfishingphil on 2012-01-14
Welcome ot Ubuntu.

First you say you downloaded the image. Did you download the entire Ubuntu file? For 11.10 it's 600+ MB in size. If you don't have the entire file you're getting as far as you can get.

Suggestion: Download the file and save it to a cd. With that you can now start your computer up with the cd in the slot and you will be given the option to start in Win or Ubuntu. This gives you a chance to play with a limited version to see if you like it.

Options include installing and using through Virtual Box, partitioning your hard drive and having both or doing a format and total install of Ubuntu. I did the partition for a few weeks, while I did research on what all was offered, and now run only Ubuntu.

Works faster and better, almost no threat from virus and trojans, nearly everything you need in programming is free and you have the forum where you can get help from people with some knowledge (like me) to experts that do programming for free.

Stick around and you'll probably get much better answers than I can provide.

flyfishingphil

---

### Post by jlsfagan on 2012-01-14
Yes, the file is 690+ so I do believe I downloaded the whole thing i am thinking about useing both windows and ubuntu but like I said still not sure of the system. I am trying the other usb file now to see if this works. 
 
I do not have a cd so usb is the best I can do for now.
 
I will tell you is the other Unetbootin works

---

### Post by grahammechanical on 2012-01-14
Hi and welcome to the forums. Be assured you will be helped even though you are new. We all were new at sometime and a lot of us are still new in some sense or other. You can learn from this experience and then you can help others.

Please look through this link. It may help you. Then again it may not help. Look at the second post and look for modesetting and the liveCD.

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

It may be that you need some video drivers that can only be installed after Ubuntu is installed. And we do that through a utility called Additional Drivers. So, the first thing is to get the liveCD/USB loading.

It is a USB memory stick and not a USB hard disk that you are trying to load from? You may need to change some settings in the computer BIOS to get booting from a live USB. I had to do this. I had to disable floppy drive access to make available some settings for using a USB memory stick.

I have just found this link which might be appropriate:

[http://www.ihaveapc.com/2011/02/how-to-fix-mint-boot-error-can-not-mount-devloop1-on-cow/]("http://www.ihaveapc.com/2011/02/how-to-fix-mint-boot-error-can-not-mount-devloop1-on-cow/")

It applies to the usb-creator program.

Regards.

---

### Post by WasMeHere on 2012-01-14
Hi Jess,

Please describe your situation in more detail, and the help will be more efficient.

0 - the usage: what do you do with your computer except editing videos?

1 - the computer: motherboard, processor, graphics, wireless lan (if any), RAM, hard disk drive(s)

2 - the system: do you want to keep the old operating system, how do you want to run Ubuntu?

Then we can discuss what version (date) and flavour (desktop environment) of Ubuntu that would be best for you. And we can suggest how to install it.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by layers on 2012-01-14
Hi Jess.

If you've run out of things to try, you might want to try using a CDROM method - I for instance have a SONY VAIO, and it really dosen't like booting up from USB's (it can't).

---

### Post by jlsfagan on 2012-01-14
- I use sketchup  so I would need to keep windows and other basic online usage nothing really major
 
- I want to keep windows vista home so I will not have any problems with sketchup

---

### Post by ajgreeny on 2012-01-14
A few points worth making.

flyfishingphil said "Suggestion: Download the file and save it to a cd."  

DO NOT DO THAT!  It will not help you, I'm afraid, as you do not want to simply save the .iso file you have to CD, nor to USB, as your comment in your original post suggests.

If you are using a CD you must **burn the .iso file as an image**, not just copy it, and if using a USB, I agree that **unetbootin** is the way to go.  I can't tell you how to use that in windows as I do not have windows on any of my machines, but I know that it can be used quite easily from windows to make a live USB.

---

### Post by jlsfagan on 2012-01-14
ok, So I rebooted and chose usb and it came up with an error and went into windows. I am going to use HDD now and see what happens. I this a good option or does it have to say usb?

---

### Post by WasMeHere on 2012-01-14
I suggest that when the booting works from the USB drive, you try to run ***only a live session*** also called 'Try Ubuntu without installing'. Do a lot of testing before you decide what to install and how to install it!

But you must get there. In some computers, a USB flash drive is recognized as a disk. Then you should (re)set the computer to boot from a hard drive, but change the boot order between the internal hard disk drive and the usb drive. You can try doing it after booting with the USB drive inserted and going into the BIOS menu system.

Maybe this is the same thing as you suggested:> I am going to use HDD now and see what happens

---

### Post by Basher101 on 2012-01-14
hi Jess,
if you still get errors with the usb boot, try making the live USB with the universal USB installer from [www.pendrivelinux.com](www.pendrivelinux.com) . i for myself have never had any problems making them with that program.
You should also check with md5sum to see if your .iso is okay (it could be corrupt if a few bytes are missing from the download) or download it again.

regards

---

### Post by jlsfagan on 2012-01-14
I used the HDD and it work it was kind of slow coming on at first but it worked now i just need to look at the system and see if I want to install or do the install where I keep both windows and ubuntu

---

### Post by WasMeHere on 2012-01-14
Great, now you have reached the next level :KS

So take your time to find out how Ubuntu works. If you have a fairly new and powerful computer, Ubuntu or Kubuntu or Ubuntu Studio of the newest version 11.10 (or possibly 11.04) might be good. If you have an older or weaker computer, Xubuntu or Lubuntu 11.10, 11.04 or 10.04 LTS might be the choice. Version 10.04 has long time support from April 2010 until April 2013 (3 years). The next LTS version will be 12.04 and it is scheduled to be supported for 5 years.

I use ***OpenShot*** to edit video files and ***ffmpeg*** to convert them into other formats, frame size and rate, video and audio quality and codec). These programs can be easily installed into any of the Ubuntu family versions and flavours, but they are already installed in Ubuntu Studio. There are also other (maybe more professional) programs to edit video files, that you can install, and they are free as most of the linux programs are.

---

### Post by flyfishingphil on 2012-01-14
> **ajgreeny said:**
> A few points worth making.

flyfishingphil said "Suggestion: Download the file and save it to a cd."  

DO NOT DO THAT!  It will not help you, I'm afraid, as you do not want to simply save the .iso file you have to CD, nor to USB, as your comment in your original post suggests.

If you are using a CD you must **burn the .iso file as an image**, not just copy it, and if using a USB, I agree that **unetbootin** is the way to go.  I can't tell you how to use that in windows as I do not have windows on any of my machines, but I know that it can be used quite easily from windows to make a live USB.

ajgreeny. Thanks for noting my typo error where I said "save to" instead of "burn to". Glad you caught it.

ffp

---

### Post by jlsfagan on 2012-01-14
I have an older computer toshiba in the screen from my usb it has a button for installing 11.10 is that not a goo option?

---

### Post by MG&amp;TL on 2012-01-14
> **jlsfagan said:**
> I have an older computer toshiba in the screen from my usb it has a button for installing 11.10 is that not a goo option?


You can try, and then install, or just install straight away.

Either's fine, but I recommend 'trying' first to make sure it's working.

---

### Post by WasMeHere on 2012-01-14
Test the system, how fast some typical programs work, for example editing, browsing, looking at pictures, playing video and music! Check also how much of your RAM is used and how hard your cpu(s) must work!
'System Monitor' or in the command line terminal (ctrl + alt + t):
```
gnome-system-monitor
```
Finally, how much is left of your hard disk drive, and how is it partitioned?
Please post the result of the following command
```
sudo fdisk -lu
```
All this information will help deciding what to install and how to install it. Maybe the right thing is to install standard or 'vanilla' Ubuntu 11.10, but you might find something better for your particular computer and needs, if you make a little extra effort now.

---

### Post by jlsfagan on 2012-01-14
I did those codes what am I looking for? I am still in my usb version.

---

### Post by jlsfagan on 2012-01-14
I was trying to play game just to see how they work. Can you play game with a usb version?

---

### Post by MG&amp;TL on 2012-01-14
> **jlsfagan said:**
> I was trying to play game just to see how they work. Can you play game with a usb version?

Sure. What game? One of the built-in ones?

---

### Post by jlsfagan on 2012-01-14
yes, and I just downloaded one to see how long it takes and how it plays but when I click it all I get is a screen shot

---

### Post by MG&amp;TL on 2012-01-14
> **jlsfagan said:**
> yes, and I just downloaded one to see how long it takes and how it plays but when I click it all I get is a screen shot

Can you be a bit more specific?

What game? From where?

If you got it from the software centre, you need to click 'install' first. :)

---

### Post by jlsfagan on 2012-01-14
Yes, I got it from the software center billiard gl just picked something... I did the install but do not know how to really make it play

---

### Post by WasMeHere on 2012-01-14
> **jlsfagan said:**
> I did those codes what am I looking for? I am still in my usb version.

Test the system, how fast some typical programs work, for example editing, browsing, looking at pictures, playing video and music! Check also how much of your [COLOR="Red"]RAM[/COLOR] is used and how hard your [COLOR="Red"]cpu[/COLOR](s) must work!
'System Monitor' or in the command line terminal (ctrl + alt + t):
```
gnome-system-monitor
```
Finally, [COLOR="Red"]how much is left of your hard disk drive[/COLOR], and how is it [COLOR="Red"]partitioned[/COLOR]?
Please post the result of the following command
```
sudo fdisk -lu
```
All this information will [COLOR="Red"]help deciding what to install[/COLOR] and how to install it. Maybe the right thing is to install standard or 'vanilla' Ubuntu 11.10, but you might find something better for your particular computer and needs, if you make a little extra effort now.

It is OK, you can run these commands from your live system. And wired internet works (almost always) out of the box in live systems.

What graphics card or chip do you have? intel, nvidia, ati ? Some cards may make it difficult to get good graphics. Sometimes the standard built-in video driver works. Sometimes a built-in proprietary driver can be installed. Sometimes a proprietary driver needs to be downloaded and installed, which is tricky. The built-in options can be tested on the live system.

---

### Post by mastablasta on 2012-01-14
usb version loads all into RAM (which is the reaosn why it need longer to boot). it doesn't touch the disk. so when you turn it off everything you downloaded and installed would be lost.

small games work fine in live UBS mode. all should work even better when installed. the important things to try out if they work are -wireless (if you have one), sound, graphics you can't really try unless you can install proprietary drivers, then maybe some special keys if you have a notebook.and that's about it.

assuming you are suing the latest version with Unity interface look here for some help: [https://help.ubuntu.com/11.10/ubuntu-help/index.html](https://help.ubuntu.com/11.10/ubuntu-help/index.html)

if you use the long term support version then look at my signature for a nice user guide.

edit: A HINT - the commands they gave you - you can copy paste them into terminal (no need to type them ;-) ) and you can then copy the results form commands from terminal and paste them here. that's what they would liek you to do.

---

### Post by jlsfagan on 2012-01-14
ok here is the second code info

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   234440703   115683328    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         129     3907007     1953439+   6  FAT16

---

### Post by jlsfagan on 2012-01-14
I want to keep windows and I want to in stall ubuntu what is the best way to do this? I dont want any problems

---

### Post by jlsfagan on 2012-01-14
I do have an old computer so i am not sure which one but I have intel

---

### Post by jlsfagan on 2012-01-14
I found it :\
Genuine Intel® CPU T2080 @ 1.73GHz × 2

---

### Post by carl4926 on 2012-01-14
> **jlsfagan said:**
> ok here is the second code info

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   234440703   115683328    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2000 MB, 2000748032 bytes
64 heads, 63 sectors/track, 969 cylinders, total 3907711 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         129     3907007     1953439+   6  FAT16

You need to establish how much free space there is in windows
Windows is sda2 and ultimately you will have to use GParted to shrink sda2 if there is enough free space to do so safely. And windows should be defragemented before hand too.

I'm worried you don't really understand this though

---

### Post by jlsfagan on 2012-01-14
> **carl4926 said:**
> You need to establish how much free space there is in windows
Windows is sda2 and ultimately you will have to use GParted to shrink sda2 if there is enough free space to do so safely. And windows should be defragemented before hand too.

I'm worried you don't really understand this though
I believe I have around 30g left

---

### Post by jlsfagan on 2012-01-14
> **jlsfagan said:**
> I believe I have around 30g left
I understand but I still need windows at least for now

---

### Post by Zill on 2012-01-14
> **jlsfagan said:**
> I want to keep windows and I want to in stall ubuntu what is the best way to do this? I dont want any problems
A quick suggestion before you install *anything*...

**BACKUP ALL YOUR EXISTING DATA TO EXTERNAL MEDIA**

If you install Ubuntu correctly then your data *should* still be intact afterwards.  However, mistakes can (and do!) happen and so you should *always* have good backups to restore from if the worst comes to the worst.

Good luck.

---

### Post by carl4926 on 2012-01-14
> **jlsfagan said:**
> I believe I have around 30g left

Defrag windows

Shrink sda2 in half, no more. Should give you 15GB
Create a extended partition in that total free space and then a 1GB swap logical and 14 GB ext logical
Install Ubuntu and use custom partitioner to select those partitions

---

### Post by jlsfagan on 2012-01-14
> **carl4926 said:**
> Defrag windows

Shrink sda2 in half, no more. Should give you 15GB
Create a extended partition in that total free space and then a 1GB swap logical and 14 GB ext logical
Install Ubuntu and use custom partitioner to select those partitions
I hate to sound stupid but...

Do What?

---

### Post by jlsfagan on 2012-01-14
I can defrag I lost you after that...

---

### Post by carl4926 on 2012-01-14
This is just to give you an idea, it's not exactly what I suggested.
[http://dl.dropbox.com/u/10573557/Partitioning%20example%20win7-linux.mpeg](http://dl.dropbox.com/u/10573557/Partitioning%20example%20win7-linux.mpeg)

Right now I have to go sleep
Back in 7hrs and I can walk you through it, if you didn't already get it sorted.

---

### Post by MG&amp;TL on 2012-01-14
Maybe I'm being stupid, but is there a reason why the OP should not use the user-friendly partitioner provided by ubuntu?

---

### Post by WasMeHere on 2012-01-14
Hi again Jess,

> **carl4926 said:**
> Defrag windows

Shrink sda2 in half, no more. Should give you 15GB
Create a extended partition in that total free space and then a 1GB swap logical and 14 GB ext logical
Install Ubuntu and use custom partitioner to select those partitions
I support the suggestions by ***carl4926*** and ***Zill***.

0. If possible, clean your Windows system by deleting what is not necessary (see * below)!

1. So tonight you start to [COLOR="Red"]defragment[/COLOR] the windows partition. It takes several hours unless you did it recently.

2. Then [COLOR="Red"]backup[/COLOR] everything you need. A complete image of your disk is the best, but it might be OK to backup all your personal data (documents, mail files, pictures, private videos etc). This may also take hours depending on how much data you backup and how fast (with or without compresssion ...).

3. Now it is time to [COLOR="Red"]edit the partitions[/COLOR] on your hard disk drive. I suggest that you run from the USB live system with Ubuntu and use gparted (it is there already).

a. [COLOR="Red"]Shrink the Windows partition[/COLOR] **/dev/sda2** so that approximately half of the free space can be dedicated to Ubuntu. So if 30 GB are available, shrink /dev/sda2 by 15 GB, leaving 15 GB unallocated. This operation also takes several hours.

b. Make an [COLOR="Red"]extended partition[/COLOR] that fills the unallocated space (approx. 15 GB)

c. Make a logical partition formatted as [COLOR="Red"]swap area[/COLOR] of at least the size of your RAM (for example 2GB) at the end of the extended partition.

d. Make an ext3 (or ext4) partition filling the rest of the extended partition (in the example approx. 13 GB). This should be mounted by Ubuntu as the the root partition /

It is not very big, but it works. Ubuntu plus a few extra program packages is less than 5 GB, so there is plenty of space for personal files within approx. 13 GB.
---
*. And of course: If you can [COLOR="Red"]clean your Windows system[/COLOR] by deleting temporary files, obsolete programs and documents, cleaning the trash-can etc, you might have 40 GB free, leaving 20 GB for Ubuntu (2 GB swap and 18 GB for the system and personal files).
---
You must press the [COLOR="SeaGreen"]tick sign[/COLOR] in order to perform the changes on the hard disk drive.

[COLOR="Red"]After that you can install Ubuntu[/COLOR]. Use the 'advanced manual method' to select partitions (the whole ext3 partition should be used as /).

But as I wrote before: I strongly recommend that you [COLOR="RoyalBlue"]download and try some other version and/or flavour of Ubuntu[/COLOR] and test it before you settle for the default version (newest vanilla Ubuntu).

Have fun finding out about Ubuntu and good luck :-)
Olle

---

### Post by mastablasta on 2012-01-16
ok first thing it's better to use widnows disk manager to shrink a partition. gparted available on live linux media though a great tool has been knwon to cause problems occasionally with windows parittions.
 
and secondly why are you people keep trying to confuse new users with partitioning, file types etc?!?
 
no seriously.... this is ABSOLUTE BEGINNER TALK!!! 
 
Ubuntu can and will make the needed partitions automaticly. for someone that wants to give it a try they can do so with suggested settings in installer. aslo file type why ext3? google said they will be moving all their data on ext4 if they haven't already. and i believe ext4 is the default. if there is something horribly wrong with it then why would it be a default option? 
 
to you Jess - just keep it simple. create an empty disk space by creating a non formatted partition. then just install next to windows and follow the prompts. it couldn't be simpler. no need to worry abotu swap, home boot whatever partition. why because the necessary partitions are done automaticly and because you can always add more later IF you really need them.
 
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

