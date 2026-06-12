---
title: "Bricked Thumb Drive"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by C.S.Cameron on 2008-08-28
Has anybody had success un-bricking a thumb drive?
I have been booting Ubuntu from a Transend JetFlash V10 (8GB) for about a year now.
Installing Xubuntu for dual boot worked fine.
Then got the clever idea to attempt tri-booting XP.
Somewhere along the line I bricked the drive.
It use to show as
Jetflash USB Device
now it shows as
USBEST USB2FLASHSTORAGE.
Both Windows and Ubuntu tell me there is no media on it.
Partition Editor does not see it and windows will not format it.

---

### Post by gbold on 2008-08-28
I had this type of thing happen in XP with a thumb drive I have (with a True Crypt partition/file on it).  What I did in XP was I went into device manager (with it not plugged in) and had it show hidden devices.  I then deleted any storage volumes that were grayed out (light gray?) and any USB devices that were this way (grayed out)...  I then plugged it back in to another USB port and it got re-detected correctly.

I kinda freaked at first because of some info I had on it that I really didn't want to lose.  This may work, maybe not.
Good Luck-
Greg

---

### Post by TravisNewman on 2008-08-28
Try gbold's idea, that was what I was going to suggest first. But there IS the chance that it's dead. Thumb drives have a limited number of reads/writes and after you hit that, it's kaput. Hopefully we haven't gotten there yet, but if you've had it for a while it's a possibility.

---

### Post by gbold on 2008-08-28
Your avatar is almost as scary as mine... I like it!
;-)
Greg

---

### Post by C.S.Cameron on 2008-08-28
Could not find anything grayed out in device manager, I've tried the drive on 5 other computers and same story.
Do TD's die a sudden death? I figured they would just start rotting away slowly.

---

### Post by nicedude on 2008-08-28
Unlike hard disks that could develop bad sectors etc and therefore die slowly thumb drives just die unfortunately and as such you should backup any important data that you don't want to risk losing when using a USB flash drive.

Sorry if your drive is dead, looks like it could be though from what you posted. Only thing I could even recommend is to try forced mounting of the drive and see if you can then see it in the partition editor.

PS also since flash disks have a limited amount of read and write cycles in their lifetime using OS's installed on them might hasten their death due to constant writing of swap or other files ( both Linux & Windows like to write allot )

And greg your avatar is the scariest, if that is you then you look like you are not thinking good thoughts :-)

---

### Post by C.S.Cameron on 2008-08-28
Did not use this drive much at all as it has low R/W speeds.
Seemed suspicious it happened just after re-formatting and Installing a fresh Ubuntu, which I just remembered.

---

### Post by nicedude on 2008-08-28
That at first seems like it would implicate Ubuntu as a factor in its failure but remember that when formating and reinstalling etc that there would be a ton of reads and writes and therefore it still can be the number of reads & writes that killed it and not really anything due specifically with the Ubuntu install.

---

### Post by Crafty Kisses on 2008-08-28
Is the USB drive even recgonized? Post results of > lsusb

---

### Post by C.S.Cameron on 2008-08-28
I don't blame partition editor, I did a fresh install because the TD was starting to feel a bit wonky after trying to install XP.
But why would the ID of the device change from Transcend to UBCBEST?
Transcend site says it has a lifetime guarantee, suppose it is just for the lifetime of the dongle.

---

### Post by nicedude on 2008-08-28
I have no idea why the drive label would change but if you want I would try sending it back to the manufacturer and I would not be supprised if they would replace it. To try to fix it though I would say you would have to try and force mount it and if that works then you could try to wipe the partitions on it and then repartition it.

You might try installing pysdm which is a python script that can mount drives for you in Ubuntu and works well when disks have been removed without being unmounted etc which can cause USB drives to not mount. Here is first the command to install pysdm and the command to run it, once inside see if it shows your USB disk and see if it could mount it for you. I still think though that your drive may be toast though from your saying that you have tried it in multiple PC's.


sudo apt-get install pysdm

sudo pysdm

---

### Post by C.S.Cameron on 2008-08-28
When I plug it into an Ubuntu machine It does not appear on the desktop but shows up in File Browser as
USB Drive
lsusb (with only this USB installed) gets

Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 003: ID 1307:0163 Transcend Information, Inc.
Bus 001 Device 001: ID 0000:0000

---

