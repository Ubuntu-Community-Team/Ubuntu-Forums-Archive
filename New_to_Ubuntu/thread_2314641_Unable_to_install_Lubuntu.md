---
title: "Unable to install Lubuntu"
date: 2016-02-22
forum: New to Ubuntu
---

### Post by moran2 on 2016-02-22
Hi. I've decided to try Linux. I tried to install Lubuntu on my old win XP PC (Pentium 4 2.80 Ghz, 512 mb RAM, 8I865GME, RADEON 9600) but couldn't do it on my own, so I came here to get some help. My intention was to swap XP with Lubuntu so I wanted to boot from a flash driver and to do a clean install. I created a usb with Lubuntu with the LinuxLive USB Creator 2.9.4 tool and tried to boot from it without success. I tried different usb ports, different usb devices, different file sources. And then tried to boot from  usb zip, usb fdd usb hdd but although I can see the usb is recognised by bios it gives a "boot disk failure". I also tried to run the Lubuntu installer from within Win XP, however was prompted that it failed because it couldn't download metalinnk (I dont have internet accsess for that computer so I figured that is the problem). I also tried to run the installer from windows but with the virtual box. This was ended up with a critical error. Any ideas how to boot up from the Lubuntu usb? Or how to install Linux at all?

Thanks.

---

### Post by yoshii on 2016-02-22
have you tried creating a boot CD or boot DVD (liveCD) from the Lubuntu .ISO ?  
if you do that, edit your BIOS/UEFI settings so that the CD/DVD-ROM drive boots first.  
Then, put the burnt disc into the drive and restart the computer.  As long as the disc was burnt without errors, it should work.

---

### Post by yancek on 2016-02-22
Have you ever successfully booted any usb device on this computer, is it capable.
Do you have another computer available which you can use to test the usb to see if it works, to verify the usb is bootable?
The usb might be shown under hard drives in the BIOS.  Can you see if it is recognized there?
No, it won't boot from inside xp.
You indicate you tried to run Lubuntu in Virtual Box and got a "critical error".  You forgot to post that error!
Have you tried burning the Lubuntu iso as an image to a DVD and booting?

---

### Post by goofprog on 2016-02-22
Yoshi2 is right.  The cool old compact disk will work better.   I suggest taping it to the inside of the computer case too just for safe keeping.

---

### Post by moran2 on 2016-02-22
Unfortunately. I can't use a disc, but about the usb I guess u were right. Other computer was booted up from this usb. Still, it is strange why I cannot boot from usb in the compuer I want to install linux to since it have the option and I can see the usb pen is recognized in BIOS. what else can I try? If I run it within the virtual box can I install Lubuntu instead of XP?

---

### Post by yancek on 2016-02-22
Check the various options in the BIOS under the Boot tab.  You might try the suggestion at the link below in the first post.  Computers over 10 years old probably won't boot from a usb. 

[http://www.pclinuxos.com/forum/index.php?topic=119088.0](http://www.pclinuxos.com/forum/index.php?topic=119088.0)

> If I run it within the virtual box can I install Lubuntu instead of XP? 		

No, because you have to install VirtualBox on xp and then install Lubuntu inside VirtualBox inside xp.

---

### Post by Mopar1973Man on 2016-02-22
Can you steal a DVD player from another computer temporarily so you can use a DV installer disk to get the Lubuntu installed? I've done that a few times stealing the DVD-RW from my main computer to install Ubuntu in another computer because the DVD player is damaged or missing.

---

### Post by sandyd on 2016-02-22
If you don't have a DVD/CD drive, and USB does not work, and you don't mind fiddling around, you can use PXE to boot the computer. I find that even older computers that cannot boot from USB will be able to do a network boot from PXE.

You will need another computer, and temporarily turn off your DHCP server on the network or create a network between the other computer and this one that does not have a DHCP server. Seeing as you are using Windows, you can run Serva on your other Windows computer (Ignore the subscriber requirements/etc, the free version will be fine for your needs). You can download it from [http://www.vercot.com/~serva/](http://www.vercot.com/~serva/)

You can then follow the instructions at [http://vercot.com/~serva/an/NonWindowsPXE3.html#linux](http://vercot.com/~serva/an/NonWindowsPXE3.html#linux) to setup PXE boot. After the server is setup, check in your target computer's BIOS or boot options. There should be something to boot from NIC or PXE. Using that boot option should allow the PXE install to begin, and you should be able to install

---

### Post by mörgæs on 2016-02-23
With 512 MB I suggest installing the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") no matter if you use USB, CD/DVD or PXE.

---

### Post by moran2 on 2016-02-23
Wow what a vibrant community. Thanks for the replies. In the end I managed to open the stucked compact disk drive, and it was simple to install it from the cd on the old computer (although as one friend suggested her I should have used the alternate installer, because the regular installer was slow and the menues didn't close after what caused a mess of stacked menues). So now I have Linux! Lubuntu is indeed faster than the XP I had before although its hard to compare because the Linux is fresh comparing to the used XP. But guys here's a problem: I don't have a keyboard there so I've instaled onboard (on screen kb) but I can't run it after I boot linux when I'm asked to enter my passcode. What can I do? I did asked to log me in automatically but from some reason it won't (and it is the only account). Please help me.

---

### Post by mörgæs on 2016-02-24
A screen keyboard is slow and cumbersome to use. You will be better off by getting a real one.
If it's about saving money you can get them more or less for free at a flee market.

---

### Post by moran2 on 2016-02-24
Well the price isn't the problem. Isn't there a way to log in automatically? (and I clearly remember that I checked such an option...)

---

### Post by mörgæs on 2016-02-26
[https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#How_to_enable_automatic_logon](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login#How_to_enable_automatic_logon)

---

### Post by Geoffrey_Arndt on 2016-02-26
It's really a bad idea (horrible in fact) to log in without a password . . . . . dumb & dumber bad.    Too much can and does go wrong without a strong password . . . just like in Windows.

---

