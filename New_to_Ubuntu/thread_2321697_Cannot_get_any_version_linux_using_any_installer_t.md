---
title: "Cannot get any version linux using any installer to boot from USB"
date: 2016-04-23
forum: New to Ubuntu
---

### Post by Klawdek on 2016-04-23
I have tried mint, ubuntu installing them to USB using Universal USB, unetbootin and rufus.   I know everyone says to make a bunch of changes to the boot options.  I have tried all that.  

Yet without changing any boot options I can boot up to a recovery USB and I can boot to a bootable DVD so long as they are not linux.   I can only boot to a linux LiveDVD if I change all boot options to the other setting (fortunately they mostly have just two options so I just have to invert everything).


I can see why Linux is only for people with extreme technical knowledge not only of computers but specifically of linux.  It is not hard to use but it is dam near impossible to install and boot up.

---

### Post by QIII on 2016-04-23
Not everyone says to make changes and not everyone has even the slightest problem installing Ubuntu.

What is your point here?  Are you seeking help?

---

### Post by Klawdek on 2016-04-23
I have read a lot on the subject of trying to boot to linux from USB.  They all say to access boot menu and make changes.  I have tried many times and made many changes to the boot options and nothing works.  I cannot boot to a linux USB.  It I have tried ubuntu and mint.  I have used Pendrive, Unetbootin, and Rufus.  When I boot up and press F12 to get boot options USB is not listed.

I made a DVD and in order to boot to it.  I had to change all of the boot options.  Maybe only some were needed.  However without making any changes to boot options I can boot with bootable USB sticks and DVDs such as recovery discs.  

I read somewhere that the best way, was to boot to the live CD and make the bootable USB from there instead of from windows.  I tried that but linux only wanted to install to a hard drive and there was no option for installing to USB. 

I was able to take one of the USB sticks that would not boot on my system and boot to it on an older BIOS system.

---

### Post by QIII on 2016-04-24
Except as I have wanted to for some purpose of my own, I've never *had* to change ANY boot option, with the rare exception of sometimes changing nomodeset depending on the state of support for some graphics cards -- which, after having been made permanent, was never a problem again.  So I don't know what you've been reading a lot of.

It's a bit hard to sound convincing when you walk into a crowd of people wearing lederhosen and start saying it is impossible to put on lederhosen.  It doesn't ring and you might be taken for a crank.

Now, if you were to walk in with your lederhosen and say you have really had a lot of trouble getting them on and politely ask for help, the people who wear lederhosen all the time would probably be happy to help.

So, were I you, I would make a different choice about your current approach.

---

### Post by kurt18947 on 2016-04-24
What make/model machine is giving you so much trouble? I wonder if you have the misfortune of having a machine with a difficult UEFI implementation. I've had some older machines (7+ yrs. old) that were cranky about booting from a USB drive but have never had a DVD fail to boot. Yes it may be necessary to temporarily override the default boot order which is what I suspect F12 does for you. If "extreme technical knowledge" were required I'd be in deep trouble:D. Also, there's a LOT of outdated and just wrong information on the interwebz. The trick is to figure out which sites are generally correct and which are for entertainment purposes only.

---

### Post by Klawdek on 2016-04-24
I am not sure why you take such exception to what I am saying.  You may have never had to change boot options but if you look up "cannot boot linux from USB" it is pretty standard advice.

Linux has a long history of being difficult to install.  They used to sell linux distributions on the basis they were easier to install because they had install scripts.  Every time I have looked into linux it was an issue of which distribution could actually be installed by a beginner at linux. 

Now microsoft has forced this UEFI thing in order to prevent any OS other than windows to boot.   I have read about how micorsoft hates linux.   I doubt Microsoft has any concern about linux.  I figured they must be trying to stop google from putting out an android on USB stick and later in systems.  And guess what?  They have just come out with an android system for your desktop and laptop that can boot from USB. 

I suspect that my problems are to do with Microsoft not wanting any other OS to be run.

