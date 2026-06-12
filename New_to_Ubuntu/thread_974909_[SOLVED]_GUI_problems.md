---
title: "[SOLVED] GUI problems"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by iwishiwuzskiing on 2008-11-07
I'm trying to install Ubuntu 8.1 for the first time. The machine I'm using is a new lenovo w500 running vista busniness 64-bit.

I tried installing ubuntu via the Wubi installer, and as far as I could tell the installation was completed successfully, but when tried to boot ubuntu, it loaded a command line rather than the desktop.

I tried startx, and it returned a "fatal server error: no screens detected" error. I'm new to linux and not sure where to go from here. any help would be greatly appreciated

thanks


ps. My graphics card is an ATI Mobility Radeon HD 3650

---

### Post by bscbrit on 2008-11-08
Hi, welcome to the forum.

The problem you are experiencing might be due to some problem in 8.10 although I cannot say for certain.  However, if this is your first time installing Ubuntu, I would recommend that you try to install 8.04 first.  This a a more stable version - 8.10 has only just been released and it is not uncommon for there to be a few small bugs when a new release is issued - and it is more likely to install without a hitch.  Just because 8.10 has been released it doesn't imply that 8.04 is out of date. In fact, 8.04 is a long-term support version which has been specifically designed for stability and it will be supported and updated until 2011.

However, just to check the obvious.  Where did you get your version of 8.10 from?  If you downloaded it yourself, are you sure that you have not got any errors on the disk?  If you don't know how to check, let me know.

Next, start the computer in recovery mode i.e. when the menu appears select the second ubuntu option rather than the first.  If you don't recall seeing a menu, it should be displayed immediately after the BIOS has completed its own checks.  If you see a countdown on the screen, then press the Esc key to see the full menu.

During the boot of recovery mode, it will present to you several options.  One of these is 'xfix'.  Select this and the computer will attempt to correct your screen configuration.  When it returns to the menu, select the first option which will allow you carry out the rest of a normal boot.  If you get your screen display back - you are finished!  If you end up back at the command line we will still have some way to go, and there is no guarantee that one of the few bugs that do exist in 8.10 will not appear.

Let me know how you get on or whether you wish to try to install 8.04 first.

---

### Post by iwishiwuzskiing on 2008-11-08
I tried 8.04 with similar results, I also tried the 32 bit version with no success there either. I also tried installing fedora, to see if that worked any better, and had similar problems and errors, which leads me to believe that this is a problem with my machine rather than ubuntu.

I also tried booting into recovery mode like you suggested, but when I got to the menu I got options such as "start installer in normal mode", and "start installer in safe graphics mode", so maybe I'm not getting the full installation that I thought I was getting. I tried running the installer in safe graphics mode, and it seemed to go fine for a while, then it said "starting ubiquity", then did nothing for a minute then showed an error that was something to the effect of "failed to start x server after 60 seconds" then went straight to a command line

---

### Post by bscbrit on 2008-11-08
I agree, it looks very much like a hardware problem.  With 2 versions of Ubuntu an one of Fedora failing to load you either have hardware faults or a very unusual computer.  I'm sorry that it hasn't worked out for you.  Have you ever run windows on this computer, and are you able to use windows now?

EDIT - You say that its a new Lenova running Vista.  I'm surprised that it is causing such problems.

---

### Post by bscbrit on 2008-11-08
You **are** trying to load the 64 bit version of the software and not the 32 bit, aren't you?  The 32bit should still run, I believe, but I might be mistaken on that.

---

### Post by bscbrit on 2008-11-08
You initially started by trying to install the Wubi Ubuntu 8.10 version.  This is a version of Ubuntu that runs as if it were a Windows program.  It doesn't, or at least I believe shouldn't, try to take direct control of the hardware because it should be working as any other Windows program would.  I am at a loss to understand how you are encountering display problems if your windows installation is fully functional.  Perhaps I need to do some more research on Wubi, having never installed it myself.

You then tried installing a different version of Ubuntu (8.04) and your comments suggest that you tried both 64 bit and 32 bit programs.  You also tried to install Fedora - which as far as I know ( but I might be wrong ) does not have anything similar to Wubi.  Therefore, you would have had to repartition your hard drive and carry out a completely new installation.  Did you do this?

In so doing, we have strayed far from the original problem (displays not working in Wubi) and are now looking at something completely different.

