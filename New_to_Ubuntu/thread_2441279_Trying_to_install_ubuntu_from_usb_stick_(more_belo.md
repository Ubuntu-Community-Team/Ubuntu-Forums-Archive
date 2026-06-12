---
title: "Trying to install ubuntu from usb stick (more below)"
date: 2020-04-21
forum: New to Ubuntu
---

### Post by jaredbuck on 2020-04-21
Hi all.

I am having trouble installing the latest version of ubuntu via a usb stick.When I select to install ubuntu and get to the drive to select to install on, ubuntu install IS ONLY SHOWING ME the external 4 tb drive I have. It is not showing either of the main hard drives inside my computer - one a 1 TB ssd and the other a 1 TB regular platter-based drive.  Using gparted and even various disk listing commands shows both of those drives, but the installer itself WILL NOT SHOW THEM.  I want to install to the 1 tb platter based drive as the ssd is used for windows 10 and I'd like to dual boot.

Any help here would be appreciated. I do not see an option in my alienware area 51 r2's bios settings to disable raid (as I know leftover raid settings can sometimes prevent the installer from actually seeing all my drives.

Jared

---

### Post by CelticWarrior on 2020-04-21
RAID and IntelRST modes aren often not supported. Change to AHCI after installing AHCI support in Windows if applicable.

---

### Post by jaredbuck on 2020-04-21
I just said I don't see an option in my bios settings to disable raid and switch to achi. So how I am supposed to do that?  I don't know how to install achi support either.

---

### Post by yancek on 2020-04-21
What is on the 1TB drive on which you wish to install Ubuntu?  Is this a new drive which has never had an OS or any data on it?  Is it partitioned and/or formatted and if so, what filesystem?

---

### Post by C.S.Cameron on 2020-04-21
Installing Ubuntu always seems to work best for me if only the Target drive is plugged in.
Are you installing using "Something else"?

---

