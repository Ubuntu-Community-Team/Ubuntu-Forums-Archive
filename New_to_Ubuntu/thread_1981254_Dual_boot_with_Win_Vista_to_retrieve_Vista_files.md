---
title: "Dual boot with Win Vista to retrieve Vista files?"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by frizzlefrazzle on 2012-05-16
**A little background info (ignore?)**
My Vista laptop got a blue screen of death (I didn't even know they still made that) the other night. In the last few days, I installed one program, did about 3 months worth of "updates" and updated Adobe. Then, boom. Crash, right after connecting to a public wifi spot. I didn't pay much attention to the long blue screen of death error, but it said something about "if this is the first time...and something about new installs".
 
**Windows Vista error when booting up:**
Intel UNDI , PXE-2.1 (build 082)
Copyright (C) 1997-2000 Intel Corporation
 
For Atheros PCIE Ethernet Controller v2.0.0.9(05/08/09)
 
Check cable connection!
PXE-M0F: Exiting Intel PXE ROM.
No bootable device -- insert boot disk and press any key.
 
**Bad MBR (possible diagnosis)?**
I'm probably just dangerous enough to do some real damage, and am fairly worthless in linux. But, I'm pigheaded and don't want to take this thing to a "geek." I should be geek enough.
 
**Possible Useful Info**
So, my first thought after rebooting a few times, realizing I never made back/recovery discs (as suggested by the manufacturer - Acer), was "no problem."
 
A few years ago, I loaded a USB thumbdrive with Ubuntu 8.10. I used that once before to help a friend get files off their computer (booting into Ubuntu and seeing their hard drive to snag some files). So, I figured I'd do the same with my laptop, then, since I do have the Win 7 upgrade discs, I'd just install/update to Win 7 and everything would be happy (I'd just would have to reload any software/files I wanted).
 
Well, that didn't go so well.
 
I could see my hard drive when I booted up Ubuntu on the USB. But, I couldn't access it. I couldn't mount it. I kind of felt like it was giving me the middle finger. Now, this is perhaps where I just don't have the linux skills to be awesome. But, doing some research on the interwebs...it just sounds like a file became corrupt, perhaps in that MBR (which, honestly, I never really heard of until yesterday). I could be wrong, but since my BIOS shows my computer fine, and Ubuntu on the USB atleast saw my hard drive...I figured the laptop could be saved....if only I had a recovery disk.
 
New dangerous thought / advice request
That takes you up to today. It looks like I could purchase recovery disks for about 10 bucks, so that's probably a good idea. But, I figured, why not dual boot this laptop with linux anyway. I really only use the thing to connect to the internet, to RDP into my work computer.
 
So, still having the Ubuntu 8.10 (and 9.04) disk, I was about to start installing it, since I remember when I created the USB drive, it partitioned the stick, so I figured these could do the same. However, some internet searches have me a little worried about doing that. They want to use Windows (which I can't access) to partition the hard drive, and some other partition software.
 
I then thought, instead of installing 9.04 (and perhaps Kubuntu), I should come to the official site and get the latest. My plan was to install 9.04 then start upgrading it...but, that's a waste of time. 
 
My thinking is that perhaps a dual boot version of Ubuntu would be able to get me into the Windows Vista partitioned part of my laptop and I could get the files I need off of it.
 
Now, maybe I wouldn't be able to recover Vista at that point, or upgrade it with the Win 7 discs...but, why not just keep Ubuntu on this laptop and learn something. Surely I'll eventually figure out a RDP-equivalent tool that could connect my linux laptop to my work computer. Right? Right?
 
**Is my thinking terrible?**
I'm going to start downloading the ISO (did I say that right) of the latest Ubuntu to a different USB stick so that as soon as any of you much smarter than I say "yeah, that could work" - I'll start.
 
Thanks for any heads up, warnings, tips, whatever. I'll continue looking over this site, and the interwebs for help getting my linux skills...well, better.

---

### Post by sudodus on 2012-05-16
Welcome to the Ubuntu Forums!

First of all, do you know if your Vista file system is encrypted or not?

When you boot from a CD or USB Ubuntu drive (8.10 or 9.04 should be fine), you can see the hard drive and it should be straight-forward to mount the partitions (read/write), so that your personal files are available.

If they are encrypted, I don't think Ubuntu can unlock that, but you might repair the file system. But there might something wrong with the drive (hardware read/write error or some file-system error).

There are linux tools available in Ubuntu to check for hardware errors. I think you should use Windows to check for and repair file-system errors. This can be done from some repair boot drive or from another windows computer, if you can move your hard drive.

---

### Post by Mark Phelps on 2012-05-16
It's very likely that your Vista BSOD carried with it some filesystem corruption -- which will prevent Linux OSs from mounting the corrupted partitions.  Linux does that to prevent damaging the filesystems further -- actually, a GOOD thing.

If you can't boot into Vista safe mode (which is generally done by pressing F8 repeatedly during the Windows boot, and you have access to a Windows PC, then you should download the Partition Wizard BOOT CD, burn that to CD, and boot your machine from it.

It will have the option to run CHKDSK (using the Check feature) on your Windows partitions -- and that might be enough to get them bootable again.

If not, it might repair them enough that you can then boot from an Ubuntu LiveCD or LiveUSB and use that to retrieve your files from the MS Windows partitions.

---

### Post by frizzlefrazzle on 2012-05-16
Oh, so I did leave out some info.
 
My OEM (I think) didn't include the ability to start in a Safe Mode, or it certainly doesn't work (ie, F8 - although I tried and searched the interwebs for everything).  It looks like they really wanted me to create those backup/recovery disks.  Ooops.
 
I did use a Live CD, and it too could not mount the drive, so...yeah, installing Ubuntu might not have any effect, for the reasons ya'll listed above.
 
Hmmm.  Seems like I'm leaving something else out, but its sounding like I really need to get my hands on recovery disks to make things easier.

---

### Post by wilee-nilee on 2012-05-16
9.04 is end of life, 10.04 supported for about a year 10.10 end of  life, try the latest release 12.04.

---

### Post by Ubun2to on 2012-05-16
Have you tried removing the hard drive and hooking it into another computer (preferably a Linxu distro)? You could most likely mount it, and if it was caused by a virus, Ubuntu won't be infected while you're cleaning it up.
Also, the MBR and partition tables are something you don't play around with. The MBR isn't easy to access for good reason, and very rarely does it need modifying (and if it boots but gives you a BSOD, the MBR is perfectly fine-if it refuses to get past the BIOS screen, you might have a problem).

---

### Post by wilee-nilee on 2012-05-16
> **Ubun2to said:**
> Have you tried removing the hard drive and hooking it into another computer (preferably a Linxu distro)? You could most likely mount it, and if it was caused by a virus, Ubuntu won't be infected while you're cleaning it up.
Also, the MBR and partition tables are something you don't play around with. The MBR isn't easy to access for good reason, and very rarely does it need modifying (and if it boots but gives you a BSOD, the MBR is perfectly fine-if it refuses to get past the BIOS screen, you might have a problem).

mbr is easy access

---

### Post by frizzlefrazzle on 2012-05-16
> **Ubun2to said:**
> Have you tried removing the hard drive and hooking it into another computer (preferably a Linxu distro)? You could most likely mount it, and if it was caused by a virus, Ubuntu won't be infected while you're cleaning it up.
Also, the MBR and partition tables are something you don't play around with. The MBR isn't easy to access for good reason, and very rarely does it need modifying (and if it boots but gives you a BSOD, the MBR is perfectly fine-if it refuses to get past the BIOS screen, you might have a problem).
 
I think this is my next option (slaving? the old hard drive).  Hopefully, I'll atleast be able to get a few files off the drive that I'd like.  Then, I don't think I'm going to care if I wipe Vista off the box, as I'm looking at 12.04 right now, and it is slick.  But, if there is a way to save /clean Vista...that would be fine, too.  I'd probably upgrade it to Win 7, and dual boot with Ubuntu as well...because, hey, linux is just cooler.
 
Thanks.

---

### Post by frizzlefrazzle on 2012-05-23
> **Mark Phelps said:**
> It's very likely that your Vista BSOD  carried with it some filesystem corruption -- which will prevent Linux  OSs from mounting the corrupted partitions.  Linux does that to prevent  damaging the filesystems further -- actually, a GOOD thing.

If you can't boot into Vista safe mode (which is generally done by  pressing F8 repeatedly during the Windows boot, and you have access to a  Windows PC, then you should download the Partition Wizard BOOT CD, burn  that to CD, and boot your machine from it.

It will have the option to run CHKDSK (using the Check feature) on your  Windows partitions -- and that might be enough to get them bootable  again.

If not, it might repair them enough that you can then boot from an  Ubuntu LiveCD or LiveUSB and use that to retrieve your files from the MS  Windows partitions.

Just an update for anyone that reads my issue and want so to know  how things turned out.  First, thanks, Mark.  I downloaded the Partition  Wizard 7 software you recommended.  It too originally didn't recognize  my HDD.  But, at some point, clicking on properties, or something, it  came up and a I was able to see it.  I didn't see CHKDSK or a Check  feature, but I did run a full scan that looked at each...um, is it a  sector.  Whatever, it ran for maybe 45 minutes, and everything was  green.

That may have been all I needed for Ubuntu 12.04 running  from  my thumb drive as a livecd to recognize my HDD, I didn't even have  to mount it when I finally logged back on.  But, I first tried fixing  the MBR with the rebuild feature.  

Well, it said it was  successful with that, however, when I tried booting up, it was in a  continuous loop.  I did get a screen to pop asking if I wanted to start  with Windows Vista, but it would just reboot each time.

So, after  doing that a few times, I went ahead and booted up from my thumbdrive.   I got some error I hadn't been getting the last week, some file Ubuntu  couldn't find or run.  Sorry, I don't recall what it was.  Well, after  logging on to the internet to update my fantasy baseball team, I decided  to reboot.  That didn't work very well.  It got stuck shutting down.    Again, some odd error that I didn't jot down.

But, the next time I  logged on, I checked my home folder, and saw that it was recognizing my  Acer drive, and I had access to all of those files!

I probably  could still fix Vista, but I'm going to back up all the files I want to  keep, then install Ubuntu on this laptop.  I'll partition the HDD so  that if I ever change my mind and want to try to fix Vista, I can, but  most of the disk space is going to Ubuntu.

Thanks a lot.  I'm sure I'll be asking more questions.

---

