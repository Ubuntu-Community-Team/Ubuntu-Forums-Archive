---
title: "[SOLVED] Partition new hard drive now won't boot"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by cmittle on 2008-11-11
I recently had a bad hard disk in my house server.  I purchased a new hard disk and installed it last night.  I booted up the computer and ran gparted to format as ext3.  I gave the disk a disklabel of msdos, and formated to ext3 (primary partition I believe it was called).  When I rebooted the computer it now just hangs at Verifying DMI Pool Data...

1.  I had my installed hard drive set as master by the jumper, and the new one as cable select.  I verified in the BIOS that the appropriate drives came up as Master and Slave and they did.

2.  I tried changing both to cable select, checked the BIOS to make sure they are in the right order, and I still hang at the Verifying DMI Pool Data...

3.  If I unplug the second (newly purchased, installed and formatted) hard drive it boots up just like normal (28 seconds).

4.  If I have both hard drives plugged in and boot to the CD and chose the "boot to hard drive first" option it works just like normal as well.  I can access this drive (although I just realized I haven't tried writing anything to it yet).

Please help me fix this I would like to get this working so I can backup my pictures.

Cory

---

### Post by phillik747 on 2008-11-11
> **cmittle said:**
> I recently had a bad hard disk in my house server.  I purchased a new hard disk and installed it last night.

What is the purpose of this new drive, to store data or to hold the OS?

If its just for data storage I would put it in the slave position and put the os in the master position. What was on the original 'bad hard drive?' 

You probably already know this but make sure your master drive is at the end of the IDE cable.

MOBO=======SLAVE HDD=======MASTER HDD

> **cmittle said:**
> 2. I tried changing both to cable select, checked the BIOS to make sure they are in the right order, and I still hang at the Verifying DMI Pool Data...

This should have worked. When you say "right order" do you mean boot order?

---

### Post by cmittle on 2008-11-11
The extra drive is to act soley as a backup storage in case of problems with the first.  I have had this first drive up and running for ~10 months now tinkering around with ftp server, samba shares, ssh.  

I currently have the jumpers on both set as cable select and I do have them connected like your diagram (which helped b/c that was one thing I wasn't 100% on).  When I boot into the BIOS it says something along the lines of IDE Primary Master *some_numbers* and IDE Primary Slave *some_different_numbers*.  When I go into these menus they confirm that the appropriate one is being recognized as master.

Yes by right order I meant boot order.  Right now my boot settings are HDD1 -> HDD2 -> CDROM.  I assume that HDD1 would correspond to the detected IDE Primary Master mentioned above.

Any more/other ideas?

---

### Post by phillik747 on 2008-11-11
This really sounds like a boot order issue, but I could be wrong.  

During boot does it have a boot menu option like hitting the F9 key?  If so let that boot menu come up and select the HDD you wish to boot.  If that worked there there is something wrong in the BIOS settings.  The Boot menu should show the HDD by location (master, slave, IDE0, IDE1, etc..) and/or by vendor name (Maxtor, WD, Seagate, etc..)

---

### Post by cmittle on 2008-11-11
It doesn't show any options on screen about what buttons to push.  I think on my other computer (also Emachines) it is F10.  I will try that tonight sometime.

---

### Post by cmittle on 2008-11-12
After I loaded the "optimized defaults" to the BIOS yesterday I went looking around for what changed.  The first thing I noticed was that my boot order was now;
1. Floppy (it is an old computer no suprise)
2. CDROM 
3. HDD-0

wait a tic... I have not seen this HDD-0 before.  Sure enough my options for boot devices goes something like this...
something
HDD-0
Floppy
CDROM
HDD-1
HDD-2
HDD-3
some more

The weirdest part is until about a month ago I had two disks in there booting just fine with the following;
1. HDD-1
2. HDD-2
3. CDROM

For some reason my new drive made my computer hate this boot order, but all I had to do to fix it was change the boot order to;
1. HDD-0
2. HDD-1
3. CDROM

Solved.

cory

---

### Post by phillik747 on 2008-11-13
> **cmittle said:**
>  all I had to do to fix it was change the boot order to;
1. HDD-0
2. HDD-1
3. CDROM

Solved.

cory

Heck I was right! Glad your system is working again.

---

