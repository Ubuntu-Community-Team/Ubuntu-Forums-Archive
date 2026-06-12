---
title: "Help with ubuntu/ windows xp"
date: 2007-06-08
forum: Other OS Talk
---

### Post by lankan526 on 2007-06-08
i used to have win xp installed on my acer aspire 5100 laptop. it was configured for that model and everything. then i installed ubuntu. it was working fine with dual booting. then im not sure why but i deleted my entire hdd. then when i tried installed win xp again, in the middle of the installation it turns off by itself. i think something with the booting is corrupted. im not sure. but then i put in the ubuntu cd and it works fine. i think it works because it doesnt boot from cd. it boots after it gives you that live thing. i want to know how to put xp on there again or to delete all the files and everything from the hdd. not reformat. like clean it straight!


PLEASE HELP

---

### Post by raja on 2007-06-08
> **lankan526 said:**
> i used to have win xp installed on my acer aspire 5100 laptop. it was configured for that model and everything. then i installed ubuntu. it was working fine with dual booting. then im not sure why but i deleted my entire hdd.
Deleted means ? - formatted it?

> 
 then when i tried installed win xp again, in the middle of the installation it turns off by itself.

Is this a restore cd or are you trying to install from an XP disc?

> 
i want to know how to put xp on there again or to delete all the files and everything from the hdd. not reformat. like clean it straight!

You dont want to reformat ?

---

### Post by smoker on 2007-06-09
> **lankan526 said:**
> .. .then when i tried installed win xp again, in the middle of the installation it turns off by itself. i think something with the booting is corrupted.

