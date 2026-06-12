---
title: "after download/load can not find the program."
date: 2014-04-22
forum: New to Ubuntu
---

### Post by Jim_Murray on 2014-04-22
I have heard Linux is hard to get to know so I have avoided it until now when XP was blown up. I downloaded the UBUNTU ISO and burned it to a DVD. Then tried to install it. I continually got a herring bone pattern green colored screen. I left the machine running for several hours to see if that was a pre install screen or? I then decided that I would put the iso on a 16 g thumb drive. I was then able to move to the install screen and the program seemed to install up to a point then said it needed a restart to complete the install. I restarted and my XP desktop came up along with the Ubuntu logo flower. I clicked the flower and hit run and ultimately was informed that the existing copy of the program must be removed before the new installation could begin. I am now in that install/uninstall process and feel I am doing something wrong. Does anyone have a suggestion as to what I should do/try next?

---

### Post by jbaerboc on 2014-04-22
Hi Jim. Are you looking to install Ubuntu and remove Windows XP, or are you looking to install Ubuntu along side of your Windows XP? 

Assuming you're looking to replace you Windows XP installation completely are you booting from the DvD or into WinXP then running the DvD? If you are trying to replace Windows XP I would always recommend restarting the computer and letting it boot into the LiveDvD [most computer do this automatically if there is a DvD with an OS burned to it in your drive].

If you boot to the DvD it should give you 2 options. 1. would be to try ubuntu [just lets you testdrive it without installing] or 2. install ubuntu [installs to your hardrive and replaces WindowsXP or installed along side it dependong on options you choose.

If you can answer some of the above questions it might clarify for us what you'd like to do. Thanks.

---

### Post by Jim_Murray on 2014-04-22
unloaded the 32 bit version now reformatting the thumb drive then will try the 64 bit version. The machine is an old P4 3.06g with 3g ram, 250g hdd, NVidia 9400gt video had Win XP MCE SP3 on board.

---

### Post by Jim_Murray on 2014-04-23
I would like to get rid of XP so it would be a clean full install. I was booting straight from the thumb drive and after I came to the point where it advised to restart the computer, upon the reboot it went straight to XP. There was the UBUNTU icon on the desktop and when I ticked it, it directed me to uninstall the program prior to re-installing UBUNTU. I could not get a install from the DVD, all that came up was the UBUNTU name with several crawlers running along the bottom then it went into a herringbone pattern of green small bars. I felt it might be a corrupt disk so I re burned the ISO (this came from a completely different mirror) and again the same incident re appeared. I then re downloaded a fresh copy onto a thumb drive and that resulted in the above described result of re boot to complete the install but still had no OS button or other way to tick into UBUNTU other than the original install logo. I would reformat the c drive but do not want to loose XP until I'm sure UBUNTU is going to work. I should add that the ISO burns are accomplished on my Win 8.1.1 i5 8G machine which has a near new burner in it

---

### Post by Jim_Murray on 2014-04-23
I should also mention that the initial downloads were to the 32 bit version that I chose since my XP version was in 32 bit. The thumb drive version I have now is the WIN version in 64bit, I double checked to make sure I didn't try to run the Apple version in 64 bit.

---

### Post by monkeybrain20122 on 2014-04-23
Do you remember seeing something like these screenshots?

What did you do when screenshot #4 came up?
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by Jim_Murray on 2014-04-23
none of the screen shots ever appeared. (I had printed out this same info so I would have it to follow) All that I had was during the thumb drive install a print proclamation appeared stating " YOU MUST RESTART YOUR COMPUTER NOW TO COMPLETE THE INSTALLATION". on restart the machine went into Win XP and the Ubuntu logo icon appeared on the desktop. I ticked the icon and was informed that there was a copy of the program already installed and to uninstall it prior to installing another copy of the program. Yes, I did set my boot order so I could boot strait into the DVD and after that failed I then set the removable (thumb) drive. I have not tried to boot from "my computer". Perhaps I should try that next and tick the removable drive H icon from the running XP.

---

### Post by 3rdalbum on 2014-04-23
Jim, if you did not see any of the screenshots on that site, you did not install Ubuntu correctly.

Try burning another DVD of Ubuntu, using the Burn Image To Disc function of your burning software. Boot the computer from it by selecting it as the boot drive in the BIOS. You will NOT see Windows, you will be asked if you want to try Ubuntu or install Ubuntu. That is Ubuntu running already.

I don't think your computer is 64-bit capable. You would need 32-bit.

At no point during the installation will you see Windows. If Windows is running, you are doing it wrong. It is only after installation that you will have the choice of operating system to boot into.

---

### Post by Impavidus on 2014-04-23
Installing Ubuntu doesn't add anything to your Windows desktop. Windows doesn't even know Ubuntu has been installed. So if you do see anything, apart from an indication that the Ubuntu live disk is present, you didn't install it the right way. Did you use anything called wubi, the Windows Ubuntu installer? That's unsupported nowadays, so don't use it. You could best install as a real dual boot, by booting from the live dvd or usb.

The green herringbone pattern may be the result of a problem with the graphics driver. It can usually be solved. Read [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) and boot from the live dvd or usb. Often the nomodeset option is needed.

---

### Post by Jim_Murray on 2014-04-23
OK, I am going to burn another image, in 32 bit. Just for info I am using Nero burning rom to burn the ISO to disc. Is this not good? It has worked on all prior burns but that was in windows applications. Is Linux that different when it comes to ISO's ? (I have been computer literate since my first Timex Sinclair computer back in 1982. BUT this is my first experience in Linux)

---

### Post by sandyd on 2014-04-23
> **Jim_Murray said:**
> OK, I am going to burn another image, in 32 bit. Just for info I am using Nero burning rom to burn the ISO to disc. Is this not good? It has worked on all prior burns but that was in windows applications. Is Linux that different when it comes to ISO's ? (I have been computer literate since my first Timex Sinclair computer back in 1982. BUT this is my first experience in Linux)

It should work - some of us use imgburn and other tools, but all of the burning tools should create the ubuntu disk properly.

After creating the disk, boot up your computer, and do either

a) Set your bios to boot from cdrom, then hdd
b) hit the key that opens up the boot menu (this should display on the screen during bios post)

You should then see the ubuntu logo come up.

Choose either 'Install Ubuntu' or 'Try Ubuntu' (When choosing try ubuntu, you will get a icon on the desktop labeled 'install ubuntu' after the disc is finished loading.)

You can then choose 'take over whole disk' (or similar, the wording changes a bit each ubuntu release...) which will wipe out windows xp and install ubuntu over it.

---

### Post by Jim_Murray on 2014-04-23
OK, problem resolved (embarrassed to admit was my fault) I switched out my little monitor and went to the storage unit and picked up a large flat that I had. When I brought it back I hooked into the on board video and paid no further attention. My bios is set for external but on boot it will still show as loading, then as it switched to the video card is where the green herringbone pattern would appear. I realized my mistake as I was preparing to stomp the machine into oblivion. On changing the output to the monitor I again placed the ISO disk into the DVD and re booted. Problem resolved and as of now the program is loading. I would like to thank all for their suggestions and will look forward to conversing with all of you in the future. Thanks.

---

