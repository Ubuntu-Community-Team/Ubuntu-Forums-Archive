---
title: "Problems when unplugging mains power"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by WolfBroth3r on 2012-05-06
Hi All,

I have a Dell Inspiron Duo that I have recently dual-booted with Ubuntu 12.04 (upgraded from 11.10) and Win7. I need help with a power issue though;

When I first installed 11.10, I have issues where when the laptop was plugged into, or unplugged from, mains power it crashed to a black screen with a load of text printed over. From there all I could do was hard-reboot. After some searching online I found a guide to disabling acpi which fixed the problem (update GRUB), but removed my battery status icon and possibly resulted in my laptop running incredibly hot under Ubunutu (I cannot be certain that acpi was the cause for the latter though).

After upgrading to 12.04, I followed another guide that detailed how to cool the system down - again by updating the GRUB runline. Now, with the new set-up my battery icon is back (as is acpi), but I am again left with the crashes when unplugging the power cord.

Does anybody know of a fix for this (pretty significant) bug that does not involve disabling acpi? I have tried another fix that requires downgrading pm-utils, but that had no effect.

Many thanks!

---

### Post by Ms. Daisy on 2012-05-08
If you don't get any suggestions, I recommend you ask a question on launchpad about this. You can include a link to this question in launchpad which sounds like the same problem but in 11.10:

[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/881043](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/881043)

---

### Post by christoph411 on 2012-05-11
You should really check out this thread. It has pretty much anything you would ever want to know about the Duo. I have a Duo too and there are a lot fixes and a there's a ton of information, even though sometimes it takes a while to sort through the 71 pages (but luckily most of the fixes are in the OP). As far as I know, this bug has been reported but will most likely never be fixed, since it has been marked as invalid/wont fix. It seems that there is some glitch/abnormality in Dells BIOS for the Duo that causes the acpi to work in a nonstandard way. Thus, the kernel developers don't want to include a nonstandard workaround in the kernel, they think it is Dell's responsibility to fix their BIOS problem. Apparently this could be resolved with a BIOS update from Dell, but I don't believe they have ever released a BIOS update for the DUO, let alone an update with a fix as substantial as this. 

[http://ubuntuforums.org/showthread.php?t=1658635&highlight=inspiron+duo](http://ubuntuforums.org/showthread.php?t=1658635&highlight=inspiron+duo)

The way I deal with the "kernel panic" problem you mention is pretty simple. I never found a real fix, but I remember in a previous version the kernel panic didn't used to happen (maybe in 11.04??). But anyway, I boot my Duo unplugged and have it set so it suspends when the lid/screen is closed (the default behavior). So, if you close the screen so it suspends and then plug it in to charge, it doesn't crash. Then you can just pull it off the charger, open the kid to wake it from suspend and use it again without any problems. Unfortunately it will still crash if you open the lid again while it is still plugged in. If you want to use it while on the charger, you have to power it off before plugging in, put it on the charger, and reboot, but you also have to shut it down again before unplugging it and using it. This all sounds quite incovienient, but you learn to live with it. :) It's pretty much not that much of a problem if you either use your laptop unplugged for the majority of the time or use it plugged in a lot. It's just when you do a lot of switching back and forth that things get pretty annoying. I'd recommend reading through that thread though when you have a bit of free time, its undoubtedly the most comprehensive collection of information on running Ubuntu/Linux on the Duo on the web haha! :p Good luck with your Duo and Ubuntu.

---

### Post by WolfBroth3r on 2012-05-15
Hi christoph411, Ms. Daisy, thanks you for your replies, I'll give them a try :-)

---

### Post by chofo1979 on 2013-01-05
Hello, I know the post is somewhat old, but I ran into the same problems and while googleing and going into forums to find a solution I managed to find one so I will share here to help others too. I have to say I am new in the Linux world.

I was having the same issue: when unplugging the ac adapter, the computer just froze. Had to press power button 5 secs to turn it off and then on again. 

I tried turning off acpi. That would solve the problem but it will leave me with only 1 core working (I have a Pentium B940 2.0GHz DC). Plus the battery icon obviously disappeared.

So here is a solution that solved this problem, plus my backlight buttons on the keyboard now work perfectly:

First open terminal

Edit /etc/default/grub.

In the grub file, 
change GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to be GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
Save the file.

Then do sudo update-grub
close terminal


Then go to Ubuntu Software Center
search for 'pm-utils'
click on 'more info'
on the add-ons: uncheck 'Utility to control ATI Radeon backlight functions on laptops'
click on 'apply changes'

close and RESTART!

That solved the 2 issues for me. Hope I can help someone.:)

---

