---
title: "New to Linux(Grub and hardware issues?)"
date: 2017-08-28
forum: New to Ubuntu
---

### Post by 1skylar on 2017-08-28
I am new to Ubuntu and my father convinced me to build a computer using all fresh components and to try ubuntu to see all of the features available. I am having a problem installing Ubuntu.

Corsair case
Asus ROG STRIX z270 LGA1151 DDR4 atx mobo, on board wifi, paired with an i5 7500 7th gen kaby lake
Asus ROG STRIX 1070 8gig 
Crucial 525g m2 ssd and a Hitachi 2tb hard drive
EVGA Power supply 
Corsair AIO cooler

I got a live usb of Ubuntu 16 from a vendor on amazon and I can boot from it fine, I go into the bios to click to boot it, It goes to the yumi multiboot screen with the penguin on it, I then go to Linux distributions and click Ubuntu 16.04.1 desktop amd64. You can then select try without installing or install, among others like advanced options. I usually click try without installing because I read in a post on here that someone did this option and the grub issue fixed for them. As soon as I hit try Ubuntu a black screen with a blinking underscore follows, and then a message saying,

 [      4.068234] nouveau 0000:01:00.0: unknown chipset (134000a1)

It then goes away and then I see the red purple Ubuntu loading screen. Then this appears on the same screen :

.  .  .  .[   18.467320] ath10k_pci 0000:04:00.0: could not fetch firmware file ath10k/QCA6174/hw3.0/firmware-5.bin': -2

Then it goes to the home screen and I am free to browse the "demo" version and connect to a network and surf the web and also install the os (that's why im here after all). I put in my name and password it starts retrieving the files but every single time It gets to the grub part of the install it says unable to install grub in /dev/sda and it does give me other locations to install the bootloader on but every single option I select, ssd,hdd it doesn't matter when I hit ok to install it it doesn't do anything past that point its like I hit a brick wall. 

I have tried to install Ubuntu 17 and 16 on every drive I have including the ssd, hdd and other usb drives and no matter what I do I cannot get past grub. So I started to look at hardware. I called asus and after an hour they tell me that this motherboard I got (listed in specs above) is NOT compatible with Ubuntu. Has anyone else had this issue? Is Ubuntu not compatible with this motherboard like asus said? I don't see why. Are the new kaby lake 7th gen processors incompatible with this OS? This had occurred to me and that's why I thought about trying to try Ubuntu 17. 

Can anyone help me?

Thank you!

---

### Post by oldfred on 2017-08-28
That is a new UEFI system.
So are you booting install media in UEFI or BIOS boot mode.
Not sure if the multi-boot installer you have even boots in UEFI mode, but since new system you really want UEFI.

Lots of details in link in my signature.
Probably better to directly download newer Ubuntu 16.04.3 or 17.04 which have newer kernels & drivers to better support your system.
You also probably need nomodeset to have installer & first boot of install to work with your nVidia card. Only install nVidia drivers from Ubuntu repository or ppa, not from nVidia directly.

             
 Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
           
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
I have a somewhat older Asus Z97, but expect your UEFI is very similar. I had to make multiple changes in Asus UEFI to have to work easily.
      
 Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)
Asus Z97 Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)

---

