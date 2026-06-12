---
title: "500GB HDD, Only Recognised as 32GB by Bios"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by paulm2008 on 2008-11-26
Hello, I have a problem, When I attached a 500GB HDD to my Striker II Formula motherboard.  The Bios Only recognises it as 33GB HDD.  However when I go into the Ubuntu Partition editor [GParted [?]] the 500GB drive is there.  I can format the drive within this utility - and all is well,  then when I re-boot the HDD it is recognised as being 500GB - But when I re-Boot shut-down fist and re-apply the power, the bios reverts back to seeing the drive as only a 33GB.  I do not know why this should be the case.  I cannot find any cause of this discrepancy, nor do I know how to solve the problem.  Any Ideas, or is it RMA the HDD
Kind Regards
Paul

---

### Post by Therion on 2008-11-26
Internal or external drive?  SATA or IDE?

---

### Post by paulm2008 on 2008-11-26
> **Therion said:**
> Internal or external drive?  SATA or IDE?

Sorry !!

WD5000AAKS SATA II Internal

I have also the lastest 1802 BIOS for the Motherboard [release last week] and also the latest Chipset Drivers From nVidia

---

### Post by Therion on 2008-11-26
LOL... No prob.

This really IS odd...  

Are your connecting directly from drive to SATA header on the mobo?  

When you go into the BIOS, does the drive EVER register there as being 500GB?  I'm assuming not, but tell me so we're clear.

If you have a spare, open, SATA header on your mobo, have you tried switching the drive connection?

---

### Post by melrokz on 2008-11-26
If u r using a desktop, u may have to check your HDD jumper settings (master/slave)
Upto 40 GB, there is one setting and above it there is another. You may have to see the label of your hard drive for this.

---

### Post by paulm2008 on 2008-11-26
> **Therion said:**
> LOL... No prob.

This really IS odd...  

Are your connecting directly from drive to SATA header on the mobo?  

When you go into the BIOS, does the drive EVER register there as being 500GB?  I'm assuming not, but tell me so we're clear.

If you have a spare, open, SATA header on your mobo, have you tried switching the drive connection?

Thank you For your reply

I know its really strange.  I connect the HDD directly to the Mobo.  I have tried other SATA slots on the board and that has the same effect.  I have 3 other HDD's of the same make and model, All these show up as 500GB.



When I turn the machine on the Bios always states 33GB - when I then load ubuntu - Go in to partition editor, it sees 500GB.  I can then format the drive - Then when I re-boot without powering down the BIOS sees the 500GB.  However again re-booting, turning the power on and off, the bios reverts back to 33GB.  It seems ubuntu sets something which the bios likes, then when you remove power it goes and reverts back to the old 33GB setting

---

### Post by paulm2008 on 2008-11-26
> **melrokz said:**
> If u r using a desktop, u may have to check your HDD jumper settings (master/slave)
Upto 40 GB, there is one setting and above it there is another. You may have to see the label of your hard drive for this.

Hi tahnks for the interest in solving my problem, I have no jumpers at all on the drives.  As I said earliey, I have 3 other drives of the same make and model, these are all OK showing 500GB in the bios at bootup

---

### Post by damis648 on 2008-11-26
Do you have any other computers you could check this on?

---

### Post by paulm2008 on 2008-11-26
> **damis648 said:**
> Do you have any other computers you could check this on?

Afraid not.  I gave my old PC Away, that didn't have SATA connectors - so It would have been no use.  I may e-mail ASUS and western digital and see what they say

---

### Post by Therion on 2008-11-26
> **melrokz said:**
> If u r using a desktop, u may have to check your HDD jumper settings (master/slave)
SATA drives don't have jumpers.

> **paulm2008 said:**
> When I turn the machine on the Bios always states 33GB - when I then load ubuntu - Go in to partition editor, it sees 500GB.  I can then format the drive - Then when I re-boot without powering down the BIOS sees the 500GB.  However again re-booting, turning the power on and off, the bios reverts back to 33GB. 
This is sounding like a "communication" error between the drive and the BIOS.  What confuses me is that the Partition Manager is seeing the drive correctly even though the BIOS does not.  Unless the BIOS is simply making what amounts to a "reporting" error; in which case you could just ignore what it's telling you.  If the OS is "seeing" 500GB and allowing you to ACCESS all 500GB (and that's the real issue, isn't it?) I'd be inclined to write it off as some sort of bizarre behavior and simply get on with life.  At the same time I can understand how you'd really like to have a "real" answer...  Emailing WD and/or ASUS is the next logical step, but something tells me it will wind up being a fool's errand.

I swear sometimes that SATA is just... Quirky.

---

### Post by paulm2008 on 2008-11-26
The thing is that when I re-boot the system, ubuntu and windows state that the HDD is not in a usable state, basically I think the drive is telling the system that the drive is newly installed and has no formatting.  Hence anything I put on the drive is not accessable.  I will see what WD say in the first instance.  I will post anything of interest back here.  I must admit I have not experienced anything like this before.  All very strange

---

### Post by paulm2008 on 2008-11-27
> **Therion said:**
> SATA drives don't have jumpers.


This is sounding like a "communication" error between the drive and the BIOS.  What confuses me is that the Partition Manager is seeing the drive correctly even though the BIOS does not.  Unless the BIOS is simply making what amounts to a "reporting" error; in which case you could just ignore what it's telling you.  If the OS is "seeing" 500GB and allowing you to ACCESS all 500GB (and that's the real issue, isn't it?) I'd be inclined to write it off as some sort of bizarre behavior and simply get on with life.  At the same time I can understand how you'd really like to have a "real" answer...  Emailing WD and/or ASUS is the next logical step, but something tells me it will wind up being a fool's errand.

I swear sometimes that SATA is just... Quirky.


Well Western Digital informed me that there must be a problem with my drivers.   This I know is incorrect since 1. The drivers and the BIOS are all upto date 2. My other WD5000AAKS devices are seen perfectly OK with my mobo.

I have undertaken a bit of Google search.  In my search I came across Seagate HDD utility called Seatools which allowed the drive size to be re-set.  I do not know how or what this tool actually does but it allows the user to specify either a maximum drive size -or- enable via software to define the maximum size as that determined by the Seagate Seatools [For DOS] utility.  When I basically allowed the software to define the max size - saved and exited the program.  Upon re-starting [power off & on] the Bios recognised the drive as 500BG !!  I'm unsure exactly what these tools have done or how whatever was written to the HDD to inform the bios of the drive size became corrupted in the first place.  It does seem to have sorted the problem out though.  It will be interesting to see what additional information Western Digital come up with !!  

Regards

Paul

---

### Post by paulm2008 on 2008-12-06
Update : Western Digital Told Me To RMA the Drive !!

---

