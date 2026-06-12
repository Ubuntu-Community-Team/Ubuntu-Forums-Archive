---
title: "Black screen after fresh install"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by djen9999 on 2011-09-18
I decided to wait until I did some hardware upgrades before upgrading to Natty.  I just upgraded to two hard drives and did a fresh install on the smaller drive.  The boot splash comes on very briefly then the screen goes black and that's it.  Nothing after that.  I just have a black screen staring me in the face.

The live CD works fine and Maverick was fine before the install.  
 
I find it odd that the boot splash comes on then quickly vanishes.  Any ideas?

---

### Post by Blasphemist on 2011-09-18
There is a thread just waiting for you to use it. [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

The first few posts walk you though the troubleshooting of exactly what your issue is. You can post back here if you have questions. The OP does still check that thread though if you do use it.

---

### Post by anewguy on 2011-09-19
It's possible this might also be an issue that can be solved with "nomodeset" on the boot line, then installing a driver after it boots.

Dave ;)

---

### Post by djen9999 on 2011-09-19
Thanks, I was sure there was a thread but I wasn't sure where to find it.  I'll check it out

---

### Post by djen9999 on 2011-09-20
I've tried just about everything in the tutorial with no luck.  I think going back to a previous version of the Kernal may help, but I have no idea how to go about it.  Any help?

---

### Post by pierreyy on 2011-09-20
what are your specs?? what kind of graphics card is installed on you computer?

---

### Post by djen9999 on 2011-09-20
> **pierreyy said:**
> what are your specs?? what kind of graphics card is installed on you computer?

The video card is an integrated GeForce 6100. I have 2 gig. of memory and two hard drives.  My desktop system is home and I'm at my office right now.  In going over some old posts, I noticed that I had a similar problem over two years ago that stemmed from an improper video driver being installed. The recommended driver was the 180 but the 96 was the proper driver for my system.  The major difference was that in that case I was able to get my GRUB menu and boot into recovery mode.  In order for me to get my GRUB menu now, I have to press the shift key (and hold it down) during load.  If I try to get into recovery mode now, I still get the black screen.

You guys have been great in the past and I want everyone to know how much we appreciate your hard work to keep us up and running.

---

### Post by Blasphemist on 2011-09-20
Can you tell us what happens at this stage of the troubleshooting process from the thread above?
> Step 2 "Does the Linux Kernel Boot?" At Grub Menu, go into edit mode and boot into a text console (see instructions below)
- Yes. Go to Step 3
- No. Messages will be verbose on what is loading, what are warnings and what are error messages. Shortcut keys will start to work as the kernel modules load. If if stops at an error, you will be able to use the shortcut navigation cuts to review the errors. Depending on the error, if it is a kernel error, you may be able to reinstall or renew the kernel image. If it is a device module, at least you have somewhere to go to reload that device module or driver.,,, Goal is to get a "booting kernel."

Step 3. From the Grub Menu, try to boot in Rescue mode/low graphics.
- If Yes, look for addtional drivers and install recommended driver.
- If No, goto Step 4 to verify that linux kernel will boot.

Step 4. Can you boot a graphical Xseesion from a text console session? From the command line type 
Code:
```
sudo service gdm start
```
- Yes No black screen/No problem... should boot straight from the grub menu.
- No. Reboot and start testing and changing gfx_modes and kernel boot graphical modes, still booting into the text console before you try to start an Xsession. Going this way, you will have more of a possible chance to be able to toogle between a graphical session or text terminal session (sometimes). ...and at a text console, at least you have the abilty to install files and make changes to config files. And if you can get back into a command prompt, you could then stop the gdm service that is locked.

You can stop the gdm service via
Code:
```
sudo service gdm stop
```


---

### Post by djen9999 on 2011-09-20
> **Blasphemist said:**
> Can you tell us what happens at this stage of the troubleshooting process from the thread above?

The kernal does not boot. To get to the GRUB menu I must press and hold the shift key.  When I go into edit and change to nosplash and Verbose, I get a string of comments but there doesn't seem to be an error message in the comments (not to my eye anyway).  I don't know of any way to copy these comments or I would post them.  None of them say ERROR:

I cannot boot into recovery/low graphics mode.  I continue to get the black screen.

---

### Post by sean lyon on 2011-09-20
Hi have had that too, Updating an Acer aspire laptop from 10.10 to 11.04 using update manager.

is it a blank screen or is it that the backlight for the screen has been bypassed? Shine a bright light at the screen can you see a gohst image of the sign in screen etc?

- it seems to be a bug and I was advised to report it as such the more its reported the more likley we will get a patch.

in the mean time booting from a USB stick still with 11.04 on it the same happened but and beware! stabbing about in the dark  it must have started the install and has tidied away the previous install of 11.04 but Id hit the power button to get out and so HD no longer boots.

so new set of problems for me to sort.
the earlier Kernel works fine. but Im at a loss to find "It" or where to install it

Sean

---

### Post by djen9999 on 2011-09-20
Using the live CD I was able to mount my boot disc and download the current driver for my card. I rebooted and everything loaded just fine. It seems it was a Unity thing. I'm not going to call it a bug but I guess it is.  I'll check Launchpad and see what I can find.  I'll share anything that I come up with.

---

