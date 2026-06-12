---
title: "When installing only my second HDD shows up."
date: 2013-02-15
forum: New to Ubuntu
---

### Post by TheXtreme1 on 2013-02-15
Hia, I'm trying to install Ubuntu via live CD but when I go into the installer only my secondary HDD shows up.

I've looked around and alot of people suggest unplugging it but I have a laptop which makes that more of a hassle.

So, is there any way to disable or stop Ubuntu from detecting my second one and/or detecting my primary?

Or does it not really matter which I install it on?

A little info in case it is needed. I would be installing this alongside Windows 7. My secondary HDD has nothing on it but steam games. I also have a 32 GB Intel Smart Response thingy if that could be used/interfering.


Thanks for any help you guys can provide. And sorry if any of my comments/questions are dumb, never got into any BIOS or OS stuff.

---

### Post by oldfred on 2013-02-16
Welcome to the forums.

That Intel SRT is the issue. It uses RAID and the desktop installer does not have RAID drivers. Some install Ubuntu to SSD, some to hard drive and reimplement SRT. But you have to turn it off and remove the RAID meta data from drive.

May actually be better to install to second drive so you do not mess with the SRT?

Brand of computer does not really matter as it is an Intel standard. Size of SSD is main difference.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
    

Is this a UEFI system? If so you need Ubuntu installed in UEFI mode. Depending on if installing in Windows drive, SSD or data drive will make a difference. Is data drive also gpt?

---

