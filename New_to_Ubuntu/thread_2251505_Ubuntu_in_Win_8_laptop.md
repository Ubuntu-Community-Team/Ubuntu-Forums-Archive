---
title: "Ubuntu in Win 8 laptop"
date: 2014-11-04
forum: New to Ubuntu
---

### Post by ray9 on 2014-11-04
I installed ubuntu 14.04LTS in my HP lap top that came with win 8 about a year ago.  I could never boot into ubuntu, I had to get into ubuntu the hard way.  Last nite while doing this I noticed that had a 32 bit version of ubuntu installed and figured that was why I couldn't boot into ubuntu because my lap top is 64 bit and win 8 is too.  So I reinstalled ubuntu this time with the 64 bit version.  The installation went fine and there is a boot loader that shows win 8.1(I upgraded) and ubuntu when starting up.  But, after I click on the ubuntu square I get a windows error screen  saying "Windows boot manager failed to start..................blah blah file  \ubuntu\winboot\wrbidr.mbr" On the bottom of the screen it says "ENTER=OS" on the left side and "ESC=UEFI Firmware Settings" on the right side.  I click on "ENTER=OS" and it shuts down.  So I made a "Boot Repair Disk" but I can't get it to run in win 8.

What can I do to fix this?

---

### Post by sandyd on 2014-11-04
> **ray9 said:**
> I installed ubuntu 14.04LTS in my HP lap top that came with win 8 about a year ago.  I could never boot into ubuntu, I had to get into ubuntu the hard way.  Last nite while doing this I noticed that had a 32 bit version of ubuntu installed and figured that was why I couldn't boot into ubuntu because my lap top is 64 bit and win 8 is too.  So I reinstalled ubuntu this time with the 64 bit version.  The installation went fine and there is a boot loader that shows win 8.1(I upgraded) and ubuntu when starting up.  But, after I click on the ubuntu square I get a windows error screen  saying "Windows boot manager failed to start..................blah blah file  \ubuntu\winboot\wrbidr.mbr" On the bottom of the screen it says "ENTER=OS" on the left side and "ESC=UEFI Firmware Settings" on the right side.  I click on "ENTER=OS" and it shuts down.  So I made a "Boot Repair Disk" but I can't get it to run in win 8.

What can I do to fix this?

You did a WUBI installation - which is not compatible with UEFI. Uninstall WUBI from Windows, then

Try booting from the DVD/USB and see if the installation works from there.

---

### Post by oldfred on 2014-11-04
Only use Something Else to install. Bug is still in most versions you download.

 Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but mulitiple drive installs must use Something Else. And fix is not in current versions.
[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192"]https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192

[/URL] Backup efi partition and Windows partition before Install of Ubuntu. If you have backups then any install issue, user, hardware, or software can then be restored to as before.

Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[URL="https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192"]
[/URL]

---

### Post by ray9 on 2014-11-04
How do I uninstall WUBI and where can I find "Something Else"?  And thank you for the replies!

---

### Post by westie457 on 2014-11-04
Hi you uninstall wubi using 'Remove a Program' while Windows is running. It should all be removed in one step.

The 'Something Else' is an option of the installer when using a Live USB/DVD.

---

### Post by ray9 on 2014-11-04
I get it.  Something else is the option in installation.  I can't get the cd to run.

---

### Post by ray9 on 2014-11-04
My programs just list ubuntu, no WUBI

---

### Post by westie457 on 2014-11-04
Uninstall Ubuntu, that is the wubi installation.

While Windows is running go to Power Options in the Control Panel click on 'options that are hidden' or something like that and disable 'Fast Boot'. This will force Windows to fully shutdown instead of going into the 'Hybrid sleep/hibernation' that usually happens. Also this action will/should stop some of the issues that a lot of people have.

---

### Post by oldfred on 2014-11-04
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You need DVD not CD as install is way to large. Usually better/faster to use flash drive.
From UEFI menu you should have two boot options for DVD/flash. One is UEFI and the other BIOS/CSM. 
Must better to have both systems installed in same boot mode to avoid issues.

More info in link in my signature. Backups important.

---

### Post by ray9 on 2014-11-04
Right, I meant DVD.  I got sidetracked for a few hours, back at it now.

---

### Post by ray9 on 2014-11-04
Right, I meant DVD.  I got sidetracked for a few hours, back at it now.

---

### Post by ray9 on 2014-11-04
I'm really green at this.  I don't remember how I did it a year ago.  When I reboot with the Ubuntu disc in the laptop it doesnt start.  Is this the way it's supposed to be?  I think I can start it from within win8 but how can I shrink win with it running?  Is there a step by step anywhere?  Also I can't find a 14.04LTS Live CD/DVD.

---

### Post by JeQhdMD on 2014-11-04
You get 14.04 from the Ubuntu web site or from a site such as distrowatch.com.   Plus another 100 or so websites probably have it. ALso, your BIOS may need updating to show booting from dvd/cd optical disk as top priority, (or if the iso image of ubuntu 14.04 is on flashstick, then that needs to be the top listing in boot order).  Only the 64 bit version will work with a UEFI system.  When in system/setup (efi/bios) did you disable fast boot?

---

### Post by yancek on 2014-11-04
Starting it from within windows 8 will only start a wubi install and the Ubuntu website specifically states wubi will not work with windows 8.  When you boot your computer, you should see the HP logo on screen and at the bottom it will tell you which key you need to tap to "enter setup", usually with HP it is F10.  Go to the Boot tab and set the DVD drive to first boot priority and reboot with the Ubuntu DVD in the drive.

---

### Post by ray9 on 2014-11-04
Got it going.  Thanks to everyone for the help.

---

