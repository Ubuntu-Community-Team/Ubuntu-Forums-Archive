---
title: "Ubuntu Install Issue on Acer Aspire 5050"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by rTxx on 2012-09-12
I have been trying to install Ubuntu 12.04 on to an Acer Aspire 5050 laptop. I am using the 64 bit Live CD method.  I downloaded the ISO from the Ubuntu site.

I plan to replace the Windows Vista that was on the computer.  There was a problem with the Windows installation which I took to being a bad HDD.  I booted into Ubuntu Live CD with the HDD installed with absolutely no problem (except it took about 10 minutes to get to a desktop), so I assumed that installing would be easy.  When I tried, the install failed, which again I put down to a bad HDD.

I took out the SATA HDD and replaced it with a SATA SSD and tried to boot the Live CD. I get the BIOS boot messages, then the screen goes blank and nothing happens, although the HDD light is on continuously.  The Live CD does not seem to be being accessed.  If I look in the BIOS configuration screen, the SSD seems to be detected okay.

If I take the SSD out of the computer I can boot the Live CD.  Does anyone have any advice as to what I might try to get this working?

Many thanks.

---

### Post by rTxx on 2012-09-13
Here is an update.  I left the laptop having attempted to boot and came back over an hour later and it has actually booted into Ubuntu!  However, when I try to install on the SSD it says there is no space (or more specifically there is not 8.6Gb of unused space).  The SSD capacity is 64Gb.  I formatted it NTFS one partition only.  There is no data on the SSD.  I cannot see any sign of the SSD from Ubuntu's equivalent of Explorer, but I could be looking in the wrong place.

I think the basic issue is that Ubuntu cannot detect the SSD despite the BIOS seeing it.

Is anyone able to help with this new information?

Many thanks.

---

### Post by androssofer on 2012-09-13
> **rTxx said:**
> Here is an update.  I left the laptop having attempted to boot and came back over an hour later and it has actually booted into Ubuntu!  However, when I try to install on the SSD it says there is no space (or more specifically there is not 8.6Gb of unused space).  The SSD capacity is 64Gb.  I formatted it NTFS one partition only.  There is no data on the SSD.  I cannot see any sign of the SSD from Ubuntu's equivalent of Explorer, but I could be looking in the wrong place.

I think the basic issue is that Ubuntu cannot detect the SSD despite the BIOS seeing it.

Is anyone able to help with this new information?

Many thanks.

are you only wanting ubuntu on the machine? or a dual boot with windows?

anywho.. when you boot into the live CD, click the ubuntu logo on the top left and search for 'gparted'

this will give you info on the partitions on the ssd. see how much is used by the ntfs partition and how much free space is left...

ubuntu cant install onto ntfs. so it will look for space that isnt in ntfs.. 

if you only want ubuntu on the machine, then delete you ntfs partition and run the install, it should do the rest for you. 

If you want to dual boot, then let us know and we can help with it..

---

### Post by rTxx on 2012-09-13
I only want Ubuntu on the system.  No Windows - had enough of that on  the laptop.  I tried searching for gparted but 40 minutes later it was  still manically not finding it! I don't think Ubuntu can see the SSD in  any event.  My experience previously is that the drive would appear as  mountable even if it was NTFS formatted or has this changed?

Since  writing the above paragraph, I gave up the search for gparted, and  switched the machine off. I've removed the SSD and deleted the partition  on it from another machine, and I have tried re-booting the machine  from scratch with the blank SSD in it.  I re-booted at about 17:45.   After the boot messages from the BIOS, there was activity reading from  the Live CD and the screen went black apart from a flashing  terminal-like cursor in the top left corner.  The screen has remained  like that ever since.  It is now 19:15, one and a half hours later...

I really believe this is an issue with Ubuntu and the SSD.

---

### Post by mips on 2012-09-13
First make sure you have AHCI enabled in your BIOS.

In ubuntu you can open the terminal and run 'sudo gparted' if gparted is not installed you can install it from the cd with 'sudo apt-get install gparted'

---

### Post by rTxx on 2012-09-13
Thank you for the suggestion.

The BIOS configuration settings are very simple on this machine. AHCI is not one of the options available.

---

### Post by Bashing-om on 2012-09-13
Pardon me for intruding..know that this is frustrating to no end.

Gparted (post #3)..boot the live/install cd->try ubuntu->dash-> type gparted into the dash search bar...Gparted is available ! ...

ssd : UEFI ?
[http://ubuntuforums.org/showthread.php?t=1974392](http://ubuntuforums.org/showthread.php?t=1974392)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

see if these links help.
[INDENT]just trying to help ==>BDQ

[/INDENT]

---

### Post by rTxx on 2012-09-14
Thank you for your suggestion.

The BIOS on this machine is from around 2006.  I am unclear if you are saying that the SSD is incompatible with the BIOS and that is the issue, or if you suspect that Ubuntu is booting from the Live CD in the wrong mode: UEFI instead of MBR.  I do not think UEFI is an option on this board.  The conflict only seems to occur (from what I have read at the links you kindly gave) if UEFI is an option but is not being used?

Also this is NOT a dual boot machine - the SSD has no partitions defined and is ready to accept a completely Other OS-free machine.  ie. I plan to install only Ubuntu and there is no sign of a previous Windows system anywhere to be seen on the SSD.

---

### Post by androssofer on 2012-09-14
> **rTxx said:**
> Thank you for your suggestion.

The BIOS on this machine is from around 2006.  I am unclear if you are saying that the SSD is incompatible with the BIOS and that is the issue, or if you suspect that Ubuntu is booting from the Live CD in the wrong mode: UEFI instead of MBR.  I do not think UEFI is an option on this board.  The conflict only seems to occur (from what I have read at the links you kindly gave) if UEFI is an option but is not being used?

Also this is NOT a dual boot machine - the SSD has no partitions defined and is ready to accept a completely Other OS-free machine.  ie. I plan to install only Ubuntu and there is no sign of a previous Windows system anywhere to be seen on the SSD.

is the CD definitely the 1st boot option? if you can, get a usb stick and make a bootable usb drive. and boot ubuntu from that..

---

### Post by rTxx on 2012-09-23
I could not get this to work with the machine as configured.  I removed the SSD and replaced it with a conventional 60Gb HDD (second hand/used) and I have now managed to install Linux Mint on the machine and it is working quite nicely, I think.  My daughter seems very happy with it (she is the primary user of that particular machine) and says it is far more responsive than when it had Windows Vista on it.

Thanks to everyone who made suggestions.  I think my instincts were right that I simply could not get Ubuntu to work with the SSD.  Now to find somewhere to use an SSD... ;-)

---

