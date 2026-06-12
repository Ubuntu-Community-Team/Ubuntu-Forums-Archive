---
title: "Mysterious Black and White boxes?"
date: 2012-02-16
forum: New to Ubuntu
---

### Post by SmrtMouth on 2012-02-16
Okay, I'm new to Ubuntu. I've just built a nice custom machine with some decent parts. It has no operating systems on the hard drive. I popped in an Ubuntu 11.10 (x86) CD-R I just made. After Ubuntu loads (purple background with orange dots) I get a screen that looks like a broken television or something. It is filled with black and white boxes. To make sure the disc wasn't flawed, I tested it on my laptop. I also used the check disc feature by pressing F4 when booting into the CD. I've tried disconnecting all USB devices but no luck. I've switched from IDE to AHCI and to RAID. Nothing seems to work. I'm convinced that the graphics card is the root of the problem (nVidia GT 240). There might be some kind of incompatibility issue causing these black and white boxes. I'm on my phone right now so I can't post a picture. Will post one soon though if needed. Help anyone?

---

### Post by oldfred on 2012-02-16
Welcome to the Forums.

If you switched to RAID you may have compounded the problem. If you have hard drive issues later on, you will have to remove RAID meta data. 

With nVidia you need a nomodeset on first boot. Then it will offer to install the nVidia driver and it should work without any issues.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

