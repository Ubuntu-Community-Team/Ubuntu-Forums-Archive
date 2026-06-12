---
title: "[SOLVED] Completely new system - am I missing drivers?"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by gshockxc on 2008-11-25
I've just finished my build of a completely new system from scratch.  I'm running an AMD Athlon X2 2.1 GHz processor on an ASRock A780 Full Display port.  I think the first problem was that I accidentally downloaded the 32-bit .iso version of 8.10.  That gave me a boot CD error.  

I had an 64-bit version of Fiesty (7.04) that I tried to install, but that didn't seem to work either.  It would give me the Ubuntu start up menu, and when I selected install, it would keep trying to read the floppy, and then give me a tty error, job control turned off.  I tried to use the help function for tty, but I couldn't figure out what tty is.   

So I picked up the mobo install manual and there was some information pertaining to SATA-II and setting that up in the BIOS.  There was some reference to RAID, but I have no idea what it is or how it works, or if I even need to worry about it once I get the right version of Ubuntu burned to an .iso image.  I was reading in the mobo manual that I need to follow some special procedures if I have a SATA-II HDD, but it seems to only apply to Windows.  

So I booted from the mobo mfr's CD to install some of the drivers, just guessing at what might work.  It seemed to install something.  So I tried to boot the 7.04 version that I had.  

Then I got an I/O error, fd0 device not found.

I have several questions (that I know of, and probably more I haven't figured out how to frame yet).  

First, if I'm building a completely new system from scratch, and everything is new hardware, do I need to install any particular drivers just to be able to boot the OS, or get to install mode?

Second, what's a RAID?

Third, what does that have to do with SATA-II?

Fourth, do I need to worry about making any changes to RAID or SATA-II settings in the BIOS before installing an OS?

Finally, I'm not going to have a temper-tantrum because this takes some time and effort to get up and running.  For me, I am planning on this taking some time.  It's my intent to learn.  So the more problems I have, the more I learn about how to run Linux (Ubuntu).

Thanks for your help.
-gshockxc

---

### Post by jimreynold2nd on 2008-11-25
1) As far as I know, necessary drivers are included in the Ubuntu CD. If missing, they can only be installed after you install Ubuntu (think about it, without an OS, where should the drivers go?). It's weird tho, coz with your configuration everything should works right out of the box... **Try disabling the FDD controller in BIOS setup to see if that helps you boot from the Ubuntu CD** (who uses floppy disk this day...).
Actually, either 32bit or 64bit works fine on a 64bit system. Btw, you should either download Hardy (8.04) or Intrepid (8.10) instead of Gusty.

2) Basically, RAID is a way of organizing multiple HDD's into a single volume (partition). RAID0 is a way of merging/slicing 2 HDD's into one partition, giving a boost in speed (think of dual-channel HDD). RAID1 is clone, it gives no boost in performance but it ensure your data always have a copy in case one of the drives fail. RAID5 typically involves 5 HDDs and it's basically a combination of RAID0 and 1 with more advance backup techniques that uses less space but ensure same level of redundancy.

3) No, this has nothing to do with SATA2. With XP, you normally need a separate driver to install on a SATA2 machine or you have to temporarily disable the SATA controller (have it run in legacy mode) during installation. With ubuntu you don't have to.

4) No AFAIK with Ubuntu

EDIT: seems like you have a lil rough path. Normally people would be able to boot straight from the live CD. Anyway, good luck!

---

### Post by handydan918 on 2008-11-25
The 32 bit .iso should not have caused you a problem. I use 32 bit on my amd64 bit system. No problems.

I would do a little digging and make sure that 
1) your download is good. Check the md5 sum.

2)Use only good quality cd's to burn the .iso image to. Generally, the burn speed should be about as low as the burner will support.

3) Review your bios documentation and make sure you are not overlooking something in the boot order. 

You aren't trying to boot the cd off of a sata cdrom drive, are you?
That sometimes causes issues....

---

### Post by stalkingwolf on 2008-11-25
RAID = Redundant array of Inline Drives.  as I recall.  Used primarily for
making several identical backups of your system to prevent data loss and downtime.  If one drive fails system changes to another as I recall.

