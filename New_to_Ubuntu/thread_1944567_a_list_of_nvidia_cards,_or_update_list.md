---
title: "a list of nvidia cards, or update list?"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by the.phantom on 2012-03-21
older computer is getting just a bit old
so working on building a 3 core amd and want a nvidia card for it 
i have googeled a lot and close as i could come was this !

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

and it is just a bit too old !
i want to just use the "addition drivers" to easly install it, that is my main concern !

i have one system with a 9500gt and like it, but damn hard to find anymore
and don't want to spend the $ and find out i have to install drivers myself ( yes i am lightweight on linux ! but not ashamed as "it just works")
i've read about troubles with 220,420,520 series and very worried
any advice on a good working pci express card?
thanks

my usual way is to google " nvidia 9500gt and ubuntu" and go through several pages
but working video cards don't have post
links show up on sites that do benchmarks, but they overclock and are good with software !

thanks

---

### Post by HiImTye on 2012-03-21
just check the list of supported devices on nVidia's page with Ubuntu's 'current' nVidia driver

---

### Post by Frogs Hair on 2012-03-21
Eight and nine and newer series Nvidia cards should work with Nvidia current drivers found in additional drivers . Some of the older cards can be found at New egg and Tiger direct . Options change depending on where you live.

---

### Post by the.phantom on 2012-03-21
thanks got the great tips !
i did find if you go to 
usr/share/doc/nvidia-current/readme

on your current system 

and scroll about 1/2 through it you find a list of what it supports ;-D

i can do that on my latest system and find a card in my price range as won't be that old a list

all the reading said to stay away from the 220,420,520 series cards
but they show up on the list

so happy me !
D

i will close this out but leave it open for a bit in case i made a bobo with that file i found ;-D

---

### Post by grahammechanical on 2012-03-21
I am using the Geforce GT220 and I have never had a problem getting a driver from Additional Drivers and I have never found any issues with the driver. At present it is 295.20.

Regards.

---

### Post by mal1958 on 2012-03-21
There is a list of nVidia cards that are supported by the latest release of the drivers [[COLOR="RoyalBlue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1771806")  Hope this helps...

---

### Post by oldfred on 2012-03-22
With just about all nVidia cards you will have to use the nomodeset boot parameter for liveCD or first boot.

This is a comparison of video cards (Windows) but gives an idea of the differences. See last page = Graphics Card Hierarchy Chart March 2012, and to see real performance change you need to go at least two groups up. 

[http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html](http://www.tomshardware.com/reviews/gaming-graphics-card-review,3107.html)

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

