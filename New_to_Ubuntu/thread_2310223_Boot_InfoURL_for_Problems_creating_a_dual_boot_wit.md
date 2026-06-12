---
title: "Boot InfoURL for Problems creating a dual boot with 12.4.5"
date: 2016-01-17
forum: New to Ubuntu
---

### Post by john.dardenne24 on 2016-01-17
I have an old XP dell i-8600 laptop with 750MB ram that I am trying to use as my backup computer. I decided that Windows XP is way too slow so I am dual booting with XUBUNTU 12.4.5 since the Dell I-8600 is a non-PAE computer. The first time I installed XUBUNTU I didn't wait long enough or the computer lost its connection to the router because after 5 hours I did a force shutdown. I then used an emergency Windows Boot disk to boot up XP. In XP I wipe two drive partitions the 40GB XUBUNTU 12.4.5 OS and a second 750 MB partition unknown content. I then tried to reinstall the XUBUNTU OS and got the same non-booting computer "error: out of disk.                 grub rescue>". I then followed the prompt for "Boot Repair" using the second option (loading LIVE USB and installing BOOT Repair inside of XUBUNTU) since this is a non-PAE laptop. _**Here is the the Boot InfoURL**_ -> [http://paste.ubuntu.com/14541267/](http://paste.ubuntu.com/14541267/)

If I have to wipe the computer disk and reinstall the XP OS , SP1, SP2 and SP3 followed by XUBUNTU 12.4.5 I am willing to do that. I was just wondering if there is a shortcut to fixing my problem.

BTW: I have reinstalled Windows XP several times to try and speed it up. Before the latest iteration the average virtual memory usage with Firefox opens was 1.4 GB. I had to wait tens minutes for the computer to boot and open a web page. When I reinstalled to SP3 and ignored ALL windows XP security patches the computer is idling at 0.250 GB and .400 GB with firefox. The computer is actually now a computer! It looks like 500 MB of memory is taken up by MS Windows security patches! The other 500MB is other stuff like dropbox, chrome, open office and all the rest that want to "open fast" by always staying open at the expense of memory.

Thanks for any help.

John D'Ardenne

---

### Post by oldfred on 2016-01-17
Out of disk can be related to IDE or AHCI setting. And if system is old enough you may not have the AHCI setting for your hard drive in BIOS. But with AHCI on XP will not boot.

With some old IDE systems, all boot files must be seen by BIOS in the first 137GB of a hard drive. Those old systems did not have large drives, so not an issue, but if larger drive added it could be.
Work around was to either have smaller / (root) fully in the first 100GB or so and separate /home or a separate /boot partition at beginning of drive.

With nVidia you may need nomodeset, until you install the correct legacy driver for your nVidia card. That driver is in Ubuntu repository, do not install from nVidia directly.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by john.dardenne24 on 2016-01-19
Thanks oldFred,
Your idea about BIOS not recognizing larger hard drives was correct. The XUBUNTU was past the limit. When I installed XP it would only let me make a drive 105 GB so I wipe the hard drive and started over. The XP partition occupied the first 45 GB. I installed XP. Then I built a 60 GB data drive at the end of the drive to force the XUBUNTU partition to be from 45 to 93 on the hard drive and voila. I have a dual boot computer! Many thanks.

John D

---