I realize that android for desktop will not go over well for business.  However the average user mostly uses their web browser and little else, so I suspect Microsoft is concerned about Android on the desktop and this EUFI stuff is all about preventing there ever being a competing OS from Google. 

This leads me to wonder if it is worth perusing linux at all.

---

### Post by Klawdek on 2016-04-24
I am using a Dell Inspiron 15-3521 laptop with Windows 8.1.

---

### Post by Bucky Ball on 2016-04-24
> **Klawdek said:**
>   

I read somewhere that the best way, was to boot to the live CD and make the bootable USB from there instead of from windows.  *I tried that but linux only wanted to install to a hard drive* and there was no option for installing to USB.

This suggests you managed to boot install media and were offered the option to install Ubuntu. :-k

If whatever you booted from was offering to install to a hard drive, then you have successfully created install media, are booting into it and not sure what the problem is. 

Or is it that what you're trying to do is install Ubuntu to a USB? There are a lot of words here but not much clarity. If this is the case, you need two USB sticks/disks. Sounds like you have and can boot from one. Plug another in and install Ubuntu to it.

Please confirm: are you wanting to install to hard drive or USB and can you boot ANY install media ANY way? (You mentioned that without changing anything you can boot to boot disks. Well do that.)

---

### Post by Klawdek on 2016-04-24
I can only boot to liveDVD if I change the boot options with F12.  I have never had to change boot options before to get system to boot from an optical drive.  It will not boot from USB no amount of options changing will do it.  It is not even possible to get to either system setup  F2 or the boot menu F12 if the USB is plugged in.   If I try to get into boot options menu with USB installed it will just freeze the system until the USB is removed and the system is powered down.

---

### Post by RobGoss on 2016-04-24
> **Klawdek said:**
> I have tried mint, ubuntu installing them to USB using Universal USB, unetbootin and rufus.   I know everyone says to make a bunch of changes to the boot options.  I have tried all that.  

Yet without changing any boot options I can boot up to a recovery USB and I can boot to a bootable DVD so long as they are not linux.   I can only boot to a linux LiveDVD if I change all boot options to the other setting (fortunately they mostly have just two options so I just have to invert everything).


I can see why Linux is only for people with extreme technical knowledge not only of computers but specifically of linux.  It is not hard to use but it is dam near impossible to install and boot up.



> I can see why Linux is only for people with extreme technical knowledge not only of computers but specifically of linux. It is not hard to use but it is dam near impossible to install and boot up.

Ubuntu has made it very easy for anyone to learn how to install Ubuntu or any **distro**, You have to have a little patients and willing to deal with problems that may arise

This forum is full of people willing to give a helping hand all you have to do is ask your questions and I'm sure someone will answer them

---

### Post by RobGoss on 2016-04-24
> **Klawdek said:**
> I am using a Dell Inspiron 15-3521 laptop with Windows 8.1.

These are not the specs for your machine providing what hardware you have will help other give you the help you so desperately need

---

### Post by oldfred on 2016-04-24
Of all the brands, Dell is one of the better ones.
It offers Linux pre-installed on some of its highend systems. And often the same drivers are available for lower end machines.
They first created sputnik for 12.04 which included a lot of drivers. But all that was included in 14.04 so users had a much easier time installing.
And they have a new sputnik for new systems.

With UEFI and by brand the issues are common across models. Only real differences are whether AMD or Intel, what video card/chip & what Wi-Fi chip is used. And often those type of issues are even common across brands as the sub-systems/chips are the same.

One or two threads with users who use Dell and had it work. With my Dell it took about 10 minutes to install, and I think the only settings I changed was to turn off Secure Boot in UEFI and choose to boot USB flash drive.

       Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)
