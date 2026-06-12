---
title: "uefi boot"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by Amithiel on 2012-12-20
hello,

I own an ultrabook from asus ( S56CM )
and i want to install only ubuntu on it. But i want to know how! because of this uefi boot, or what it's called.

specs:

core i7 
6 GB ram
24 GB ssd + 1TB hdd ( they called this an hybrid disk? its not pure ssd, however i can install ubuntu on it, right?)

help me out guys. Im affraid i get into trouble, i heard people getting a messed up system and they couldn't install anything after.

Will it be secure? what if i want to format and go back to windows 8, can i still do it?

---

### Post by oldfred on 2012-12-20
You want to install dual boot. But of course make full backups before doing anything.
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Different model but Asus, so UEFI should be similar?
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

            ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

If you have the SSD, is that the Intel SRT? Similar for most vendors.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by Amithiel on 2012-12-20
hey thanks for the reply. i just disabled fast boot.

also, i was messing around with uefi settings, in the security i changed some options to allowed. 
like, install from usb, and bla bla bla. it was everything denied execution. and i allowed. was that a good thing? thought it could help the ubuntu install a bit.

i don't like dualboot, i would prefer just ubuntu or linuxmint. it has to be in dualboot?

---

### Post by arpanaut on 2012-12-20
A couple of links to get you started:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by oldfred on 2012-12-20
Not sure with Windows 8. There seem to be some systems that use Windows UEFI to rein-able some things or other things. We really do not know how Vendors are doing thing yet.

Then some users find they have one application they really do not find a good equivalent in Ubuntu or some game that is Windows only and want to reinstall Windows. 

If you want to just install Ubuntu you can but I would fully back up all Windows partitions including efi, recovery and the main install. Not sure if Windows hides some serial numbers in the MSR like they do with the space after the MBR but before the first partition in MBR partitioning.  

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by Amithiel on 2012-12-21
> **oldfred said:**
> Not sure with Windows 8. There seem to be some systems that use Windows UEFI to rein-able some things or other things. We really do not know how Vendors are doing thing yet.

Then some users find they have one application they really do not find a good equivalent in Ubuntu or some game that is Windows only and want to reinstall Windows. 

If you want to just install Ubuntu you can but I would fully back up all Windows partitions including efi, recovery and the main install. Not sure if Windows hides some serial numbers in the MSR like they do with the space after the MBR but before the first partition in MBR partitioning.  

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Yeah that's what i'm affraid off. 
I can't acess the bios in anyway. I can only change uefi settings from within the windows8. its weird.
anyway, i'll figure out. thanks everyone for the info

---

### Post by oldfred on 2012-12-21
There have been several users with issues getting into UEFI/BIOS. 

Some have stange combinations of keys and others have said quick boot makes it almost impossible to hit the key(s) quickly enough.

---

