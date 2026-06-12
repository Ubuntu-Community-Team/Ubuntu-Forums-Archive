---
title: "Your suggestions please"
date: 2016-02-29
forum: New to Ubuntu
---

### Post by Hangman_ on 2016-02-29
Good afternoon,
I am new to the Ubuntu forums & new to the OS but I am determined to leave Windows behind.  I don't like the way MS is pushing.
Anyway, I have an old laptop to learn the new OS & it was suggested from others I use Ubuntu.  I have 4 books I'm currently perusing & have downloaded the Ubuntu 14.04.4 (LTS) to kickstart things but I am kind of stuck.  I am wondering if this laptop will do the trick or if I have to go with a better system.
The laptop in question has the following specs:
    Intel Pentium III 750 MHz processor
    128 Meg Ram
    System BIOS & Video BIOS are both shadowed
    XGA/TFT Display
    Toshiba DVD ROM drive
    PS/2 Mouse or Touchpad
    9.5 GB hard drive  (currently Blank)

I have downloaded the Ubuntu 14.04.4 LTS ISO image & have burned it to a DVD.  The CHK5Sum is correct & the DVD after the burn was verified & successfully finished.
When I tried (I just threw caution to the wind) to install the OS, after a several hours of crunching numbers I got a few "unable to read sector" errors & the install never finished after 6 hours. 

