---
title: "Live Cd Booting"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by redhat16 on 2012-06-05
Hi everyone, 

I'm brand new to these forums, as i'm just starting to try out ubuntu. I'm thinking about upgrading, and I wanted to live-boot ubuntu from a cd first just to take a look around. I downloaded 12.04 ubuntu .iso and burned the image to a dvd. I then reset my computer and live booted from the cd. everything seems to be working just fine until I get to the screen where it gives me the option to install or to live boot. I also have the language selection on that screen. However, once that loads, I can't go any further. None of the buttons work (live boot, install, etc.). Even though i click the live boot button, my machine just sits there for hours on end until i restart it. Is there something i'm doing wrong? I would really like to try it out before i upgrade, so any help in advance would be greatly appreciated. Thanks!

---

### Post by unibroker on 2012-06-05
> **redhat16 said:**
> Hi everyone, 

I'm brand new to these forums, as i'm just starting to try out ubuntu. I'm thinking about upgrading, and I wanted to live-boot ubuntu from a cd first just to take a look around. I downloaded 12.04 ubuntu .iso and burned the image to a dvd. I then reset my computer and live booted from the cd. everything seems to be working just fine until I get to the screen where it gives me the option to install or to live boot. I also have the language selection on that screen. However, once that loads, I can't go any further. None of the buttons work (live boot, install, etc.). Even though i click the live boot button, my machine just sits there for hours on end until i restart it. Is there something i'm doing wrong? I would really like to try it out before i upgrade, so any help in advance would be greatly appreciated. Thanks!
This might be of help [https://help.ubuntu.com/community/BootFromCD]("https://help.ubuntu.com/community/BootFromCD")

---

### Post by Curtis6767 on 2012-06-05
And there's this, as well: [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

Did you Check the MD5SUM for your CD/DVD? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Your disk could be faulty.

---

### Post by codemaniac on 2012-06-05
> **redhat16 said:**
> Hi everyone, 

I'm brand new to these forums, as i'm just starting to try out ubuntu. I'm thinking about upgrading, and I wanted to live-boot ubuntu from a cd first just to take a look around. I downloaded 12.04 ubuntu .iso and burned the image to a dvd. I then reset my computer and live booted from the cd. everything seems to be working just fine until I get to the screen where it gives me the option to install or to live boot. I also have the language selection on that screen. However, once that loads, I can't go any further. None of the buttons work (live boot, install, etc.). Even though i click the live boot button, my machine just sits there for hours on end until i restart it. Is there something i'm doing wrong? I would really like to try it out before i upgrade, so any help in advance would be greatly appreciated. Thanks!

Hello redhat16 ,

Welcome to the UbuntuForums .
have you tried checking the integrity of downloaded Ubuntu ISO .
The below link might be useful .
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by oldfred on 2012-06-05
Often a video setting or possibly other Boot options.

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
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by redhat16 on 2012-06-05
> **unibroker said:**
> This might be of help [https://help.ubuntu.com/community/BootFromCD]("https://help.ubuntu.com/community/BootFromCD")

I had already exhausted those options, except for the boot parameters. I can't get to the correct screen while booting up.....it goes to the image below....i tried to hit F6 but nothing happened....Ideas? :/



[http://www.sitepoint.com/wp-content/uploads/1/files/2012/04/01.png](http://www.sitepoint.com/wp-content/uploads/1/files/2012/04/01.png)

---

