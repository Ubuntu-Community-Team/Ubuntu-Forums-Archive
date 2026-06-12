---
title: "cant run live or install from usb 2gb stick"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by toebertgg on 2011-10-03
so im trying to do a fresh install or even run live. i have a 2gb usb stick w/ ubuntu 11.04 on it. i get to the main menu pick wich one i want to run then dats its. it freezes up. any help is greatly apperciated. first time user here and lookin forward to contiue using..

---

### Post by thatguruguy on 2011-10-03
I'm having a hard time understanding you.

What kind of computer are you using? What main menu are you referring to?

---

### Post by Quackers on 2011-10-03
Welcome to UF :-)

How much ram do you have?
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also check the cd/usb for errors by pressing any key at the first purple screen when booting. Choose your language then on the next screen select "check for errors". 
Any error at all means that the iso needs to be installed again.

---

### Post by toebertgg on 2011-10-03
[http://www.fryssupport.net/gq6310.cfm](http://www.fryssupport.net/gq6310.cfm)
 
this is the type of pc im using. sorry for the confusion. i get the pc to boot off usb. it gives me the option to run live or install. its starts thn med way through it just stops.

---

### Post by toebertgg on 2011-10-03
> **Quackers said:**
> Welcome to UF :-)
 
How much ram do you have?
Have you checked the md5sum of the downloaded iso file?
 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
Also check the cd/usb for errors by pressing any key at the first purple screen when booting. Choose your language then on the next screen select "check for errors". 
Any error at all means that the iso needs to be installed again.
 
ill check this once i get to another pc then i'll up date everyone.

---

### Post by oldfred on 2011-10-03
If you have not added memory 512 is on the low end of what works. A lighter weight versions may be more reponsive.

I have a newer nVidia (9600) but have to use nomodeset on CD, USB or first boot until I install the nVidia driver. Yours may need the older driver.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by ubun2geek on 2011-10-03
I would try using ubuntu 9.10
I had to do that on a super old PC. (not saying anything about yours.:) )

---

### Post by ajsoulmate on 2011-10-04
> **OpenOffice.org said:**
> I would try using ubuntu 9.10
I had to do that on a super old PC. (not saying anything about yours.:) )

9.10 is not supported anymore as far as I know.

---

### Post by ajsoulmate on 2011-10-04
> **toebertgg said:**
> [http://www.fryssupport.net/gq6310.cfm](http://www.fryssupport.net/gq6310.cfm)
 
this is the type of pc im using. sorry for the confusion. i get the pc to boot off usb. it gives me the option to run live or install. its starts thn med way through it just stops.

> System Specifications

CPU: AMD Sempron 3200+ 1.8Ghz, 128KB Cache
Motherboard: ECS GeForce 6100SM-M
Chipset: NVIDIA GEFORCE 6100/NFORCE 405
Devices
120 GB SATA, 7200rpm, 8 MB cache
16X/18X/6X/8X/4X DVD+/-R/RW Burner
Memory Card Drive
Memory: 512MB SDRAM, DDR2-533MHz
Operation System: Windows Vista Basic with DVD Playback
Accessories Box
PS2 optical mouse w/ scroll wheel
PS2 Multimedia Keyboard w/ 6 hot keys
2 Stereo Speakers
User Manual
Quick Setup Sheet
Full OS Restore DVD
Port Connectors
2x PS/2 Ports
1x VGA Port
6 x USB ports (2 front, 4 back)
2 Set Audio Port (front and back)
1x Serial Port
1x Parallel Port

Do you take an advice from a new Linux User?
I have Sony Vaio Laptop with 1GB RAM and I didn't go for Ubuntu 11.04, I installed Ubuntu 10.04 using Plop (my CD drive stopped working :( ) and it works perfectly.
I have learned that there are some other lighter OS but haven't tried them yet. I guess I'll go for it some time later.

Hope this will help!

---

### Post by toebertgg on 2011-10-04
thats what i have been doing for the last couple of days researching light weight ubuntu's especially for usb stick. have problems understanding:what programs come w/ them?if i need internet to download and install them.

---

### Post by ajsoulmate on 2011-10-04
> **toebertgg said:**
> thats what i have been doing for the last couple of days researching light weight ubuntu's especially for usb stick. have problems understanding:what programs come w/ them?if i need internet to download and install them.

I don't care about the default programs as long as I do have an internet access and can install whatever I want :)

---

### Post by ajsoulmate on 2011-10-04
There you go:
[http://distrowatch.com/search.php?category=Old+Computers&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Old+Computers&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&status=Active)

List of some OS for old machines :)

---