fd0 error,  probably because you dont have a floppy drive installed.
I usually get this on laptops where the floppy and Cd are swappable
or external if both are not plugged in.  I have cured it by plugging in a usb floppy drive.

---

### Post by gshockxc on 2008-11-25
> **handydan918 said:**
> You aren't trying to boot the cd off of a sata cdrom drive, are you?
That sometimes causes issues....

This is EXACTLY what I'm doing.  I have two SATA-II LG DVD/CD drives.  

Do you know of any work arounds?  I can borrow a drive from my other system.  I don't know what you call it when it's not SATA-II.

---

### Post by gshockxc on 2008-11-25
> **stalkingwolf said:**
> RAID = Redundant array of Inline Drives.  as I recall.

Perfect.  That makes sense.  Since I don't have any, I want the non-RAID option in the BIOS.  There's an AHCI option, but I tried that and it didn't work, it just kept cycling through the startup sequence, and wouldn't boot from the CD.

> **stalkingwolf said:**
> 
fd0 error,  probably because you dont have a floppy drive installed.

Actually, I do have a floppy installed.  It's just not reading it, or so it seems.  I am pretty sure that I got the Pin1 locations correct.  It only fits one way in the mobo, and I tried flipping the ribbon cable on the drive, and it didn't seem to help.

I went into the boot sequence and set the CD as the primary boot order, then the HDD next, and finally the floppy.

The Ubuntu CD loads, and I select install, then the status bar comes up, the light on the floppy comes on, it churns in repeated pauses, then the Ubuntu display turns a funny pink color for a second, and I get the fd0 error.

Thanks for the suggestions.  Keep 'em coming, if you can.

---

### Post by gshockxc on 2008-11-25
I was searching some other posts, and someone mentioned checking the jumper settings.  I was reading the mobo manual, and it didn't mention much about jumper settings for the CD/DVD drives or the HDD.  What jumper settings should I check?

On the back of the [LG CD/DVD drives]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827136152"), there are 8-pins, no jumpers.  Should there be?

What about the HDD?  I didn't see anything in the documentation, but I could have missed something.

Thanks

---

### Post by bumanie on 2008-11-25
SATA drives don't have jumpers, the thread you read would have been talking about (the older) IDE drives. Running a 32bit OS on 64bit architecture won't cause problems that you describe - in fact it will run perfectly well. Also the majority of drivers are included in the kernel. Looks as though you have some idiosynchratic issue. I would try the alternate installation cd which is a text-based installer, it often installs witout problems when the live cd won't. Theoretically, all drivers should be installed during the OS installation. Try the alternate cd and post back if there are any problems post installation.

---

### Post by gshockxc on 2008-11-25
> **bumanie said:**
> SATA drives don't have jumpers, the thread you read would have been talking about (the older) IDE drives.

Thanks for the clarification.  Perhaps it was the floppy I was thinking of?  

> **bumanie said:**
> Try the alternate cd and post back if there are any problems post installation.

I tried to install in text mode for 7.04 (AMD64), and I also tried the 7.04 (alternate).  In the alternate installation, it kept asking me for the driver for the floppy.  I had no idea what to select so I tried the generic, floppy, ide-generic, etc.

Based on that, and the other hang-ups I mentioned, I figured that it wasn't recognizing the floppy.  But I still can't figure out why, or why it's trying to access it during the install.

I suppose that 8.10 has drivers that 7.04 doesn't.  Since the floppy is new, maybe the driver's not in the list.  Should I try unplugging it and installing without it for now?

Thanks for your help.

---

### Post by CatKiller on 2008-11-25
If you have a peculiar drive setup, it can sometimes be necessary to have a driver for the hard drives before an OS can install. It's sometimes the case for a RAID setup, and it used to be the case for SCSI devices. I don't know if it's still an issue for SCSI devices, or if they just aren't popular enough to mention any more. I also don't know if this is necessary for SATA drives.

