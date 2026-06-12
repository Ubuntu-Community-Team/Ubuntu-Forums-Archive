---
title: "Install issue"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by Dolalu on 2012-12-25
Brother got a new pc for xmas with no operating system as he wants to run unbuntu on it, created an iso image on laptop,, installed and everything was going good, upon restart there was spme error messages (end request i/o error) and where unbuntu started the screen was full of pixels and froze...we are now at a point where im not sure what to do next but i want to get it sorted for him tomorrow. 

Any ideas? His computer is decent enough quad amd 3.6, 8gb ram,2gb radeon graphics card, 1tb hd so should be able to cope

Can we delete and start again?(how?)
Thanks
Luke

---

### Post by drpjkurian on 2012-12-26
Well that message probable mean this > The System Log Says, "end_request: I/O error, ...."
This error message, and messages like it, almost always indicate a
hardware error with a hard drive.

This commonly indicates a hard drive defect. The only way to avoid
further data loss is to completely shut own the system. You must also
make sure that whatever data is on the drive is backed up, and restore
it to a non-defective hard drive.

This error message may also indicate a bad connection to the drive,
especially with home brew systems. If you install an IDE drive, always
use new ribbon cables. It's probably is a good idea with SCSI drives,
too.

In one instance, this error also seemed to coincide with a bad ground
between the system board and the chassis. Be sure that all electrical
connections are clean and tight before placing the blame on the hard
drive itself. 

This is what I got when I googled the error message

---

### Post by Dolalu on 2012-12-26
> **drpjkurian said:**
> Well that message probable mean this 

This is what I got when I googled the error message

Thats, system is brand new so i wouldnt have thought it was a harddrive fault?

---

### Post by fdrake on 2012-12-26
> **Dolalu said:**
> Thats, system is brand new so i wouldnt have thought it was a harddrive fault? booting into live section did you experience any issues?

> upon restart there was spme error messages (end request i/o error) can you be more precise?

---

### Post by Dolalu on 2012-12-26
> **fdrake said:**
> booting into live section did you experience any issues?

can you be more precise?

The install itself went ok, did everything as youd expect it to, issue came when it restarted for first time, then it came with this I/O message that went something like 453.345643 then I/O message. Now it goes to main screen but just freezes, also has hundreds of red pixels on the screen

It was installed onto a Virgin harddrive with no partician or  anything, is there a way to delete everythi g and start again or to rescue install

Thanks for replies to date

---

### Post by fdrake on 2012-12-26
> **Dolalu said:**
>  is there a way to delete everythi g and start again or to rescue install

you can. Just boot into the live cd again. Before you attempt the install check the cd for possible errors. also try it first to see if the hardware is compatible. Browse the internet, check sound and video. then install with the option like "erase everything and install ubuntu"(something like that)

---

### Post by andybrady on 2012-12-26
I  have found that just  buying a disc ($10 including shipping) eliminates all the questions of download and disc creation  problems.    Not the most frugal approach, but it eliminates lots of possible problem with net connections and data transfer.

---

### Post by fantab on 2012-12-26
> **Dolalu said:**
> It was installed onto a Virgin harddrive with no partician or  anything, is there a way to delete everythi g and start again or to rescue install


How did you partition the Hard Drive? 
Did you create any Partition Table? How big is your Hard Drive?
Does the laptop has Bios-boot or UEFI?
What kind of Graphics does the laptop has?

---

### Post by Dolalu on 2012-12-26
> **fdrake said:**
> you can. Just boot into the live cd again. Before you attempt the install check the cd for possible errors. also try it first to see if the hardware is compatible. Browse the internet, check sound and video. then install with the option like "erase everything and install ubuntu"(something like that)

Managed to get desktop on, when it restarted it is now scrollong through a black screen saying
[ 186.309359] swap_dup: bad swap file entry 20c2c8f0

Any ideas? Its just stuck scrolling on this page

---

### Post by Dolalu on 2012-12-26
> **fantab said:**
> How did you partition the Hard Drive? 
Did you create any Partition Table? How big is your Hard Drive?
Does the laptop has Bios-boot or UEFI?
What kind of Graphics does the laptop has?

Hi

500gb hd
Graphics is radeon HD 6570
Its a desktop pc

I dont think he created a partition just installed directly
Thanks

---

### Post by fdrake on 2012-12-26
> **Dolalu said:**
> Any ideas? Its just stuck scrolling on this page
did you run a checksum of the disk for integrity. It looks like a kernel issue. Which ubuntu are you installing 12.04? Try a different version

---

### Post by fantab on 2012-12-26
Well then, use [**GPARTED LiveCD/LiveUSB**]("http://gparted.sourceforge.net/livecd.php") (its a valuable tool have around) or use your Ubuntu LiveCD and delete everything on the HDD. And then start with creating a partition table... choose MSDOS table/DOS table. 

If the PC has** UEFI **and not BIOS then you have create the first primary partition of about 500mb-1gb and during Ubuntu install you should format it as Fat32 (I am not sure please check on google or these forums) and mount it as '**/boot**'. 

Remember to create a SWAP partition of about at least 1GB. Ideally this is not required by newer PC with more than 2gb RAM, however to avoid any inconvenience later, create one.

---

### Post by audiomick on 2012-12-26
Regarding swap: if your swap is not a little bigger than the amount of RAM, then the hibernate function wont work. If that is not important, the 1GB should indeed be enough for most normal users. On the other hand, if the drive is big, what are a couple of GB here or there?

You have said a couple times you don't think a partition was created. This is not the case. The installer would have created a partition for the system, and a partition for swap. You can check this by looking at the drive with gparted as suggested. You don't really need to go to the bother of getting gparted on a CD of it's own. It is on the Ubuntu installer, and if you can get into the "try Ubuntu" on that, you have gparted.


Do not discount the possibility that the drive is faulty even though it is new. This does happen. You could perhaps look at it with the hard drive application from the live environment on the installer CD (the "try ubuntu" option). There is a button in there to look at the SMART values of the drive. These are self test results that the drive saves about itself. Maybe that will tell you something, even if it is just that the drive is healthy.

Open the case, unplug the drive and plug it back in. You never know. I had periodic trouble with a drive for about 2 years before I gave in and changed the cable...

---

