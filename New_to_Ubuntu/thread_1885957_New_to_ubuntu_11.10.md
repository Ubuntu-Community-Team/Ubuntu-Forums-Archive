---
title: "New to ubuntu 11.10"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by WinzenFlyer on 2011-11-24
Hello everybody,  
I have been using Knoppix and Ubuntu (10.4, 10.10, 11.4) besides Windows for the last half year approximately (in LIVE mode) and now I ordered a pack of 11.10 CDs from Canonical because I decided to install it on my hard drive. 

Now I just put in one of the CDs and started up in LIVE mode to look how it looks like and if it accepts my TP-LINK TL-WN721N WLAN USB adapter. It does, but this time it is a bit strange. On the previous Ubuntus, the green light in it just was steady all the time while idling. When accessing a website or when it was downloading, it began to flash rapidly.  

Now it flashes even while idling, like six times with a break of a few seconds in between. When I use *xterm* and *ifconfig*, I can see that while flashing about 74 bytes are transmitted and 84 bytes are received. Can it be that this is just the normal "talk" between router and WLAN stick to keep the connection up?

 Also, what do I have to do when I am installing ubuntu to the HDD? I read that there are some security advices to follow, which are these (IIRC, automatic updates are important, is that correct)? 

Best Wishes, 
WinzenFlyer

---

### Post by 3rdalbum on 2011-11-24
> **WinzenFlyer said:**
> Now I just put in one of the CDs and started up in LIVE mode to look how it looks like and if it accepts my TP-LINK TL-WN721N WLAN USB adapter. It does, but this time it is a bit strange. On the previous Ubuntus, the green light in it just was steady all the time while idling. When accessing a website or when it was downloading, it began to flash rapidly.  

Now it flashes even while idling, like six times with a break of a few seconds in between. When I use *xterm* and *ifconfig*, I can see that while flashing about 74 bytes are transmitted and 84 bytes are received. Can it be that this is just the normal "talk" between router and WLAN stick to keep the connection up?

This sounds like the normal 'talk' between computer and router and nothing to worry about. Sometimes the driver for the device changes a little bit between Ubuntu versions to make the light perform a little differently.

> Also, what do I have to do when I am installing ubuntu to the HDD? I read that there are some security advices to follow, which are these (IIRC, automatic updates are important, is that correct)?

By default, Ubuntu will check behind-the-scenes for new updates. It will put a red exclamation mark icon on your top panel when there are security updates, or an orange one when there are just bugfix updates. Clicking on the little exclamation mark and choosing "Show Updates", then clicking the Install updates button, will keep everything up-to-date.

The Ubuntu installer will pretty much guide you through everything you want to do. If dual-booting between Windows and Ubuntu you should use Windows to defragment the Windows partition first as it will be quicker than getting Ubuntu's installer to do it. Just read the instructions in the installer carefully and **make sure all your data is backed up before installing**. Probably nothing will go wrong, but with any partitioning operation there is a small risk of data loss. How small depends on the current state of the disk and filesystems.

---

### Post by fantab on 2011-11-24
Yes, during installation Ubuntu will check for Updates and install those updates provided there is internet connection during install process. 

Personally, I never stay connected to Internet during installing Ubuntu. I don't like the idea.  I will first install it as it is on the CD. Then I connect to INTERNET, check for updates with UPDATE MANAGER and install them. Only then will I proceed with other customizations. I feel safer this way. 

Are you planning on Dual-Boot with Windows? If you are then, follow **3rdalbum's** advice. I will suggest use [**GPARTED LiveCD**]("http://gparted.sourceforge.net/livecd.php") to move, resize, format and create partitions. Also don't forget to create a small SWAP partition about the size of your RAM or 2GB is enough.

And remember to use "**Something Else**" option to allocate space when installing Ubuntu. This option will give you more control over installation and managing your partitions.

Some USEFUL LINKS:
[**LINK I**]("http://members.iinet.net.au/%7Eherman546/index.html")
[**LINK II**]("https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")
[**LINK III**]("http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html")

---

### Post by mastablasta on 2011-11-24
here is how install process will look like (pic by pic): [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
as you can see, you can choose to install updates during install or not.
 
if you plan to use the whole disk you can just leave the installer to partition it automaticly. it does a preety good job.

---

### Post by WinzenFlyer on 2011-11-24
Thank you for all your answers!

I am planning to install ubuntu alone, that was mostly brought forward due to a M.Sc. student at university, who told me "I am using Linux for working and Windows only for gaming". And thus I decided to go for ubuntu :)!

The only things to do would be to have ubuntu running with a Canon Pixma iP3600 printer and with the Arduino Microcontroller (but for the latter one I have found a good tutorial and also saw that there are several threads on here dealing with Arduino and ubuntu).

---

