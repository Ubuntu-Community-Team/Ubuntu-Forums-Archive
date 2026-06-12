---
title: "Won't boot after restart"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by WesternRyno on 2013-02-28
Phew, I could sure use a helping hand as I'm starting to feel I'm in over my head.  I really want to work this but am at a loss.  I will continue to read the forums for answers, but any help to get out of this nightmare would really be appreciated.  Thanks to anyone out there for their time assisting me. 

I put on a fresh install of Ubuntu 12.04 (ISO from Ubuntu.com) from a brand-new flashdrive on my new laptop and after installing the recommended updates (40 of them) from the update manager it now will not boot.

I've tried a variety of things but so far no luck.  The GRUB boot menu gives the following options:

1.)  Ubuntu, with Linux 3.5.0-25-generic
2.)  Ubuntu, with Linux 3.5.0-25 (recovery mode)
3.)  Previous Linux versions
4.)  Memory  test (memtest86+)
5.)  Memory test (memtest86+, serial console 115200)
6.)  Ubuntu, with Linux 3.5.0-23-generic (on /dev/sda2)
7.)  Ubuntu, with Linux 3.5.0-23-generic (recovery mode) (on /dev/sda2)
8.)  System setup


**Option 1** leads me directly to a black screen with an unblinking cursor in top right, or a purple screen of inactivity.

**Option 2** leads me to the Recovery Menu.

- Resume leads me to a black screen where with an option to type my   login: and then password, after which I get my login@computername:~$ with a blinking cursor.  Don't know where to go from here.

- Repair broken packages tells me no upgrades are available, do you want to start the upgrade.  
Continue [yN] Details [d]
When I try an option it then says END

- fsck gives a few details and leads me back to Recovery Menu
- failsafeX leads me back to the Recovery Menu

**Option 3** lets me try to boot into Linux 3.5.0-23-generic or the same in recovery mode.  I get a purple screen of inactivity in the first and the Recovery Menu offers the same results as the previous Recovery Menu notes from above.

Neither of the Memtests work and the last two sda2 options are for an installation I mistakenly made on my SSD drive.

Am I looking at installing 12.04 again as my best option?  I would hope to avoid this if possible, as I've done a number of them already, but more importantly, how can I avoid this happening again even if I do a fresh install.

Thanks again for any help forthcoming.

---

### Post by WesternRyno on 2013-02-28
Attempting to run Boot Repair from flashdrive I used for installation.

A check for errors revealed no errors found.

When I try to run a boot repair from a terminal I get an error message and a crash report:

ExecutablePath
   /usr/bin/add-apt-repository
Package
   python-software-properties 0.82.7.3
ProblemType
   Crash
Title
   add-apt-repository crashed with error in get_ppa_info_from_lp():(6,"Couldn't resolve host 'launchpad.net'")
Traceback
ApportVersion
   2.0.1-Oubuntu17.1
Architecture
   amd64
CasperVersion
   1.315.1
CrashCounter
   1
Date
   Thu Feb 28
Dependencies
DistroRelease
   Ubuntu 12.04
InterpreterPath
   /usr/bin/python2.7
LiveMediaBUild
   Ubuntu 12.04.2LTS "Precise Pangolin" - release amd64 (20130213)
MarkForUpload
   True
PackageArchitecture
   all
ProcCmdline
   /usr/bin/python/usr/bin/add-apt-repository ppa;yannubuntu/boot-repair
ProcEnviron
   TERM=xterm
   PATH=(custom, no user)
   Lang-en US>UTF-8
   SHELL=/bin/bash
ProcMaps
ProcStatus
ProcVersionSignature
It goes on...
UnreportableReason
   This is not an official Ubuntu Package.  Please remove any third party package and try again.
UpgradeStatus
   No upgrade log present (probably fresh install)

Sigh.  Guess I'll have to make a flashdrive version?

---

### Post by fdrake on 2013-02-28
try to update-grub:
select "Recovery Mode" > "upadate grub bootloader" > press "ok" and then reboot (cross fingers).

if still no luck, then you may need to reinstall the bootloader.
follow my tutorial (you will need a cd/usb install). Let me know if you have questions
[http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/](http://theguyonthe3rdfloor.wordpress.com/2013/02/28/how-to-install-grub-2/)

---

### Post by WesternRyno on 2013-02-28
@fdrake  Thanks for your reply!  I had a read of your blog and will keep it in hand.  I'm pretty sure I took the update GRUB option and it didn't lead me anywhere, however, I did not follow it to the degree that your instructions outline.  In the interim while the forums were down, and after trying all that I could, I decided to re-install Ubuntu 12.04 which it is currently doing.  My worry of course is that this situation could occur again so I really hope to get to the bottom of this.

Ideas that I have so far from a noob's perspective are:

1.  An issue with the graphics card?  I have a Nvidia 610M which came up failed after a test.  I received this report:
graphics/compiz_check Failed Xlib:extension "GLX" missing on display.

2.  Wiping Windows 8 has done something to compromise?  I have a UEFI and an SSD.  My gut tells me it isn't this, but I don't have the experience to accurately say.

3.  Something I updated?

So, when the installation is complete, I plan to run a boot repair if possible and attempt to install the correct drivers for my card to see if the issues can be resolved.

Still very open to suggestions and input as to why this complete boot/load failure reared it's head in the first place.

---

### Post by fdrake on 2013-02-28
the puprple screen problem that you had before may be cause by a kernel problem. When grub calls initiate your kernel, the kernel is not responding. Idoupt it's a graphic drive problem, since the kernel initiate xorg with the graphic modules. It is something else. If you have the same problem boot into recovery meny or into an older working/stable kernel and reinstall the non working kernel. Check also for errors.

---

### Post by WesternRyno on 2013-02-28
Thanks again for replying to my issues, I sure do appreciate any input.  I agree with you that the crashing screens are related to a kernal issue as i have no issues on a fresh install.  It was only after downloading and installing the updates, which I assume contained a kernal in it, that the crashes initiated.

Some additional information that could be of value:

I have multiple versions of Ubuntu installed, including one on my SSD drive.  I kept this so I could consistently access the GRUB/BOOT options, but I'm sensing that this may be causing underlying issues, perhaps using too much space or simply conflicting things?

Ubuntu 12.04 is not recognizing a driver for my Nvidia GEForce 610M graphics card when I look in details and a system test shows a fail and the following message:

graphics/compiz_check Failed Xlib:  extension "GLX" missing on display

I've been pouring over the forums and will be taking the following steps unless advised or guided otherwise:

1)  Remove the installation from the SSD.  I hesitate to do this as I value the ability to access the boot priority settings where I can ensure to boot from a flashdrive.  This has been my failsafe in case I need to put fresh installs on, which unfortunately I have mastered now from multiple experiences.

2)  Attempt a memtest again.  I get an error:  unknown command 'linux16' message when I try this.  I would like to rule out the possibility of corrupted RAM.

3)  Download and install the appropriate Nvidia driver for my graphics card.  I did this once but got a corrupted message and feel that I should address steps 1-3 first.  I have also tried the other solutions offered in the forum and in the AskUbuntu forums.  Bumblebee could be an option here.

So that's where I'm at for anyone who has anything to offer, I'm collecting two-cents at a time!  Thanks again.

---

