---
title: "Unable to set up dual boot with windows 10 PC"
date: 2016-03-13
forum: New to Ubuntu
---

### Post by john526 on 2016-03-13
Hello,

I attempted to follow the installation instructions given at

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

for a PC running windows 10.  It seemed to work until I got the part that says "restart the computer, and you should be offered a choice between starting Windows or starting Ubuntu".

When I restart, or turn the computer off and then on again, I am not offered a choice between starting Windows or starting Ubuntu.  Instead it goes straight to Windows.  

I thought perhaps that if I disabled SecureBoot, it might help.  However, I've now read that not all PCs with Window 10 offer the option of disabling SecureBoot, and unfortunately it appears that my PC is one of those that doesn't allow disabling SecureBoot.  

Does anyone have any ideas about what else I might try to set up a dual boot with Window 10?

Thanks,

John

---

### Post by grahammechanical on 2016-03-13
The issue might be secure boot but I am more inclined to something else. At least you can confirm that you followed the advice here.

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]


It is a safe bet that Windows 10 was installed in EFI mode. Whatever mode we run the Ubuntu live session in, then that is the mode Ubuntu will be installed in.

Regards.




[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by yancek on 2016-03-13
Read through the link below, the official Ubuntu documentation on dual-booting window/Ubuntu.  Do you see anything there you did not do?  Did you check or can you check to see if windows 10 is UEFI?  If it was pre-installed, it almost certainly was.  In that case, you would need to install Ubuntu UEFI or you get the result you now have.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you can still boot windows, go to the boot repair site below and download it and burn it as a bootable image to a CD.  Reboot the computer with the CD in the drive and then select the option to "Create BootInfo Summary'.  Post a link to the output as it has a lot of information on your system and with it someone should be able to help. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2016-03-13
What brand/model system?

Some systems call Secure boot "Windows" and UEFI without secure boot "Other".

---

### Post by john526 on 2016-03-13
Thank you for the quick responses.  I'll look into these leads to see if I can make headway and then post the results.

---

### Post by john526 on 2016-04-03
Things have gone from bad to worse for me.  I uninstalled Ubuntu because I wanted to just start over (which may have been a mistake).  However now I cannot even boot Ubuntu from the DVD anymore.  So I tried to go back to step 3 "Change the boot order" described in the standard installation to try to make sure that the optical drive was still at the top of the boot order.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

But for some reason my PC is no longer allowing me access to a menu for changing the boot order.  I unfortunately didn't write down how exactly I changed the boot order before - it did vary some from what is described in step 3 "Change the boot order".  However redoing what I thought i did before, does not bring up the screen allowing me to see and if necessary change the boot order any more.   

I was going to try to run the boot repair as described in 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

from within Ubuntu but now I can't do it since I can't even boot Ubuntu anymore.

Another obstacle I hit was in UEFI Installing - Tips

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

it says "In UEFI turn off fast boot (different than fast start up)".  I have been unable to access the editing screen allowing me to turn off fast boot (or secure boot for that matter).  

The product information for this PC is as follows

It is a Lenovo H50-55

Windows 10 Home 

Processor: AMD A10-7800 Radeon R7, 12 Compute Cores 4C+8G 3.50 GHz

I purchased this PC recently and I believe I can return it.  At this point I'm wondering if there is another PC model option that someone could recommend where the dual-boot setup is more established and less arduous for an absolute beginner?  Alternatively is it possible to purchase a PC with windows/Ubuntu dual-boot already installed? 

Thanks

---

### Post by oldfred on 2016-04-03
Did you turn Secure boot on? That may totally restrict booting.
And then you may have to turn on allow USB/DVD device booting.
Best to have UEFI secure boot off.
And then change boot order.

Some other Lenovo which may have similar issues.
       The thermal updates were submitted today for the Linux 4.6 kernel merge window and there's a very important fix for at least some newer Lenovo laptops.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)
Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side 

 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124) 

Just about every brand has issues. And newest hardare needs newest version of Ubuntu.

---

### Post by john526 on 2016-04-03
I'm actually not able to access Secure Boot.  In researching this I've found that not all PCs with Window 10 offer the option of disabling SecureBoot, and unfortunately it appears that my Lenovo PC is one of those that doesn't allow disabling SecureBoot.

I think related to this is the fact that I could not access the Fast Boot editing either.  When I looked up disabling Fast Boot it appeared to be edited through the same screen as Secure Boot.  My PC does not appear to give me access to this screen preventing me from changing either Fast Boot or Secure Boot from the default.

It looks like I could return my PC for ones with windows 7 or 8 installed.  Would I have a better chance of successfully setting up a dual boot if got a PC with one of these older versions of windows?

---

### Post by Quarkrad on 2016-04-04
wijnaldumwilliam  I have come across this problem a number of times - I solved it using something called DISKPART.  Do some research on 'converting a mbr disk to gpt disk' and have a look at [http://www.disk-partition.com/gpt-mbr/convert-mbr-to-gpt-without-data-loss.html](http://www.disk-partition.com/gpt-mbr/convert-mbr-to-gpt-without-data-loss.html).   I used the win10 install DVD - went to repair PC - command prompt - then used the diskpart commands to convert the disk.  This allowed me to do a clean install win10 and then a clean install of ubuntu.   Make sure you do your research first re protecting your personal data - I had a backup so converted my HD and did a clean install.

---

### Post by oldfred on 2016-04-04
What brand/model computer?
Only some tiny laptops or tablets have 32bit UEFI which does not have a CSM/BIOS boot mode. They were designed as Windows only devices. But some are able to install with difficultly.

---