Uses Intel Wi-Fi adaptors
[http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/](http://arstechnica.com/information-technology/2016/03/dells-skylake-xps-13-precision-workstations-now-come-with-ubuntu-preinstalled/)
Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
Dell with Ubuntu pre-installed loopmount ISO for recovery
[http://askubuntu.com/questions/739763/grub2-issue-ubuntu-will-not-boot-unless-i-type-exit-from-grub-menu](http://askubuntu.com/questions/739763/grub2-issue-ubuntu-will-not-boot-unless-i-type-exit-from-grub-menu)
Install Ubuntu 15.10 on Dell XPS 15 2015 9550 with Nvidia 960
[http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960](http://askubuntu.com/questions/736613/install-ubuntu-15-10-on-dell-xps-15-2015-9550-with-nvidia-960)
Dell XPS 13 9343 Needs /EFI/Boot/Bootx64.efi to boot
[http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13](http://askubuntu.com/questions/731931/uefi-not-finding-a-bootable-system-on-xps13)
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323)
Black Screen on Install (15.04 & 15.10) Dell XPS 8900 
[http://ubuntuforums.org/showthread.php?t=2303880](http://ubuntuforums.org/showthread.php?t=2303880)
Dell LATITUDE E5450  LInks to Dell fixes for 14.04
[http://ubuntuforums.org/showthread.php?t=2270275](http://ubuntuforums.org/showthread.php?t=2270275)
Dell M3800 with 14.04 Some issues
[http://arstechnica.com/gadgets/2015/03/review-dell-m3800-developer-edition-is-a-great-linux-pc-with-a-few-rough-edges/2/](http://arstechnica.com/gadgets/2015/03/review-dell-m3800-developer-edition-is-a-great-linux-pc-with-a-few-rough-edges/2/)
Dell XPS13 - New Broadwell, not yet fully supported Feb 2015
[https://bugs.launchpad.net/dell-sputnik/+bug/1499323](https://bugs.launchpad.net/dell-sputnik/+bug/1499323)
[http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/](http://major.io/2015/02/03/linux-support-dell-xps-13-9343-2015-model/)
[http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)
Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3647 w/  i3-4170 Processor  
   Dell XPS13 2015 image with 14.04
[http://phoronix.com/scan.php?page=news_item&px=Dell-Ubuntu-XPS-2015-14.04](http://phoronix.com/scan.php?page=news_item&px=Dell-Ubuntu-XPS-2015-14.04)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)
Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
[http://ubuntuforums.org/showthread.php?t=2179297](http://ubuntuforums.org/showthread.php?t=2179297)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
[SOLVED] Dual-boot Ubuntu/Windows8 on Dell XPS 8500, need just a few advices with info on UEFI settings
[http://ubuntuforums.org/showthread.php?t=2151494](http://ubuntuforums.org/showthread.php?t=2151494)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Question about Dell's Ubuntu Preloaded XPS 13 Developer Laptop Link to review, Sputnik
[http://ubuntuforums.org/showthread.php?t=2106590](http://ubuntuforums.org/showthread.php?t=2106590)
New Haswell Sputnik - Dell orbits Linux a third time with revamped Sputnik notebooks
[http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/](http://www.theregister.co.uk/2013/11/15/dell_sputnik_3_linux_laptop/)

---

### Post by Klawdek on 2016-04-24
The setup says at the top InsydeH20 Setup Ulility.  The BIOS version is A12. Intel i3-3217U 1.8 GHz.  Windows 8.1 64 bit

---

### Post by oldfred on 2016-04-24
Is that the newest UEFI from Dell for your system?

A user who had your model.
But was a much older version of Ubuntu. It should be easier now.

[http://askubuntu.com/questions/323477/how-to-dual-boot-on-dell-inspiron-3521-laptop-preinstalled-with-windows-8](http://askubuntu.com/questions/323477/how-to-dual-boot-on-dell-inspiron-3521-laptop-preinstalled-with-windows-8)

---

### Post by Klawdek on 2016-04-24
I just updated it to the newest one offered on Dells site for this computer so it went fro A12 to A14.  It now will allow me to go into set up or the boot menu with the USB installed.  But that it is the only improvement.  USB does not show up at all anywhere in the boot menu of the set up.  There is no way to select it as a boot option.

---

### Post by oldfred on 2016-04-24
How did you make flash drive?
 What flash drive?
 Did you verify download is correct with md5sum?

       [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb

[/URL]
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]
[/URL]

---

### Post by Klawdek on 2016-04-24
Thank you for all the links however I am starting from a windows system not linux so those instructions do me no good.  The DLs are good as the USB can boot from old BIOS computers just not a newer UEFI computer.

---

### Post by oldfred on 2016-04-24
Links do have versions for both Ubuntu & Windows.

If download is 64 bit then it also is UEFI. But if you downloaded the 32 bit version, it will not work with UEFI.
And if then 64 bit version, it seems that it still is a setting in UEFI.
You often need to have UEFI on, and maybe UEFI secure boot off. And some require you to specifically allow USB port booting.

---

### Post by sudodus on 2016-04-25
To be specific, this link points to a method starting from Windows: [https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by RobGoss on 2016-04-25
> **Klawdek said:**
> I just updated it to the newest one offered on Dells site for this computer so it went fro A12 to A14.  It now will allow me to go into set up or the boot menu with the USB installed.  But that it is the only improvement.  USB does not show up at all anywhere in the boot menu of the set up.  There is no way to select it as a boot option.

I have nothing but Dells and there has to be an option that allows you to boot from a USB or CD, I been using Linux for a few years now and even on my 15- year old Dell it's running Ubuntu, having patience and understanding is the key to using Linux

It appears to me you have some frustrations dealing with Linux you might want to stick with Windows because it's no one fault you chose to give Linux a try

The people in these forums are devoting there time to help answering questions so keep that in mind when you post a guesting here.

---

### Post by oldfred on 2016-04-25
I dual booted with XP for quite a while. And I had one Windows application that I had used since DOS days and it was not available in Linux. 
And I considered myself knowledgeable in Windows and it took a while to get used to Linux.

Now I have the opposite issue. My one new Dell which came with Windows 8, was to record video with Linux, but then Comcast lets us watch our DVR recordings on the computer but only works with Windows. And now I do not know how to do anything anymore. But somehow when I finally find the right set of icons to get where I want the screen is almost identical to what I remembered with XP. 
But Windows uses so many resources that DVR sometimes stutters. I cannot find what in background is running. 

But Amazon Firestick with almost no hardware in a flash drive size stick plays HD video from Wi-Fi without issue.

---

### Post by kurt18947 on 2016-04-26
> **Klawdek said:**
> I just updated it to the newest one offered on Dells site for this computer so it went fro A12 to A14.  It now will allow me to go into set up or the boot menu with the USB installed.  But that it is the only improvement.  USB does not show up at all anywhere in the boot menu of the set up.  There is no way to select it as a boot option.

disclaimer: I don't have a Dell laptop. When you cold boot with an Ubuntu USB by pressing F12, do you see anything like USB HDD (hard disk drive) or similar? Ubuntu Live USBs are sometimes seen as USB hard drives.

---

### Post by Klawdek on 2016-04-29
> **kurt18947 said:**
> disclaimer: I don't have a Dell laptop. When you cold boot with an Ubuntu USB by pressing F12, do you see anything like USB HDD (hard disk drive) or similar? Ubuntu Live USBs are sometimes seen as USB hard drives.

No the USB does not show up at all.

---

### Post by oldfred on 2016-04-29
It could be a sub-menu under hard drive.

Or flash drive is not correctly configured to be bootable. It will not show in boot menu unless it is bootable.

---

### Post by him610 on 2016-04-29
Just a suggestion:

Before you boot, make sure your USB drive is in a USB 2 port; sometimes, USB drives in a USB 3 port are not seen by the OS.

---

### Post by Bucky Ball on 2016-04-29
> **him610 said:**
> Just a suggestion:

Before you boot, make sure your USB drive is in a USB 2 port; sometimes, USB drives in a USB 3 port are not seen by the OS.

And +1 to this. I did an install only three days ago where I battled with a USB3 *dongle* in a USB2 slot trying to install. Put the installer on a USB2 stick and installed without issue. This is not exactly the same as what him610 describes, but related and also a consideration.

---

### Post by leunam12 on 2016-04-30
If you boot Windows and then restart your computer while holding down the SHIFT key, it will take you to a blue screen with a special menu from where you can choose to boot from the USB device. you USB stick has to be inserted and it has to have a bootable 64 bit system.

---

### Post by Klawdek on 2016-05-01
Here is what happened.   After updating my firmware. I decided to try some other installers.  Now I did try different USB sticks.  However they were all Microcenter 16 and 32GB 3.0 USB bought at different times and with different physical sizes.  The stick I tried this time was a Microcenter 4GB 2.0 USB.  I had not tried it before because it had files on it, but I recently moved them off of it. 


I was able to create a bootable Mint LiveUSB.  Then I remember one of the posts that said sandisk will boot well so I went to Wallgreens and bought 2 sandisk cruzer glide 16GB USB 2.0 (I wanted 3.0 but I had to take what could get).


I was able to make a bootable LiveUSB with Ubuntu.  I was also able to make a full install of Mint and I assume I will be able to do it Ubuntu.


That brings me to my next question. Can I follow the same instructions I did for Mint? 
[http://www.linuxveda.com/2011/05/30/install-linux-mint-usb-drive-walk-portable-linux-mint/](http://www.linuxveda.com/2011/05/30/install-linux-mint-usb-drive-walk-portable-linux-mint/)


I read some instructions for doing a full install of Ubuntu and it looked the same.  I like the ones for Mint because it is very clear with complete list of settings and has pictures so I can see as I am doing it.


I plan on following those instructions unless someone says it is a bad idea.


Also I am planning on getting some more USB sticks that are 3.0 so I hope it is not a problem with 2.0 in general.


I have been planning on getting an external HD.  I am thinking about a 5TB drive.  Would it be better to install to an external HD?  I am thinking it will run better.

---

### Post by Bucky Ball on 2016-05-01
From '1. Install' yes, it is pretty much the same, with different graphics. 

Were you attempting to use USB2.0 sticks in a USB3 slot or tried both types of slots? It can be problematic trying to install from 3 using a 2 slot and vice versa, although the stick might work fine for day-to-data data storage and retrieval. Go figure. :|

So don't try the new USB3 in a USB2 slot for install. Working on a thread a day or two ago where this was the user issue. Soon as they grabbed a USB2 stick for the slot, problem solved.

---

### Post by Klawdek on 2016-05-01
> **Bucky Ball said:**
> From '1. Install' yes, it is pretty much the same, with different graphics. 

Were you attempting to use USB2.0 sticks in a USB3 slot or tried both types of slots? It can be problematic trying to install from 3 using a 2 slot and vice versa, although the stick might work fine for day-to-data data storage and retrieval. Go figure. :|

So don't try the new USB3 in a USB2 slot for install. Working on a thread a day or two ago where this was the user issue. Soon as they grabbed a USB2 stick for the slot, problem solved.

I used 3.0 USB ports for install and for booting except when I tried to boot from USB 2.0 port to see if that worked.

---

### Post by kurt18947 on 2016-05-01
> **Bucky Ball said:**
> From '1. Install' yes, it is pretty much the same, with different graphics. 

Were you attempting to use USB2.0 sticks in a USB3 slot or tried both types of slots? It can be problematic trying to install from 3 using a 2 slot and vice versa, although the stick might work fine for day-to-data data storage and retrieval. Go figure. :|

So don't try the new USB3 in a USB2 slot for install. Working on a thread a day or two ago where this was the user issue. Soon as they grabbed a USB2 stick for the slot, problem solved.

It may depend on the USB drive vendor. I've used MicroCenter USB 3 drives inserted into USB 2 sockets for live USB and had no issues. It seems to me like MicroCenter drives are pretty 'plain vanilla', no 'value added' enhancements that can throw a wrench in the works. I had a couple Toshiba white 16 GB. USB 2 drives inserted into USB 2 slots that didn't seem to like being used as Live USB drives.

---

