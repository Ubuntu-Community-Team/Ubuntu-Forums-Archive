---
title: "Shuttle SG31G2S and Ubuntu"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by Malmberg on 2013-05-03
Gents, "The Newbie" has a new problem!
I have/had an old well functioning Shuttle Xpc SG31G2S (Core 2 Quad / Intel G31 + ICH7) with 2 Sata drives, OS =  XP. 
I thought that I would upgrade this a bit by installing Win7 on one drive, and Ubuntu 12.04 on the other drive.
I did a low-level format of both drives - disconnected one drive, and started my Ubuntu Live CD.
I did chose "the manual installation" - did the "partitioning" and hit the "next" button,
the installation started for seconds - then I got an dialogue box = error, can not write xxx partition. And only way out was a reboot, pc was hanging.
If I look at the drive (Gparted) then I can see the partitions - but it looks as the /home not is formatted?

Sigh
Then I disconnected the drive - and attached the other one, and started the Win/ installation - it also hangs when it comes to writing files to the drive?
Btw. I can install Win7 on a IDE drive!

So - do I have a faulty motherboard? - or have I (again) misunderstood something?

Any help will be appreciated - thanks

Malmberg

---

### Post by tgalati4 on 2013-05-03
It sounds like when you disconnected the drives, the Live CD got confused.  Try reconnecting the drives, then rebooting the Live disk and see if the installer works correctly.

---

### Post by Kopkins on 2013-05-03
I think it's interesting that if failed in both installs. Maybe run a Disk Test to make sure the disk is okay. From Ubuntu live cd there should be a disk utility app you can use to analyse disk health.

---

### Post by 2F4U on 2013-05-03
Is the cable properly connected to the drive? Is Gparted from the liveCD (not from the installer) able to create and format the partitions?

---

### Post by Malmberg on 2013-05-03
> **tgalati4 said:**
> It sounds like when you disconnected the drives, the Live CD got confused.  Try reconnecting the drives, then rebooting the Live disk and see if the installer works correctly.

Hi tgalati4
Have been there - no luck :-(
But thanks!

---

### Post by Malmberg on 2013-05-04
> **Kopkins said:**
> I think it's interesting that if failed in both installs. Maybe run a Disk Test to make sure the disk is okay. From Ubuntu live cd there should be a disk utility app you can use to analyse disk health.

Hi Kopkins,
I have tried with 5 drives - they are all Nuked - and in good shape!

I think I will install Win7 on a IDE, and see if I can find a way to install Ubuntu on the SATA drive!

Thanks

---

### Post by Malmberg on 2013-05-04
> **2F4U said:**
> Is the cable properly connected to the drive? Is Gparted from the liveCD (not from the installer) able to create and format the partitions?

Hi 2F4U,

Yes - and I have tried with a set of brand new cables!
Gparted can create - but not format the partitions.

I should have done some research on the Win7 installation problem -apparently this is a well known issue!

Thanks

---

### Post by Malmberg on 2013-05-08
UPDATE - problem solved (more or less)
Long story!
As written, I had an old Shuttle Xpc SG31G2S that I would give a new life :-), as my desktop PC with dual-boot = Win7 and Ubuntu.
There was 2 SATA drives inside, so I thought - one drive with Win7 and one drive with Ubuntu 12.04.
I disconnected one drive (and disabled the floppy controller in the Bios), nuked the other drive, and fired the LiveCD up - everything went well until Gparted started to format the partitions. Then the PC did freeze!
I did some searching to see if there where any obvious reasons - but was more confused.
So I thought that I would install Win7 (how hard could that be?) - I disconnected the "Ubuntu drive", and attached the other drive, nuked that, and WIn7 installation DVD in the drive.
It took forever to load, and eventually there was the famous BSOD :-) hmmmmmmmmmmmm!
Goggle was my friend - it pointed me in the "Bad Capacitor" direction. I inspected the motherboard - and viola, 3 bulging (crap) capacitors (1800uF/6,3V).
Our local "Parts-pusher" had some nice Panasonic in stock - so firing up the soldering iron, and replaced the caps.
Motherboard back in place - power on - and YESSSSSSSSSSSSSSSSSSS, soldering job done OK!
Live CD in tray - and the installation went fine, then Win7 in tray - and installation went fine!
So now I have a nice low-noise small dual-boot Shuttle stuck under my table :-)

Sorry for this long story - but it had a happy ending!

---