What I need to know is what have you done so far, and what are you hoping to achieve?  Does your Windows system still function correctly (if it does, it proves that the hardware is serviceable, and if it doesn't you might have corrupted it while trying to install Ubuntu/Fedora)?  If you switch the computer on, with no disks in the CD/DVD drive - what do you see?  Does it boot directly into Windows, do you see a menu giving you the option to boot either Ubuntu or Windows, or does it boot directly to the Ubuntu commandline?

And it is now way past my bedtime.  I will be back online tomorrow.  I'll chat to you then.

---

### Post by handydan918 on 2008-11-08
> **iwishiwuzskiing said:**
> I'm trying to install Ubuntu 8.1 for the first time. The machine I'm using is a new lenovo w500 running vista busniness 64-bit.

I tried installing ubuntu via the Wubi installer, and as far as I could tell the installation was completed successfully, but when tried to boot ubuntu, it loaded a command line rather than the desktop.

I tried startx, and it returned a "fatal server error: no screens detected" error. I'm new to linux and not sure where to go from here. any help would be greatly appreciated

thanks


ps. My graphics card is an ATI Mobility Radeon HD 3650


ATI cards always require the proprietary drive to work properly.
IMHO, I would recommend not using WUBI . It sounds like a good idea, but there are some issues with it with just this sort of scenario. 

As a general overview, I would suggest resizing the Vista partition (using the native resizing tool in Vista!) and installing Ubu to the free space. You have a greater chance of the installer correctly identifying hardware on a native (non-wubi) install.

---

### Post by iwishiwuzskiing on 2008-11-08
bscbrit-Windows still works fine for me. When I boot, I get a menu with the options to boot either windows or ubuntu. When I installed fedora I did repartition my hard drive and do a new installation, and I still ended up with similar errors about not being able to start x server or find display devices

handydan-I'll give the repartitioning/install a shot, and also try to get the drivers and let you know how it goes.

---

### Post by steveneddy on 2008-11-08
I would have this post moved to the WUBI area of the forums. I believe that you would get more responses there.

I'm sorry that I can't help you with WUBI.

Personally I would just make a partition and install it.

The install should be flawless on any Lenovo machine.

---

### Post by papuccino1 on 2008-11-08
Yeah, try the Wubi area out :P

---

### Post by handydan918 on 2008-11-08
"Yeah, try the Wubi area out :P"

Just the fact that there IS a wubi area should say something, doncha think? 


There isn't a grub area...

Another brilliant idea, poorly executed.

---

### Post by bscbrit on 2008-11-09
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

has a section relating to display issues.  You might find it useful but, without installing Wubi on one of my computers, I cannot attest for how good it might be for you.  Apparently, you should be able to select different options at boot time to alleviate some of the display problems that you are seeing.

---

### Post by iwishiwuzskiing on 2008-11-09
I repartitioned, and tried to install off a cd as handydan suggested, and could not get ubuntu to install at all. First I tried the normal installation, and I got a screen with the ubuntu logo and an orange progress bar underneath. The progress bar got to about 90 percent, and then the screen cut to black with a cursor in the top left corner. It stayed there for a minute or so, then some text flashed by too fast for me to read, and left me at a command line. I rebooted without the disc and my computer went straight to windows. 

I tried the installation again in safe graphical mode, and with the command line options "floppy.floppy=thinkpad" and "vga=771", because the help file said that those options might be necessary for thinkpads or laptops experiencing graphics problem, but I still couldn't install

I checked the disc using the option from the install menu, and it said my disc was fine

Could problems with the display/graphics card be preventing it from installing, or is there some deeper problem here?

---

### Post by bscbrit on 2008-11-09
Unfortunately, there are one or two issues with the display software in 8.10.  It has been completely restructured and, while it is a great improvement for most people, it is causing all sorts of mysterious problems for a handful of others.

But you said earlier that you had also tried to instal 8.04 and Fedora.  If you saw the same or similar problems with each of them then I would suspect your hardware or the WUBI software.

I would be very tempted to use GParted to reduce the size of your Vista partition and then do a clean install from a standard desktop into the newly created space.  I would use 8.04 rather than 8.10 because it will avoid any of the problems that I mentioned in the first paragraph.

The symptoms that you are describing are unusual and I cannot suggest a logical way to approach them that might stand any reasonable chance of success.  Ultimately it is your decision but it seems to me that the WUBI option is not really for you.

Let me know how you would like to continue.

---

### Post by iwishiwuzskiing on 2008-11-09
I'm going to give 8.04 a shot. Also, a few posts back it was mentioned that ATI hardware requires proprietary drivers to function properly, how do I go about installing them.

---

### Post by bscbrit on 2008-11-10
System -> Administration -> Hardware Drivers

and follow the instructions from there.

Good Luck.

---

### Post by iwishiwuzskiing on 2008-11-11
Installing version 8.04 worked fine.
Thank you all for your time and help!

---

### Post by bscbrit on 2008-11-11
Great news!  You're welcome.  Can you please use Thread Tools to mark this thread as SOLVED - it might help others who experience similar problems.

Good Luck, and I'll see you around the forums.

---

