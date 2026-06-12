---
title: "problems with running live iso from usb or cd on dell d620"
date: 2013-11-28
forum: New to Ubuntu
---

### Post by bschilke.biz on 2013-11-28
I found an old dell d620 (1 GB Dual core CPU, 1GB RAM, 40GB HD) that my wife had been issued for work years ago that I fired up and got the below error message.*

Stop: c0000218 {Registry File Failure} The registry cannot load the hive (file): \SystemRoot\System32\Config\SOFTWARE or its log or alternate


I thought it would be a good excuse to try running a live version of Ubuntu (ubuntu-5.10-live-i386.iso) from a usb stick but I couldn't get it to run (although I now want to install permanently if I can). I changed the order of operations among devices to look at usb first but no luck. I then tried using a cd and didn't have any success there either. (in all cases the usb stick or cd is ignored and a I get a message about no bootable device being found)*

My suspicion is the bios is too low a version, I can't find the link but someone had a similar problem and solved it by upgrading to bios revision A10. I've tried that using a utility but got a file size error (I can provide links at a later point, in writing this on my phone).*

I could live with never booting into the installed windows xp, but does anyone think the above registry issue is causing me problems? In my mind the registry isn't involved until windows starts to load.*

---

### Post by heir4c on 2013-11-28
Ubuntu 5.10 is very very old and not supported any more.
Use the newer version (12.04) 
Or better: use Lubuntu or Xubuntu for better and faster performance:
[http://www.lubuntu.net/](http://www.lubuntu.net/)
[http://xubuntu.org/](http://xubuntu.org/)

Use unetbootin in Windows or in Ubuntu to make the live-usb:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

For creating a cd/dvd you must burning it as "image" NOT as "data" at the lowest speed you can get (best is 2x,4x or 8x).

In the BIOS you can Enable the support for USB.
And choose in the BOOT Tab the USB-HDD or USB-FDD or if there is not than choose the Hard Disk and click Enter. Maybe under that there are more options. (You must put your usb inside before booting your computer.)

---

### Post by DuckHook on 2013-11-28
Hi bschilke.biz and welcome to the forums,

I run both the bigger brother of your machine, a D820, and an even older sibling, the D600. No matter the age of the BIOS, it should be able to boot from USB or DVD. There is one possibility that I ran into only once--especially if it's a work machine: is the BIOS locked? If so, then it won't boot from anything except HDD. However, as I recall, you would not have been able to even enter the BIOS if it were locked. Since you've already mentioned that you did so, I doubt that this is the problem.

Next possibility is that both USB and DVD were burned improperly. How did you burn them? Some people simply copy the ISO file over, which won't work. ISO needs to be burned as an image. A proper result will yield a whole bunch of files with proper directory tree structure on the burned-to medium. The wrong way yields one big file called "ubuntu-xxxx.iso" or similar. Most will also use the utility *unetbootin* for a bootable USB.

I'm assuming that the version you are trying to boot is a typo. If you are truly trying to use 5.10, then that is probably the problem right there. 5.10 is not even ancient... Jurassic would be closer to the truth, and has been unsupported since--oh--2007? You should be using a current version that is properly patched and updated to plug any security holes and fix the ton of bugs that have been uncovered since '05. Your D620 will run anything up to the current versions, but its graphics chip is somewhat weak and will struggle with the 3D of the Unity desktop. Also, your 1GB RAM will be a limitation for Ubuntu proper. I recommend Xubuntu for this machine. Lubuntu, which is even lighter, would run like greased lightning, but it doesn't look as nice as Xubuntu. You can try it too if you like. LiveDVDs make experimentation easy.

P.S. you are correct in concluding that the XP choke has nothing to do with your boot issues. If you are happy to wipe out XP, I think it's a good idea. XP will be dead on April 2014 and the last thing anyone would want is to be running an unsupported Windows OS--an open invitation to getting owned.

---

### Post by squakie on 2013-11-28
Also, keep in mind that if the optical drive is CD and not DVD, you will either have to use a USB stick or use a slightly older version of Ubuntu (I think pre-12.04) for the ISO image to actually fit on a CD.

---

### Post by mörgæs on 2013-11-28
12.04 is the oldest version of Ubuntu with support. Don't go for anything older.

I agree that X/Lubuntu 13.10 is a better choice. Lubuntu fits to a CD. Xubuntu looks good but 13.10 has an annoying bug regarding sound volume.

Does booting with the USB stick installed and repeatedly hitting F12 give you a menu?

As a last action before erasing Windows it would be good to update the BIOS.

---

### Post by bschilke.biz on 2013-11-28
Thanks everyone for your help.

@heir4c - thanks for the links and the tips on lubuntu & xbuntu.  I think if I can, I might want to install one of these smaller linux distributions so the machine doesn't seem too slow, although I'm not sure if it will be.

@DuckHook - Based on what you & heir4c mentioned, it's clear that I did the 'bootable drive' thing wrong--I just copied it over.  I'll give this unetbootin a try.

I'm not sure about the bios being locked. I *think* I was in BIOS (I was in the very low-level text-based interface where you can view and modify things like the order of boot devices and lots of other options).

re: the version, i was trying to install something close to the age of the laptop to get close to a match of the laptop's and ubuntu's requirements.

@squakie & morgaes:  i will keep in mind the size that i'm limited to on cd.  i think i have a cd player and not dvd, will have to check that.

---

### Post by DuckHook on 2013-11-28
> **bschilke.biz said:**
> I might want to install one of these smaller linux distributions so the machine doesn't seem too slow, although I'm not sure if it will be.You will be much happier with stability and responsiveness with the lighter flavours.> I'm not sure about the bios being locked. I *think* I was in BIOS (I was in the very low-level text-based interface where you can view and modify things like the order of boot devices and lots of other options).That's the BIOS. It was not locked.> ...i was trying to install something close to the age of the laptop to get close to a match of the laptop's and ubuntu's requirements.Your laptop is not that bad. Actually, the CPU is quite good and will run any of today's stuff just fine. You account for the slightly underpowered graphics system by using one of the lighter flavours.

EDIT

***ALERT***
Unfortunately, you WILL run into the chronic Broadcom WIFI issue with that series of Dell Laptops. Thought I owed you a heads-up on that one. You will have to install the system by hooking up the ethernet cable and then following [these]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") instructions to get WIFI working. If you run into further issues, post back on these forums for help.

---

### Post by bschilke.biz on 2013-11-28
Duckhook - Awesome, thanks so much so the tips. I was downloading ubuntu but I'm going to go get the lighter version.

---

### Post by Phateless on 2013-11-28
> **bschilke.biz said:**
> I found an old dell d620 (1 GB Dual core CPU, 1GB RAM, 40GB HD) that my wife had been issued for work years ago that I fired up and got the below error message.*

Stop: c0000218 {Registry File Failure} The registry cannot load the hive (file): \SystemRoot\System32\Config\SOFTWARE or its log or alternate


I thought it would be a good excuse to try running a live version of Ubuntu (ubuntu-5.10-live-i386.iso) from a usb stick but I couldn't get it to run (although I now want to install permanently if I can). I changed the order of operations among devices to look at usb first but no luck. I then tried using a cd and didn't have any success there either. (in all cases the usb stick or cd is ignored and a I get a message about no bootable device being found)*

My suspicion is the bios is too low a version, I can't find the link but someone had a similar problem and solved it by upgrading to bios revision A10. I've tried that using a utility but got a file size error (I can provide links at a later point, in writing this on my phone).*

I could live with never booting into the installed windows xp, but does anyone think the above registry issue is causing me problems? In my mind the registry isn't involved until windows starts to load.*
I have a D620. Just keep pressing F12 while booting, then you can select your boot option.

I recommend Lubuntu because it's light and fast. Full Ubuntu will be too slow on that machine.

Use this trick to get your wifi working. - [http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/](http://linuxg.net/how-to-fix-broadcom-bcm4311-wireless-driver-on-ubuntu-and-linux-mint/)

---

### Post by ansus on 2013-11-28
I am new to Ubuntu. I have installed Ubuntu 12.04 on a very old laptop and Ubuntu 13.10 dual boot windows 8.1 on a desktop. Both run fine.
I used a DVD created using Infrarecorder, this took the ISO image and created an INSTALL DVD. You check the folders on that DVD once it is created. In both cases I had to TAP TAP TAP F12 until I had a selection to load from CD-ROM.

[http://infrarecorder.org/](http://infrarecorder.org/)

This is explained on the Ubuntu web page
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)


I did make a USB stick version also. Once again it was TAP TAP TAP F12 to get the loader, and the system saw it as an actual HARD DRIVE which I selected under the boot loader hard drive section. Below is the link to the USB Universal Installer needed to create an install USB from the ISO image.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

This is all described on the Ubuntu web page
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

I hope this helps

---

### Post by bschilke.biz on 2013-11-30
Thanks again everyone!  I updated bios, got lubuntu installed and have a working wireless connection.  This old laptop loads pages faster than the 2 macbooks my wife and I own, so that alone was worth the time.  

Any good links on learning the basics of linux on the inside?

---

### Post by heir4c on 2013-11-30
[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)
And a post of me with a few links in it:
[http://ubuntuforums.org/showthread.php?t=2190606&p=12860216#post12860216](http://ubuntuforums.org/showthread.php?t=2190606&p=12860216#post12860216)

---

### Post by DuckHook on 2013-11-30
> **bschilke.biz said:**
> Any good links on learning the basics of linux on the inside?General Ubuntu Intro:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)
[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

Command line learning:

[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

"Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Congrats and Happy Lubuntuing!

---

### Post by mörgæs on 2013-11-30
Please mark the thread solved using 'thread tools'.

---

