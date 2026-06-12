---
title: "External Hard drives"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Joe Schmoe_10 on 2008-11-15
I have four dead external hard drives. All of them have NTFS on them from XP. Just made the switch to Xubuntu and they initially worked, but one by one have gone belly up. They all spin up ... but that is all they do. Anyone ever have this problem?
Thanks in advance!

---

### Post by oilchangeguy on 2008-11-15
> **Joe Schmoe_10 said:**
> I have four dead external hard drives. All of them have NTFS on them from XP. Just made the switch to Xubuntu and they initially worked, but one by one have gone belly up. They all spin up ... but that is all they do. Anyone ever have this problem?
Thanks in advance!

sounds strange you'd have four dead drives. and even stranger that you keep buying more. but it sounds like maybe a problem with your computers usb ports. try removing the drives from their cases, and plug them directly into your computer, and see what happens.

---

### Post by dark_harmonics on 2008-11-15
> **oilchangeguy said:**
> sounds strange you'd have four dead drives. and even stranger that you keep buying more. but it sounds like maybe a problem with your computers usb ports. try removing the drives from their cases, and plug them directly into your computer, and see what happens.

Or plug them into your second Ubuntu computer :)

---

### Post by Kellemora on 2008-11-15
Hi JS

You probably have to install the programs required to see an NTFS drive.

I THINK it's

sudo apt-get install ntfsprogs

BUT DON'T TRY THAT UNTIL someone comes along to verify that is correct.
I'm only guessing the name.  It could be ntfs-3g or something like that too.

Also, if you have a LIVE CD, you could plug in the drive, reboot from the LIVE CD and see if it can detect it to tell you the name of the drive and things like that, might even make it work and let you reformat it to ext3.

TTUL
Gary

---

### Post by scorchgeek on 2008-11-15
You say they worked initially? That's odd--I assume you tried rebooting to be sure it's not a mounting issue? If you have Windows, you could see if they open in Windows.

Do you need to keep the data on them?

---

### Post by Joe Schmoe_10 on 2008-11-15
> **oilchangeguy said:**
> sounds strange you'd have four dead drives. and even stranger that you keep buying more. but it sounds like maybe a problem with your computers usb ports. try removing the drives from their cases, and plug them directly into your computer, and see what happens.

Hmmm? I do not recall mentioning continuing to buy more hard drives. The only PCs in this house are laptops and the externals are for desktops. USB ports work for all other devices. Tried connecting them to XP, but now that OS does not detect them either.

---

### Post by Joe Schmoe_10 on 2008-11-15
> **scorchgeek said:**
> You say they worked initially? That's odd--I assume you tried rebooting to be sure it's not a mounting issue? If you have Windows, you could see if they open in Windows.

Do you need to keep the data on them?

I have tried rebooting and tried going back to XP to no avail yet. Yes, I want the data. Two of the drives are exact copies of each other. If I can access one, I intend to format the other to FAT32 to avoid this problem in the future when switching back and forth from Xubuntu and XP.

---

### Post by epswinde on 2008-11-15
Connect one of the dead drives, power it on, and post the output of:
```
sudo fdisk -l
lsusb
```
The first command lists the fixed disks that are attached to the machine, whether or not they're mounted.
The second command lists any usb device that is attached to the machine.

You should repeat this process for each drive, but only post one of them so that we can show you an example of how to do diagnose this on your own.

---

### Post by Joe Schmoe_10 on 2008-11-15
> **epswinde said:**
> Connect one of the dead drives, power it on, and post the output of:
```
sudo fdisk -l
lsusb
```
The first command lists the fixed disks that are attached to the machine, whether or not they're mounted.
The second command lists any usb device that is attached to the machine.

You should repeat this process for each drive, but only post one of them so that we can show you an example of how to do diagnose this on your own.

joe@joe-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bd21bd1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7120    57191368+  83  Linux
/dev/sda2            7121        7296     1413720    5  Extended
/dev/sda5            7121        7296     1413688+  82  Linux swap / Solaris

joe@joe-laptop:~$ lsusb
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Only the 60GB internal laptop hard drive shows up after the first command.

---

### Post by epswinde on 2008-11-15
do you have the drive connected via the usb hub? that could be bad; thus preventing the system from seeing the drives, but that's just a shot in the dark.  Most likely its the drive itself.  Unless you have some valuable data on the drive(s), you've got yourself some paperweights.

Otherwise, (as suggested above) break those bad boys open and see if you can connect them internally.

---