### Post by nicedude on 2008-08-28
Then try using pysdm as I suggested previously to see if it will mount it and if so then use partition editor and see if you can redo the drive. Just because a flash drive won't mount it can simply mean it wasn't unmounted properly and therefor it will act up until you force mount it or let pysdm force mount it for you. Please post whether it mounts it.

---

### Post by C.S.Cameron on 2008-08-28
All I can find using SDM is sda5 which is my swap

---

### Post by nicedude on 2008-08-28
Its pysdm not sdm but assuming you used pysdm it should have in the left side of the GUI a list of disks and when you click on a disk it should show the partitions on that disk. It should for sure be able to see all your normal drives. Whether it will list your USB drive I do not know but it should list everything else for sure ( I have used it on 4-5 systems and it never fails to at least show what drives are present including USB ones that need forced mounting due to improper removals )

---

### Post by C.S.Cameron on 2008-08-28
It only shows sda and below that sda5, (when I click the little triangle)
When I plug in a second drive it see's sdb OK.

---

### Post by nicedude on 2008-08-28
Well that is crazy since you obviously have more than one partition since Linux requires 2 a swap and a system one. Try the following command and post the output here with your USB drive plugged in.

sudo fdisk -l

and that is a lowercase L to save confusion if you type it.

---

### Post by C.S.Cameron on 2008-08-29
Sorry, my hard drive just died, at least it is no longer recognized by bios.

sudo fdisk -l has no effect when I try it from cd boot.

---

### Post by nicedude on 2008-08-29
I would have to ask at this point if you have opened your PC case and messed with drive cables lately? If so make sure they are snugly in place. Also I would experiment with BIOS settings and menu's and see if you can find the drive is recognized as you may have changed something that is causing this. I would not just assume my disk is toast at this point as I have seen drives do all kinds of screwy things and be fixed with a little tinkering with settings etc. If you think you have lost all your data on the drive anyway and are ready to call it broken then I would suggest you download a copy of DBAN ( dariks boot n nuke ) which is free and you can find it via googling "dban" once you get it ( it is a small couple of megabytes iso image ) you burn it to a CD and boot with it and see if it can wipe your drive clean ( I have had drives that would not function at all that I thought were toast and after a fresh dban wipe they were just fine, albeit blank of course ), in DBAN just select 1 pass random data with no verify so it doesn't take all night but instead maybe an hour or so ( you also are not trying to destroy secret data so the extra passes are not needed anyway ). Once that is done see if the drive won't take an Ubuntu or Windows install as I know you at least have a chance that it will.


hope that helps you get it fixed.

---

### Post by C.S.Cameron on 2008-08-29
The mother board is not actually in a case, it is hanging off the wall. The PS and drives are spread out on the bench below it. 
The old HDD no longer spins when plugged in. It is only 20GB so must be pretty old, Likely another coincidence.
As luck would have it, spotted a computer next to a dumpster when walking the dog this morning.
Nice 80GB HDD, The MB works and is now hanging on the wall next to the old MB.
Tried a 
sudo fdisk -l
but that only sees the new hard disk and the USB HDD I booted from.
I have e-mailed Transcend, and they say they will get back to me.

---

### Post by nicedude on 2008-08-29
Found a computer by the dumpster now that is low cost computing :-)

Hey you might want to take note that it is not the best idea to not have the motherboard in a case and you for sure need to make sure nothing metal ever touches it and grounds or shorts stuff out.

And since it was a 20GB drive that just bonked out that tells me it is maybe 3-5 years old and it might just be that it died of old age as most hard drives are only under guarantee for 3 years with a few giving 5 years, and we all know that stuff breaks right after the warranty expires :-)

Hope you get your new 80GB HDD working with an OS

If I can help you out in any way feel free to PM me and ask as I am pretty knowledgeable about PC hardware issues.

---

### Post by C.S.Cameron on 2008-08-30
Thanks Nicedude:
Transcend sent me to this site:
[http://www.transcendusa.com/Support/DLCenter/index.asp](http://www.transcendusa.com/Support/DLCenter/index.asp)
Where I downloaded 'Recovery Utility' for V10
It looked like it was going work, took about 3 hours to run, said it had completed, but no change to the USB.
I am having a hard time formatting the new hard drive,
Guy has all sorts of personal data on it, Bank and Tax records, vacation photos...
Found his e-mail address and have asked if he really wants to trash the drive, have not heard back yet.
I don't think I'll just toss my old drive in the trash, wondering how to wipe a drive that doesn't spin, hammer I guess

---

