---
title: "Ubuntu boot error, no video signal after grub"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by Maohu on 2012-12-14
Hi guys, I'm very new at this so bare with me...

So I'm using ubuntu 12.04 installed on a 1TB external hdd.
After logging into ubuntu, I updated the video drivers (using home desktop with ATI, at work its nVidia) and after the reboot, i can no longer boot? (not sure if this is right description)

So I get to grub (is that like the boot menu?) and then I try the first option which is normal boot (as opposed to recovery). Then I get the purple ubuntu screen, a screen of text and before I can read it, the monitor loses video signal.

I'm not sure what I can do at this point, I really need to get back on to work :(

Any help is appreciated! thanks!

---

### Post by debodas on 2012-12-14
Yes, grub is the boot loader.
The issue will be the video drivers you loaded, ubuntu (actually linux in general) can be pretty picky about these.

Edit - deleted my advice, oldfred's is better.

---

### Post by oldfred on 2012-12-14
Some older info on using two differnt video systems.

       Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

### Post by Maohu on 2012-12-14
Thanks for the responses,

@kingnick42, when I get to the root shell prompt, after entering sudo apt-get purge nvidia*
I get
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

---

### Post by Maohu on 2012-12-14
So after unlocking the read only mode I tried sudo apt-get purge nvidia* and it was fine and I got it to boot, but it quickly resulted in the same signal loss for my monitor... although this time it showed the cursor :D

After I tried again by removing ati as well with sudo apt-get purge ati*, and an error occurred..

The following packakes have unmet dependencies:
 libc6 : Depends: libgcc1 but it is not going to be installed
            Depends: tzdata but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by he ld packages

I think the "he" is the and is just a typo lol...

Also @oldfred, How can I go into Reconfigure graphics through recovery mode? And thanks for those links!

---

### Post by oldfred on 2012-12-14
I do not know about AMD/ATI, but with nVidia I always have to use nomodeset on first boot until I have nVidia driver installed.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Maohu on 2012-12-14
I just tried booting with the nomodeset option, still not working... is there another way to completely remove al ati installations? I think thats the issue... (i've already tried sudo apt-get purge)

---

### Post by Maohu on 2012-12-14
Also when I try the safe graphics mode, it tells me "no monitors" or something along that lines.

Another error that might help is 
rt2800pci_mcu_status error: mcu request failed no response from hardware
I get that when restarting from root terminal

---

### Post by oldfred on 2012-12-14
I only have some links on AMD/ATI.

       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

    
       [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
[http://ubuntuforums.org/showthread.php?t=1558406](http://ubuntuforums.org/showthread.php?t=1558406)

---

### Post by Maohu on 2012-12-15
OMG IT WORKS!!!!!!!!!!!

Haha thanks oldfred, it seems that the link [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide) worked for me (followed the Removing catalyst/fglrx section)

Now i'm on no graphic drivers and things are awkward but i can work on this! I"M SAVED!!!

Thanks :)

---

