---
title: "Parallel ATA not found at bootup"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by doninsa on 2008-07-15
Greetings - Here's my problem -

Hardy Heron 8.04 does not detect the CD player connected as the secondary master on my Asus motherboard.  MB is an M2NPV-VM.  Boot process is real slow.  I've enabled text viewing using Startup Manger and can see that here is a long pause while the system tries to detect hardware. After about 2 minutes it fails and the boot process continues.  If I disable IDE-0 and IDE-1 in BIOS the hardware detect process is just a few seconds, but then I can't use the CD player.  How can I get Ubuntu to detect the IDE ports?  Any help with this seemingly impossible problem would be much appreciated.

Thanks,
Don

---

### Post by ApOgEEs on 2008-07-23
have you try to change your IDE cable?

---

### Post by squeakyfrommage on 2008-12-02
*Bump* Did you ever get this solved? I'm having the same issue. Thanks

---

### Post by porchrat on 2008-12-02
are there 2 separate controllers on your motherboard?  Are you saying that the SATA works while the IDE doesn't?  Could be that Ubuntu doesn't come with the drivers for that controller installed.

---

### Post by sydbat on 2008-12-02
It sounds more like a hardware issue than anything OS related. I know it was a few months ago for the OP, but if he changed the IDE cable and it still booted slowly, it might have been a BIOS setting. Or the CD drive (or other drive connected to the IDE cable) could have been faulty and not be detected. 

Lots of possibilities, mostly hardware related. If the hardware is faulty, nothing in Ubuntu or any other OS will get it to work.

---

### Post by porchrat on 2008-12-02
It is still possible that it is just a driver issue.  Does the BIOS see the CD-ROM?  If so then it isn't a hardware issue.  I have a controller that currently doesn't have ubuntu drivers (or at least it didn't a few months ago things could've changed by now)

---

### Post by squeakyfrommage on 2008-12-02
I'm running 7.10, and it was working perfectly until I did updates (not upgrade. ;) ) Now it says "parallel ata not found" at boot and I don't see the drive anywhere after boot either.  I have several other unrelated things configured specifically for work, enough that it would be a lot of work to upgrade right now, so I'm hoping to find a solution other than that. 
thanks

---

### Post by sydbat on 2008-12-02
Definitely check your BIOS and make sure the drive is seen there. If it is, then we can start looking at driver issues.

---

### Post by squeakyfrommage on 2008-12-02
Thanks, the drive is seen there and says it's enabled.  Is there something that anyone knows of that's changed recently in Ubuntu that I should look at for possible help? Also, anything I should look for in dmesg? The drive worked from day one with the original install of 7.10, I didn't have to tweak anything at that time.  It was updates a few weeks ago that caused this error to appear.

---

### Post by porchrat on 2008-12-02
> **squeakyfrommage said:**
> Thanks, the drive is seen there and says it's enabled.  Is there something that anyone knows of that's changed recently in Ubuntu that I should look at for possible help? Also, anything I should look for in dmesg? The drive worked from day one with the original install of 7.10, I didn't have to tweak anything at that time.  It was updates a few weeks ago that caused this error to appear.

Unfortunately I have very little experience with these sort of issues, but please post the entire dmesg (I know it is long, but you never know it may help).  Perhaps someone will see something in it to help you.

Please also look up on the net (google should tell you) which IDE controller your motherboard has so that we can look up the driver situation and see if this problem has happened before.

---

### Post by squeakyfrommage on 2008-12-02
deleted. See corrected entry below.

---

### Post by squeakyfrommage on 2008-12-02
It's a dell RD203 motherboard, with  Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE. 

I realize it is possible that the drive has failed for some other reason, but since it coincided with updates, I'd like to make sure that it's not an ubuntu issue first.  

Here's the output of dmesg:

---

