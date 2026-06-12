---
title: "New install - Ubuntu 16.04.4 - New GTX 1050 2gb graphics - Install display issues"
date: 2018-03-23
forum: New to Ubuntu
---

### Post by jameswilles on 2018-03-23
Hi all, looking for a little clarification if possible....

I've got a new system 

i5 3.1GHZ
4GB ram
500gb HDD
Windows 10

I wanted an Ubuntu machine so I pulled the 500gb HDD out and installed a new 1TB drive

then I installed my new GTX 1050 2gb graphics card.

booted up the system with the Ubuntu installation CD in the drive using the HDMI output from the graphics card.

the display comes up with the first splash screen (Dell Optiplex) then shows that it's booting from the cd, the Ubuntu logo pops up. then my screen switches off and says no signal input. so I cant proceed from there.

so my question is: 

Should I take the graphics card out. 
Install Ubuntu using the regular Intel HD graphics then install the graphics driver I need for the GTX 1050. 
Switch off the system. 
Physically put the card back in
then reboot?

does that sound right? or should Ubuntu just start with a driver that the 1050 can use in the first place?

thanks in advance. if you need me to give any more info I'll do my best to find it....

---

### Post by jameswilles on 2018-03-23
Does anyone have any ideas ive? been trying all day with no help or success... still same issue. im still trying now :confused::(

---

### Post by oldfred on 2018-03-23
A few have had to remove nVidia card, change settings in UEFI to use Intel Graphics, install & then install nVidia driver from repository.
But most can use nomodeset boot parameter to get into low graphics, both for install & then after install or until proprietary driver installed.
Since very new nVidia card you may want to install ppa to get very newest drivers. Do not install directly from nVidia.

Are you booting in UEFI mode?
What brand/model system. Some also need other parameters.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710) 


       17.10 defaults to wayland where nvidia's driver don't work 

      
 [https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959](https://ubuntuforums.org/showthread.php?t=2385770&p=13742959#post13742959) by 1fallen
> EDIT: This seems to work for my card here, instead of using "nomodeset" I am using this "nogpumanager"
And I have to watch carefully any changes made to "/etc/X11/xorg.conf" 
   nVidia Must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

