---
title: "Please help get me off of windows!!!"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by fubarator on 2013-02-11
I have been trying for two days to get Ubuntu running properly on my laptop. My laptop is a Dell "Inspiron" 1420. It has an internal "Broadcom wireless" BCM4312 wireless card. So here is the problem, I cant get Ubuntu to install the drivers for and recognize my card unless I'm running it off of my memory stick. I have it installed on my computers internal hard drive as a dual boot with Vista. I also have a bootable memory stick running Ubuntu. If I boot off the thumb drive, I can go through system settings to software, to "other drivers" and I can click the broadcom driver, click "apply changes" and it installs the drivers and recognizes my wireless card and I can connect to my wireless. When I boot from the hard drive and go through the same process it never installs the driver and the selector goes back to "don't use this device". I have uninstalled and re-installed Ubuntu three times trying to resolve other problems related to this wireless issue, and I really don't want to have to do it again. Can anyone PLEASE help me get this worked out so I can stop using Windows????

---

### Post by offgridguy on 2013-02-11
You may find something to help at this site.

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by |{urse on 2013-02-11
[http://ubuntuforums.org/showthread.php?t=2107510](http://ubuntuforums.org/showthread.php?t=2107510) <-- You'll find what you need here.

---

### Post by fubarator on 2013-02-11
ok so an update... I checked and have been researching on the site first mentioned. Low and behold there is my exact problem. The LiveDisc/LiveUSB files have the necessary drivers, some full install do not. Now my problem is how to get the drivers opened in Ubuntu. Thanks for the quick responses guys, and I'm gonna chack out the other link and ponder how to get the drivers opened in Ubuntu since I have absolutely no way to connect to the internet from it. My access is mobile HotSpot through Verizon... No way to attach a Ethernet cable to my phone ... :(

---

### Post by fubarator on 2013-02-11
> **|{urse said:**
> [http://ubuntuforums.org/showthread.php?t=2107510](http://ubuntuforums.org/showthread.php?t=2107510) <-- You'll find what you need here.

I have no available Ethernet connection and no way to acquire one... is there not a way I can install the drivers through windows? Or at least download them to a file accessible through Ubu?

---

### Post by offgridguy on 2013-02-11
> **fubarator said:**
> I have no available Ethernet connection and no way to acquire one... is there not a way I can install the drivers through windows? Or at least download them to a file accessible through Ubu?
Do you have access to a public facility, like a library where you
could use the internet connection?

---

### Post by fubarator on 2013-02-11
> **offgridguy said:**
> Do you have access to a public facility, like a library where you
could use the internet connection?

the Library where I live only has access through WiFi or their computers. No access to plug mine up through their ethernet cables... I can access my own internet connection, just through windows, or through ubuntu booted from the USB drive. Can I access the needed file through either one of those methods and save it to a file or another thumb drive for later access through my installed version of ubu?

---

### Post by Mark Phelps on 2013-02-11
Sorry, but you can't install the drivers referenced in the linked thread because they are contained in a ".deb" file -- which Windows can not understand.

The info from ubfan1 (in the linked thread) mentions the following:

> On the live installation media, in directory /pool/restricted/b there is a package of Broadcom drivers:
bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_i386.deb
Try installing this, the (STA aka wl) driver comes with firmware embedded. The b43 driver you are trying to use is the one needing external firmware.

You should be able to use Nautilus to get to that file in the installation media, and once there, execute the .deb file.

---

### Post by fubarator on 2013-02-11
> **Mark Phelps said:**
> Sorry, but you can't install the drivers referenced in the linked thread because they are contained in a ".deb" file -- which Windows can not understand.

The info from ubfan1 (in the linked thread) mentions the following:



You should be able to use Nautilus to get to that file in the installation media, and once there, execute the .deb file.

when I access that file through Ubuntu it takes me to the software instalation center and tells me I have to download 1.3MB of data and the install button is greyed out... I have no internet connection though Ubuntu to access the data I need to download for the driver....

---

### Post by fubarator on 2013-02-11
UPDATE: This is making my left eye twitch at an incredible rate. My original problem with windows is it wouldn't accept the drivers for my DVD/RW drive. Ubuntu picked THAT up with absolutely no problem, no driver install even needed... Just no internet. Now Windows is picking up my DVD/RW drive, with no modification from me... just booted up an installed the drivers ive been trying to install for six months. So can I re-install Ubuntu (later version) or something? This is the most irritating thing ihave ever dealt with...:(:(:(:(:(

---

### Post by fubarator on 2013-02-11
bump

---

### Post by offgridguy on 2013-02-11
I notice you never did say which version you are using, newer is not always better.
I prefer ubuntu 12.04 over 12.10.

---

### Post by fubarator on 2013-02-11
> **offgridguy said:**
> I notice you never did say which version you are using, newer is not always better.
I prefer ubuntu 12.04 over 12.10.

sorry it is 12.10 but I am in no way attached to the latest and greatest. Can I downgrade to 12.04 and do you think that would cure my issue?

---

### Post by offgridguy on 2013-02-11
> **fubarator said:**
> sorry it is 12.10 but I am in no way attached to the latest and greatest. Can I downgrade to 12.04 and do you think that would cure my issue?

Technically there is no downgrade,  you would have to do a new
install.

---

### Post by fubarator on 2013-02-11
Ok So problem solved. I am on my fresh sparkly 12.10 Ubu... I called everyone i knew until I found someone with a wireless router that could handle more than one connection, grabbed a 3 foot long CAT5 cable and went to their house and made the ten second download of the above mentioned drivers and *poof* now I have wireless. This was such a bunch of ridiculous, but a lot of it was self inflicted. Thanks offgridguy for the help and everyone else. Now on to enjoying my fully working version of Ubu. Thanks again for everyone's help.

---

### Post by fubarator on 2013-02-11
And actually I need to Edit this... I didnt ACTUALLY use the above links, however I accessed the same information by reading the information from the first link that was posted. I'll summarize that information for anyone else having this problem:

First I used a LiveUSB that I made following the instructions at Unbuntu.com/download. I also HAD to connect through a CAT5/ETHERNET connection. I actually had to go to a friends house because my intent connection is a mobile hotspot and I have no way to manually connect through a CAT5 cable, so... All of that being said, this is how I solved my Broadcom BCM4312 wireless card recognition issues.

If you plug the LiveUSB drive into the computer and boot into Ubuntu you can access the files on the thumb drive through the home folder. So once you open the thumb drive go to-"pool/restricted/b/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb"

once you run that file it will take you to Ubuntu Software Center where you will have to download a small file, just agree to all. Once it stops the download and subsequent installation of the drivers, you will need to go to the upper right corner to the power button drop down menu, then go to system settings, software sources, and then click on the last folder labeled "Aditional Drivers. Then click the dot next to the driver listed, then apply. Once it finishes the install, Reboot and log back in and the wireless icon should be populated with all available wireless networks. And mine was actually there before the reboot but i allways reboot after changes like driver installs and such. Anyway, I hope this help someone later, and saves them some of my frustrations. Thanks Everyone here for the help again.

---

### Post by mastablasta on 2013-02-12
you probably could have used AptonCD with live USB key to donwload the necessary packages: [http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html)
 
also synaptic can be used to download the necessary packages.
 
or simply you can do it manually from the browser.
 
unfortunatelly keryx project went commercial first and now it seem to have died.

---

### Post by fubarator on 2013-02-12
> **mastablasta said:**
> you probably could have used AptonCD with live USB key to donwload the necessary packages: [http://aptoncd.sourceforge.net/download.html](http://aptoncd.sourceforge.net/download.html)
 
also synaptic can be used to download the necessary packages.
 
or simply you can do it manually from the browser.
 
unfortunatelly keryx project went commercial first and now it seem to have died.

Yeah, The issue became access to the internet through ubuntu. My only source of internet connection is a mobile hotspot and i couldnt plug up an ethernet connection to it. Once I got a connection in Ubuntu It was littleraly a ten second process to fix the card recognition issue. I had the files I needed on USb to download, but had to have internet to DL them... Thanks again everyone

---

