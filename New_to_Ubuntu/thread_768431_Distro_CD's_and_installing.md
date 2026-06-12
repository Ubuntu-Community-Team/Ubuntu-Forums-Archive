---
title: "Distro CD's and installing?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-04-26
Hello

can anybody help me with installing Linux distro's from CD.

Here at home, i own 2 computers.

1) WindowsXP machine (pentium 3 MMX)  200 megs of ram
2) Linux xubuntu machine...(pentium 2)  200 megs of ram

i have installed VirtualBox into both machines.

I have downloaded several Linux distro's from the web and CD burned them correctly......at low speed.

out of the 7 distro's downloaded....i discovered that every single distro works inside a virtualbox and boots and intalls....this is no matter which computer i use....they all work

however...when i try the CD distros on my actual FLATENNED machine (pentium 3)....they often do not get beyond a BOOT prompt....some of the distros go for about 2 minutes of install and then get errors....(can't find screens...or other errors like CRC errors)


so basically...these burned Distro CD's won't install of my RAW machine....but every single distro will boot and do a LIVE install when used inside a virtualbox...

so clearly there is no problem with the CD disks....or any of my hardware while it sits in a host OS

i realize that my RAW machine is having problems between it's BIOS and these Linux distro CD's....kernel issues seam likely to me...

my BIOS looks for CD drives correctly....but the LIVE boot ups of these distros always fail near the very start...

how do i go about making a BOOTABLE linux CD with the KERNEL already there....a 2.6 kernel?...so as to then be able to put the Distro CD in the drive.... and get it to boot up into  live linux...

i see that all virtual boxes always ask what kernel your OS is gonig to be using...

some Distro CD's i try say....can't initialise graphics when tried on my raw machine...

but non of these errors happen if the distros are installed and booted from within virtual boxes.....so

thanks

Vince.

---

### Post by frup on 2008-04-26
Virtualbox emulates generic hardware which usually can run Linux. It is possible that there is a piece of hardware you are using which Linux just can't run on (yet?). The generic piece virtualbox provides does not relate to your actual hardware.

Do you have any idea what isn't working? If it's screens/graphics do the installations have a safe graphics mode? I'm guessing you aren't running Ubuntu or Kubuntu on those specs. What distros have you tried?

---

### Post by vinceUUUU on 2008-04-26
Hello

I understand what you say. Virtual box must put in a generic layer of virtual compatable hardware or something...

yes..most of the distro's have options at boot...for old graphics cards and things like this...but every option fails to boot....tried many of the options...

the errors vary from...... CRC errors...to just arriving at a boot prompt (stalling after the kernel)....

boot>

to messages like "can't initialise graphics"

to "no screens found"

they stall and fail at different points during the install process....

but again...NON of these distro's fail when tried from within virtual box's

----------------------------------------------------------

the distros i have downloaded and burned are

PCfluxOS  (Tiny flux)
Simpleslax
Slitaz
PUD linux
Wolvix
Antix Mepis
Slax
Debian Base

most of these Distros' are small....200 megs or 240 or 190...and Slitaz is just 21 megs

does this mean that they do not contain the Library of drivers for old hardware?

but if that were so...then why are the distros written for old hardware.....if they do not contain the chip driver library's...?

Antix and others are specifically for pentium 2 machines...

the only distro's that boot and install and work on my raw machine(s) are....

Xubuntu and Kubuntu distro's....both of these CD discs are ORIGINAL GENIUNE discs that i purchased..

thanks

Vince.

---

### Post by ghost_ryder35 on 2008-04-26
edit: just read the post you posted above mine.... 
You should check out you BIOS and disable any options that rely on the OS usually things to do with some graphics cards that may be built in and hard drives.

---

### Post by mikeyphi on 2008-04-26
You could check to see if you have a RAID in operation? That would cause problems with straight installs.
If so, there are several guides in the wiki

---

### Post by frup on 2008-04-26
Are you aware what type of graphics cards these computers are using? Maybe try googling for their linux compatibility and any hacks that exist.

Have you considered puppy and damn small linux? Not as easy to use but sort of specialised towards older computers.

---

### Post by vinceUUUU on 2008-04-26
Hello

thanks for your ideas...

the raid possibility does not ring any bells....

but the idea the certain bios settings concerning video chips could be looked into....caching things...

but then again....this does not explain the few distros that don't even crawl past a boot prompt...

the video chips are very common....3d voodoo chip....and SIS 530

both about 8 years old

Antix even has a specific setting for SIS chips at boot...but still does not work...

they are both ALL IN ONE motherboards....

thanks

what about my idea of making a BOOT CD with kernel already loaded up?.....to help these other distro discs?

thanks

Vince.

---

