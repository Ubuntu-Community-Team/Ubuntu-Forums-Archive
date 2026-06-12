---
title: "Can not try ubuntu without installing and cannot install too"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by newbie13 on 2014-04-26
I was trying to dual boot ubuntu with preinstalled windows 8 but couldn't succeed. I am completely new to ubuntu.

I downloaded ubuntu-14.04-desktop-amd64.iso from torrent and burned it to a DVD. After that I booted my laptop from the disc. There were four options 
1. try ubuntu without installing
2. Install ubuntu
3. don't remember this but it was for manufacturers
4. Check defects in disc

I went for the first option. A screen with Ubuntu written on it and 5 dots changing from white to orange appeared. After 20 to 30 minutes a line saying 'booting without full network configuration' appeared and nothing happened after that. I kept my laptop like that for 3 hours still it was displaying the same message. 

I followed this procedure for 3-4 times and then chose the second option i.e. to install ubuntu but this time also i got stuck at the same screen. It says booing without full network configuration but it has never booted.

When I press ctrl+alt+f2 at that screen a message saying 60 seconds have passed and so login time. 

I have 
HP Pavilion g6 2301ax laptop
processor - AMD vision A8
RAM - 4 gb
Graphic card - AMD Radeon HD 7640G + 7670M Dual Graphics
HDD - 500 gb

I really want to install ubuntu so please help as early as possible.

---

### Post by mgmiller on 2014-04-26
Just a shot in the dark here, but instead of booting from a DVD, try installing the iso on a USB thumb drive using unetbootin or similar software.  Then, boot from the thumb drive.  You may also have to try turning off secure boot in the UEFI BIOS, which is only needed for WIndows 8, just for the purposes of this test.

That being said, I recently tried booting Ubuntu on a Win 8 machine I had bought for my office and never could get it to boot.  I ended up returning the computer.  I have been using Ubuntu for 10 years now and had never had this kind of problem before, it always just worked aside from an occasional driver issue here and there.  But it always booted.  Good luck.

---

### Post by newbie13 on 2014-04-26
Sorry i forgot to mention the things i've tried.
I have tried turning off the secure boot. I've also tried turning EFI on which was off first. But it did not help.
One more thing i've tried is, when selecting try ubuntu option,i pressed e and on that screen I added 'nomodeset' after 'quiet splash --'

---

### Post by grahammechanical on 2014-04-26
Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Note these points

> 
[LIST]
[*=left][FONT=inherit]In your BIOS, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows8, also [disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").[/FONT]
[/LIST]

> 

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too.[/FONT]
[/LIST]

> 

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[/FONT]
[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[/FONT]
[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode[/FONT]
[/LIST]


This problem may be related to the graphics on that machine and less to do with Ubuntu. It is best if we run the live session first. Try this

1) At the first purple screen press Enter
2) at the next screen select the language (English is default)
3) at the TRY UBUNTU - INSTALL UBUNTU screen press F6
4) look for a menu appearing at the bottom right and select nomodest and press Enter.
5) press Esc to get back to the TRY - INSTALL screen and select TRY and  Enter.

See what happens.

Regards.

---

### Post by newbie13 on 2014-04-27
I didn't expect replies so fast. This site and its people are really great.
Thanks to mgmiller and grahmmechanic for their help.
I'm going to try all the methods mentioned in your posts and will post the results soon.

Thank you once again.

---

### Post by newbie13 on 2014-04-28
Failed.
I tried booting ubuntu by turning off secure boot and fast start up with combination of once disabling and once enabling legacy mode but it still gets stuck at the same window. Even in virtual machine it is freezing there.
I get to choose try ubuntu, install etc directly after selecting where to boot from. No purple screen comes before that and also, f6 (or f1 to f12) does not show any options while selecting options in grub.

I ran disc check up and i think I have figured out the problem. I don't know if that is the real problem so i've attached a photo of result of disc check up. It says one file is mismatching or something.

A quick message flashes on screen before grub menu appears. It says 'could not open "\EFI\BOOT\fallback.efi": 14'

This is all the data which I have collected.

---

### Post by newbie13 on 2014-04-29
Help please!

---

### Post by mgmiller on 2014-04-29
Have you tried, as I had suggested in my first post booting from a USB thumb drive?  Also, the casper error may be caused by a problem with a persistence partition that is being created.  When you create the install medium, if there is an option for persistence, make sure it is unchecked.  On a DVD, there should not have been an option to create the persistence file.  
'could not open "\EFI\BOOT\fallback.efi": 14'  sounds like an EFI/UEFI error.  Ubuntu should work with "most" computers with UEFI bios, but there are some that just don't work.  You can try turning off all refeences to EFI and UEFI in bios.  Be aware that once you do that, Windows 8 won't boot until you turn them back on.  For now we just want to see if you can boot the machine into a live session at all.

Your live disc may also be defective.  Try making another one from a fresh download of the ubuntu iso.  Here is a page that tells how to determine if your downloaded ubuntu iso is defective or not.  It involves checking an MD5 check sum "hash".  Once you go to this page, scroll down to where it gives the instructions for doing this in Windows..... [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Another question is how you are creating the live DVD/thumb drive.  I have found unetbootin to be very reliable for creating USB live thumb drives.  Get it here....  [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

So, what you are going to do is....check to make sure the ubuntu installer you downloaded is defective or not,  then try creating an installer on a different kind of medium, using different software (unetbootin) with persistence turned off on a USB thumb drive and booting from that.

One last thing, are use using 64 bit or 32 bit Ubuntu?  32bit has a lot of problems with UEFI.  Really, post #4 above, that gives the link to the UEFI support page is very important. 
Good luck.

---

### Post by newbie13 on 2014-04-30
Success!!

Redownloaded Ubuntu and booted it from usb. 

Thank you everyone:)

But now there are other problems.
1. Wireless connection key is not working. It is combination of f12 and wifi, bluetooth on/off which is not working. Other function keys are working like f2 to reduce brightness etc.
2. It is not detecting bluetooth.

When I pressed enter on try ubuntu, i thought I will have to wait for half an hour again but to my surprise it immediately showed the desktop. It was really a great feeling.

---

### Post by mgmiller on 2014-04-30
Glad to hear it worked.  For the next problems, you should do a forum search on those topics.  They are discussed a lot.  If you still can't find anything, start a new thread with your specific problems.  Blue-tooth and wifi are 2 separate things, so search accordingly.

Just as a quick thought, for the f12 wifi thing, don't you also need to hold down a function key at the same time as you press f12?  There may also be a separate physical button on the (I assume it's a) laptop to turn your wifi on and off, check that it's set accordingly.

You will need to search with the specific model of notebook as there may be different solutions depending on the model.  I have a Lenovo T400 and every function key and button on it works perfectly with no tinkering, but I selected that computer after researching specifically for very compatible hardware.  It has always had only Ubuntu on it.  I wiped the HDD and installed Ubuntu the day I got it and never even booted Windows. 

Since your original problem has been resolved, you should mark this thread as solved.

Good luck and have fun with Ubuntu.

---

### Post by newbie13 on 2014-04-30
There is no physical button for wifi and bluetooth and function+f12 is also not working.
I've others problems too like which disc to select while installing etc. but I will search it first.

Thank you for solving my problem

---

