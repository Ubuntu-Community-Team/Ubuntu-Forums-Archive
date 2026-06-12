---
title: "Black screen after installing 12.04 LTS?"
date: 2013-02-06
forum: New to Ubuntu
---

### Post by evertonmint on 2013-02-06
**Re: Boot's to Black Screen and can't do anything**             
                                                                I'm having a  similar problem, I put the CD in and pressed 'TRY'  after a while I  decided to install 12.04 LTS  from the menu on the left. After (taking  disk out) rebooting, I arrived at a black screen just after the bios  screen (where windows welcome used to come in).
I don't use a 'monitor' I use my TV set to PC INPUT. When the black screen appears I get an 'information' box 'OUT OF RANGE'!

Any Idea's? All that is in the PC is the usb locater for my wireless mouse.
I had previously formated the drive so no O/S installed.

Regards

Evertonmint.
PS i am now back on the CD trial version.

---

### Post by grahammechanical on 2013-02-06
If Ubuntu is the only OS on the disk then you will not see the Grub boot loader menu. But one is there. You need to press either Esc or Shift. I cannot remember which as I have never needed to do this.

At the Grub menu press E. That stops the countdown timer and puts you in the Grub Edit mode. Look for a line that says

> quiet splash

and change it to

> nomodeset

Then press F10 to load Ubuntu.

This change will do two things. 1) You will see messages during the loading process. If the process stops, those last messages will be useful  for diagnostic purposes. Write them down and post them here. 2) Ubuntu will load without setting a video mode. This sometimes get us to a desktop.

If you get to a working desktop, look for Additional Drivers in the Dash and run that utility and activate a video driver. That might fix the problem.

Ubuntu normally gets information about the display (monitor) from the monitor itself. It gets this information as part of the loading process. It could be that the TV is not providing that information.

You can also use 'detect displays' in the Displays utility or in the utility that was installed with the proprietary driver.

Regards.

---

### Post by ACubed10 on 2013-02-06
Yes mine did this. What graphics card do you have in the computer?  I had to boot into safe mode and was able to run all updates and install the driver from the additional drivers app which allowed me to boot normally. I have an Nvidia GTX 550 Ti

After that 12.04 has worked perfectly for me. In 12.10 my card worked right out of the box. 12.10 was still a little too buggy for me

---

### Post by evertonmint on 2013-02-06
I'm running the CD, if I go into Home Folder / Devices / 317 GB, All the folders are there for Ubuntu, what folder would I need to open?

Is it possible to do it this way?

Thanks for the feed back.

---

### Post by ACubed10 on 2013-02-06
> **evertonmint said:**
> I'm running the CD, if I go into Home Folder / Devices / 317 GB, All the folders are there for Ubuntu, what folder would I need to open?

Is it possible to do it this way?

Thanks for the feed back.

have you installed Ubuntu yet?

---

### Post by evertonmint on 2013-02-07
Yes it's all loaded just a black screen. I've been trying the suggestion of grahammechanisal, pressing Esc / SHIFT but, nothing as happened. I load up the CD and do a live session I can see all the folders on the drive in the Home folder / devices menu / 317 gb = Ubuntu

The 'BOOT folder on this drive has a GRUB folder;
In the 'GRUB' folder all the files have a 'musical' annotation on them?

Regards

evertonmint.

---

### Post by evertonmint on 2013-02-08
When I play the CD in live mode, I can access the terminal, when I 'sudo apt-get update' it tries to upgrade to the CD? Is there anyway I can get it to upgrade to the drive I installed Ubuntu on? Maybe then I can install drivers for the screen (tv).

Regards

evertonmint.

---

### Post by evertonmint on 2013-02-12
I had to replace my TV with a proper monitor then reinstall,then go to settings and install additional drivers.After I put my TV back on it still takes about 1.30 seconds to boot. After the boot page it goes to 'out of reach for 30+ seconds then a blank screen for thirty seconds+, it then boots into the Unity desktop.

Regards to all.

evertonmint

---