First of all, are these errors from an incompatible system (does Ubuntu require more resources than this laptop has) or do I have some bad spots on the disk?  Still trying to figure out how to work the search system on this forum (every search I've tried came up empty), I found a post describing in somewhat the same scenario, the OP described having a bad DVD drive.  This is possible in my case as well but if it is, it can certainly read Win7 & WinXP install disks just fine.
If these are bad spots, then can I assume Ubuntu does a complete checkdisk before installing the OS?  If THIS be the case, can Ubuntu (after running its check disk) disable the bad spots or perhaps try to fix them as Windows used to do?

If this is simply an incompatible system for the current OS I'm trying to install (Ubuntu 14.04.4 LTS), can you please give me some idea's on an OS that will run on this old system?

I have a newer laptop but I don't currently have the disk space to do a dual boot system.  I can run a USB key but as I said, I am ready to dump Windows.  I don't want a dual boot system, I want windows gone.  So I prefer learning how to install from a formatted, blank drive & delve into the world of Linux.

Do you have any suggestions, advice, or criticism on this choice of mine or this system described or other form of verbal abuse for windows you'd like to share?  By all means, share it!  :-?  And Thank you for your support.

---

### Post by jim_deadlock on 2016-02-29
Your main problem is the tiny amount of RAM. You won't get any graphical version of Ubuntu running on that. You could try a lightweight linux distro, some examples here:

[https://www.maketecheasier.com/best-lightweight-linux-distribution-for-older-computers/](https://www.maketecheasier.com/best-lightweight-linux-distribution-for-older-computers/)

---

### Post by yancek on 2016-02-29
Absolutely, Ubuntu and almost all major Linux distributions require more resources than you have with that hardware.   If you get Ubuntu installed somehow, it won't run because of the slow processor but most certainly because of the lack of RAM.  For the release of Ubuntu you are trying to install, the absolute minimum RAM for it to work at all is 512MB and 1GB is recommended.

In addition to the suggested link above, you can check the link below at distrowatch and it will show a number of options.  There will be links to the home pages of each distribution where you can check them out and get more details on the system.  Going to the site myself, I only saw 4 that might do the job:  AntiX, TinyCore , NanoLinux and Slitaz.  There were a number of others listed I'm not familiar with that might work but forget about a standard Ubuntu with that hardware. 


[https://distrowatch.com/search.php?category=Old+Computers](https://distrowatch.com/search.php?category=Old+Computers)

---

### Post by grahammechanical on 2016-02-29
Did you run the try Ubuntu session? How did that work?

Have you considered this? If that hard drive is the original drive that came with the machine, then it would not be surprising if there were some bad sectors in a drive that is so old.

I also doubt very much that the video adapter will run the Unity user interface of Ubuntu. To do that we need a video adapter than can do hardware accelerated 3D rendering and it will need from 512 MB to 1 GB of its own memory.

And you will have even less RAM available for the OS because shadowing the BIOS & video BIOS will copy them into RAM. You may need to disable those 2 functions.

If you can get the Ubuntu live session to run you should see a purple screen with an icon of a human and an icon of a keyboard. Press Enter. Then select the default language and at the underlying screen select Check disc for defects. See what that shows you.

Regards.

---

### Post by Hangman_ on 2016-02-29
> **grahammechanical said:**
> Did you run the try Ubuntu session? How did that work?
If you can get the Ubuntu live session to run you should see a purple screen with an icon of a human and an icon of a keyboard.

I did get the live session (of sorts) or I had the icons but it wasn't purple.  The disk was in continual crunch mode & the few times I tried the return & escape keys, nothing happened (now that I think of it I didn't give it enough time process the exchange).  Now that it has been mentioned the need of much more RAM than what I have, I can understand the constant crunch of numbers.

>  Have you considered this? If that hard drive is the original drive that came with the machine, then it would not be surprising if there were some bad sectors in a drive that is so old.

And it has been a long time since installing XP on the machine so I don't remember having sector errors when installing XP (it was old when I did that install) but it has been used off & on between then & now. 
But that's ok.  It's a junk PC & meant for this kind of tinkering.  If I have to lock out some sectors, so be it.  It'll go to the recycle bin after it just plain dies as I plan on driving it into the ground.

> 
If you can get the Ubuntu live session to run you should see a purple screen with an icon of a human and an icon of a keyboard. Press Enter. Then select the default language and at the underlying screen select Check disc for defects. See what that shows you.

This is good news that it does do a check disk.  I now know that the full blown Ubuntu will not run on this machine.  I just need to go find the minimum specs for each of Ubuntu's flavors now that I have this tidbit of information & find one for each of my machines (they all have different specs, different ages, etc). Although I do not plan on moving away from windows all at once.  I will do one machine at a time & get the kids & bride comfortable with what they will be working with before dumping the main windows desktop.

A Thank you to jim_deadlock & yancek for the links & a big thank you to all of you for the information you have provided.  I am stoked to get this project started & perhaps more importantly, finished.

---

### Post by 1clue on 2016-02-29
IMO that hardware is not a good way to learn Linux. You will be fighting every step.  It's possible but would be difficult.

If you have $100 or so you might try something like a Raspberry Pi. They just released a quad-core model 3 for $35.  It's a credit card sized computer.  You would need to get some extras to make that work though (hence the $100 I mentioned), and you'd need a TV with an HDMI connector and a keyboard to make it viable. This would be many times faster than what you have, and has several Linux distros which work on it, including Ubuntu.  It also has a thriving community surrounding it. I have a few older RPi model b+ boards I use. The b+ is iffy for desktop use, but the 3 should be good enough to watch pretty smooth video on a 1920x1080 (1080p) tv.

Of course if you are able and willing to get bigger hardware, Linux runs on the biggest computing hardware around.  It's just that there's a bottom end of practicality, and you're under that.

***Edit: **Where to buy a raspberry pi  depends on where you live.  I'm in the USA and bought mine at: *[https://www.adafruit.com/category/105](https://www.adafruit.com/category/105)

---

### Post by oldos2er on 2016-02-29
See [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by Hangman_ on 2016-02-29
> **1clue said:**
> IMO that hardware is not a good way to learn Linux. You will be fighting every step.  It's possible but would be difficult.

If you have $100 or so you might try something like a Raspberry Pi. They just released a quad-core model 3 for $35.  <...>  The b+ is iffy for desktop use, <...>

***Edit: **Where to buy a raspberry pi  depends on where you live.  I'm in the USA and bought mine at: *[https://www.adafruit.com/category/105](https://www.adafruit.com/category/105)

I saw this come across my desk earlier but haven't jumped at it yet.  Would this be considered the b+ you are mentioning? [URL="http://www.amazon.com/gp/product/B00MV6TAJI?smid=AHALS71WJO58T"]http://www.amazon.com/gp/product/B00MV6TAJI?smid=AHALS71WJO58T
[/URL]
Well, like I mentioned this is a temporary thing.  I have three other laptops (newer, more robust: 2G Ram, 4G Ram, 250 & 500G SSD drives, 1.2, 1.6, & 2.3MHz) & a desktop (20G Ram, 500G SSD, 4.1MHz) to update.
But I don't know Linux yet (I loved working DOS Shell & VBScript w/ WinXP so it should be relatively easy to pick up the command line) & I need to get proficient enough to troubleshoot any problems with the other laptops should any arise before putting Ubuntu on them.  I'm going to try this old machine & one other laptop for starters, then as I progress I'll move the others over.  My goal is to be completely Windows free by August.

What do you think, a worthy goal or too much to chew?

---

### Post by Hangman_ on 2016-02-29
> **oldos2er said:**
> See [https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Thank you SuperMod'der, this link & those connected to your signature are an excellent read.

---

### Post by 1clue on 2016-02-29
With newer hardware, if those laptops are relatively recent and have no funky hardware, then you will probably just install Ubuntu and it will work. User interface wise, you will probably just be able to browse around and find things just like on Windows.

Command line Linux, people who are determined will probably get it and people who aren't, well not so much.  When I got into Linux, the command line was what you had, a GUI was entirely optional and ridiculously unstable.

If you're not sure about Linux, then install VMware or VirtualBox and install Linux on that.  I recommend the 4g one for that.

---

### Post by coldraven on 2016-03-01
Another option is to buy an old laptop or netbook which is a more powerful than your junk one.
My criteria is that if it has a network socket and USB ports it is probably made this century :)
I picked up a mint condition Toshiba NB100 for £30 which can run Xubuntu easily. I also got a broken Samsung NP-N130 for free, a new keyboard was £8. It's running Linux Mint Cinnamon. Both of these have 1GB RAM. Installing from a USB stick takes about 30 mins. and everything including wi-fi worked immediately.
Welcome to the world of Linux, have fun !

Edit: Here is a handy link [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