if it is an xp disk, as opposed to a recovery disk, then look at this link for reinstalling xp:
[http://www.windowsxphome.windowsreinstall.com/sp2installxpcdnewhdd/indexfullpage.htm](http://www.windowsxphome.windowsreinstall.com/sp2installxpcdnewhdd/indexfullpage.htm)
if you run into problems, check the disk in another computer in case it is damaged.

>  i want to know how to put xp on there again or to delete all the files and everything from the hdd. not reformat. like clean it straight!

installing xp involves reformatting your drive, it has to be reformatted in a file system xp can use, ie, fat, or ntfs. this format will delete all your files.

best of luck

---

### Post by lankan526 on 2007-06-09
> **raja said:**
> Deleted means ? - formatted it?

yes


> **raja said:**
> Is this a restore cd or are you trying to install from an XP disc?

I tried restore cd and xp disk


> **raja said:**
> You dont want to reformat ?

i want to reformat but i want everything gone. even the startup company logo that says acer.

---

### Post by lankan526 on 2007-06-09
> **smoker said:**
> if it is an xp disk, as opposed to a recovery disk, then look at this link for reinstalling xp:
[http://www.windowsxphome.windowsreinstall.com/sp2installxpcdnewhdd/indexfullpage.htm](http://www.windowsxphome.windowsreinstall.com/sp2installxpcdnewhdd/indexfullpage.htm)
if you run into problems, check the disk in another computer in case it is damaged.

thx for the site. will try. the disk works fine on my other two computers. and it works fine on my laptop too. just that it restarts for no reason.



> **smoker said:**
> installing xp involves reformatting your drive, it has to be reformatted in a file system xp can use, ie, fat, or ntfs. this format will delete all your files.

best of luck

yea...sorry that i talked like i didnt know what reformatting is. i know how to do it and how it works, just that i want it so that even the company logo that says acer when booting my laptop doesnt show!  i think if i do this then the hdd wont restart on me when installing xp.


thx!

---

### Post by lankan526 on 2007-06-09
one more thing i want to make clear. i've reinstalled xp billions of times on many computers. so the site you gave me smoker isnt really helpfull. but thx anyway....

---

### Post by raja on 2007-06-09
I am still trying to understand the problem. 
So are you saying that you have a fully formatted empty drive and are not able to install XP using either the rescue disc or an xp installation disc, but can boot with the Ubuntu live cd and get to a desktop?
If that is so, at what stage is the xp installation failing. Does it not boot at all, or does it have a problem formatting or is the problem later on.

---

### Post by d3v1us on 2007-06-11
you should be able to turn off the company logo in the BIOS... I don't see how it's related to your hard drive though.

---

### Post by minhhoang on 2007-06-12
Sorry to steal the thread, but since I have a similar problem I don't want to waste another the thread.

Here is my situation.

My laptop came with windows XP. After that I manually re-partition the hardrive to create 2 new partitions,  1 to install Ubutun, 1 used as swap. I've got Ubuntu 6.10 running on dual-booting with XP for a while, but after playing around with the video driver (ATI) it screw up my Ubuntu. 

Then I decided to delete the ubuntu and swap partition from XP (using Partition Magic) without backing up all my data of course :-( . Since then, i could not start XP, as it always give me **GRUB error 15** when i try to boot the system. 

I've done some research and found out that I need to reinstall the Windows MBR. So I tried boot it win an installation disk of XP, however when I tried to start of Recovery Console, it said that it could not detect any hard drive hence could not start.I also tried ERP (Winternal boot disk) but also could not see my hard drive.  

I'm sure the HD is well connected as I can test it from BIOS. However there's some reason the boot disks can not see it.

 Any idea why is that ? and how to get my xp back please ? Thank you all.

---

### Post by wayno on 2007-06-12
yeah mine did that too, the XP install said that it couldnt find a hard drive

---

### Post by minhhoang on 2007-06-13
Does anyone know how to solve this yet ? Thanks

---

### Post by beast2k on 2007-06-13
> **minhhoang said:**
> Does anyone know how to solve this yet ? Thanks

I use a windows 98 (yes windows98) floppy disk , the one you used to use to install the operating system. When you get to the prompt type     "fdisk /mbr" (it's been a while so try the command with the / and without it) &      without the quotes. Don't worry about windows xp not seeing a harddisk. If you dont have a win98 bootdisk get one here [http://www.bootdisk.com/](http://www.bootdisk.com/) let me know how it works out.

---

### Post by minhhoang on 2007-06-14
Thanks Beast. I'm at work atm so I will try it tonight, I'll let you know how it goes.

---

### Post by johnny4north on 2007-06-14
if you completely wiped your drive.  i believe your acer has a small hidden partition - that the power management needs to access, but now lock up your system when not found.  correct me if wrong.  go into your bios <f2> tempary disable the power management. save and exit.  be careful in there.  run the recovery dvd, then reboot.  install xp, then ubuntu.  here is a fourm post w/ tons of info on the hidden partition - [http://forum.notebookreview.com/archive/index.php?t-11476.html](http://forum.notebookreview.com/archive/index.php?t-11476.html)

---

### Post by smoker on 2007-06-14
> **minhhoang said:**
> 
Then I decided to delete the ubuntu and swap partition from XP (using Partition Magic) without backing up all my data of course :-( . Since then, i could not start XP, as it always give me **GRUB error 15** when i try to boot the system. 

I've done some research and found out that I need to reinstall the Windows MBR. So I tried boot it win an installation disk of XP, however when I tried to start of Recovery Console, it said that it could not detect any hard drive hence could not start.I also tried ERP (Winternal boot disk) but also could not see my hard drive.  


hi, i'm not sure what you mean by 'delete the ubuntu and swap partition from XP...', they should be completely separate partitions not connected in any way with an XP partition. in using the recovery console, it should automatically detect  your XP installation, unless of course, it isn't there! could you have formatted over your XP partition?

i think i would download and burn a copy of the 'gparted live-cd' and boot from that, and that will show you exactly what partitions you have, what format they are, and what proportion of each partition is used. if your XP partition is still there, and has data on it comparable with an install of XP, then you can delete any other partitions if applicable, resize you XP partition, and try running the recovery console again. if you have deleted your XP install, then i think you will have to reinstall it. you can download the 'gparted live-cd' from here: [http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

best of luck:D

---

### Post by minhhoang on 2007-06-14
I deleted Ubuntu/Swap partition from XP using partition magic. I'm sure the XP partition is there, I can see it by booting from the Ubuntu Live CD. My hard disk however is a SATA one.

I've just try boot from win98 , got to DOS , tried fdisk /mbr then restart, still the same problem :-(

I'm thinking of put Ubuntu on the same partition again.

---

### Post by smoker on 2007-06-14
> **minhhoang said:**
> I deleted Ubuntu/Swap partition from XP using partition magic. I'm sure the XP partition is there, I can see it by booting from the Ubuntu Live CD.** My hard disk however is a SATA one.**


if you have a sata drive you may have to reinstall the sata drivers before xp will recognize the hard drive, you press F6 shortly after xp setup starts (before recovery console option), and install the sata driver. you should have this driver on your motherboard disc normally, or if you received a driver disk with your pc. if not, you will have to download the correct driver from the motherboard website. you normally load the driver via a floppy, but if your pc doesn't have one, look for directions to load from a usb, or cd,

---

### Post by beast2k on 2007-06-14
> **minhhoang said:**
> I deleted Ubuntu/Swap partition from XP using partition magic. I'm sure the XP partition is there, I can see it by booting from the Ubuntu Live CD. My hard disk however is a SATA one.

I've just try boot from win98 , got to DOS , tried fdisk /mbr then restart, still the same problem :-(

I'm thinking of put Ubuntu on the same partition again.

That is odd that command should have restored your master boot record of xp and after a reboot should have put you back to booting into xp. All I can suggest at this point is to backup your data from xp using the ubuntu cd (if you can see and access the data) and reinstall first windows (if you still want it) then ubuntu. If that all fails and reinstall fails then I would be leaning toward a hardware related problem.

---

### Post by smoker on 2007-06-14
> I've just try boot from win98 , got to DOS , tried fdisk /mbr then restart, still the same problem

a win98 boot disk wont work if the xp install is on an ntfs partition

---

### Post by minhhoang on 2007-06-14
Thanks all for your help. Problem solved. :)

For anyone that have the same problem as mine, just get yourself a copy of Hiren's BootCD (version 8.9 for me or any of them that has MBR tools) Boot from Hiren then Select MBR tools -> MBR Works -> Option 5 . Then restart. You should see your XP back.

 (there might be other that also works but that the first one i tried and it works)

---

### Post by smoker on 2007-06-15
glad you got it sorted:-)

and thanks for posting what the fix was,

cheers

---

### Post by lankan526 on 2007-06-24
Hey...my problems still not solved :(

let me make myself clear: when using Partion MAGIC (a partioning tool used when you restart the computer with the cd in the drive) i cannot partion a disk. well, i can but when the partioning is happening it automatically shuts off. when installing xp, when it starts copying the files, or something like that, it shuts off again. im not sure if it is my hdd problem, but ubuntu is working fine. i used Virtual Box in ubuntu to get winxp running and it worked. so i think that thers  some problem with my hdd that when i try reformating, partioning, or installing something in bios mode, it will block me, but in an alternate way, it works....if that makes sense...


please help me!!!!

---

### Post by smoker on 2007-06-24
did you install the sata drivers for xp?

---

### Post by lankan526 on 2007-06-25
im not sure how to do that, but my hdd is IDE...

---

### Post by lintoon on 2007-06-29
Maybe your MBR is screwed or you have a faulty hd.  I would try low level formatting the drive before installing windows.  Or you could try booting to the dos prompt and running fdisk, delete the hd partitions and recreate them.  Also try "fdisk /mbr" at the dos prompt. 

You may need to download a windows boot floppy in order to do this.

---