This driver would normally be on a floppy disk, in a way that an OS installer could read and use to set up the hard drives.

Perhaps you have selected that you need a driver for those drives, and so it is looking for the driver on the floppy drive, and since it's not there, it's throwing up an error?

I understand that with most motherboards you can tell the BIOS to pretend that SATA drives are IDE drives, to make OS installations easier. This would probably be called a "Legacy mode", or something similar. Doing this might cause problems if you are also using a number of real IDE devices, since you can only have a maximum of 4 IDE devices on one controller, but should be fine otherwise.

As far as I know, floppy drives haven't changed their interfaces in quite some time.

EDIT: 8.04 would probably be a better thing to install, since it's a Long Term Support release. 7.04 wasn't, and is quite old now. There have been quite a few improvements in the intervening time. 8.10 is not an LTS release, but it is the newest release. I've not had any problems with it, but a lot of users have chosen to stick with 8.04, at least for the time being.

---

### Post by gshockxc on 2008-11-25
> **CatKiller said:**
> This driver would normally be on a floppy disk, in a way that an OS installer could read and use to set up the hard drives.

My suspicion as well, but since I know so little about linux, and what might or might not happen, I didn't want to presume.  If that was the case, I wasn't sure how to resolve it.  

> **CatKiller said:**
> Perhaps you have selected that you need a driver for those drives, and so it is looking for the driver on the floppy drive, and since it's not there, it's throwing up an error?

That's very possible.  I guess my next question would be, how/where do I look to disable this so that the install isn't looking for the driver?

> **CatKiller said:**
> I understand that with most motherboards you can tell the BIOS to pretend that SATA drives are IDE drives, to make OS installations easier. This would probably be called a "Legacy mode", or something similar. Doing this might cause problems if you are also using a number of real IDE devices, since you can only have a maximum of 4 IDE devices on one controller, but should be fine otherwise.

I'm not sure if I did this when I was playing around with the bios.  I know that the SATA settings were set to "non-RAID" at first.  Maybe I missed something in the setup.  I'll try again tonight.  All of the devices (CD/DVD's and floppy) are SATA.  To my inexperienced mind, I don't have any IDE devices except the HDD.

> **CatKiller said:**
>  8.04 would probably be a better thing to install, since it's a Long Term Support release. 7.04 wasn't, and is quite old now.

I downloaded the Alternate and the 64-bit versions of both 8.04, and 8.10.  I'll take your suggestion and do the 8.04 version first.

Thanks a lot for your help.  Lots of info is always a good thing.

:)

---

### Post by CatKiller on 2008-11-25
> **gshockxc said:**
> That's very possible.  I guess my next question would be, how/where do I look to disable this so that the install isn't looking for the driver?

I installed 8.04 on my other half's computer, and that had a SATA drive. It didn't ask for any drivers or anything like that. So you might just find that it isn't an issue when you try 8.04.

On 7.10 (I don't have a 7.04 cd handy) you can set boot options appropriate for the drive (F1 calls up the help file that will tell you about it). You can also install with a driver cd (rather than a floppy) as one of the options on the menu, but since I don't have a driver disc that I need to use, I can't really test it for you.

---

### Post by gshockxc on 2008-11-26
Downloaded Hardy yesterday, installed last night.  Worked like a charm.  Not a single hiccup, issue, or other abnormality.  It worked great!  

I'm kind of bummed, now.  I thought it was going to be tougher than that.  It's almost too easy.  ;)

Thanks to everyone for all of your help.

---

### Post by tardeevo on 2008-12-08
since you now got my same configuration - same mobo and hardy64 - have you already tried to use usb 2.0 (i.e. external hd or fast devices like this)? I tellya because I'm experiencing big issues there...

---

### Post by gshockxc on 2008-12-08
> **tardeevo said:**
> since you now got my same configuration - same mobo and hardy64 - have you already tried to use usb 2.0 (i.e. external hd or fast devices like this)? I tellya because I'm experiencing big issues there...

No, actually, no issues at all with the USB 2.0 interfaces.  I was expecting that I might, but not so far.  

What issues are you seeing?

---

