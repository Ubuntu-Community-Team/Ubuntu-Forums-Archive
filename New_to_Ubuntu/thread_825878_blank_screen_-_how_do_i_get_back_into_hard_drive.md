---
title: "blank screen - how do i get back into hard drive"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by johnlvs2run on 2008-06-11
I enabled the driver at "system > administration > hardware drivers", rebooted and there were colors spewed all over the screen.  I didn't know how to get a normal screen back so had to do a reinstall of Ubuntu.  Now I've tried to enable the driver a different way, rebooted, this time got a blank screen, again not able to get a normal screen, so I'm running from the liveCD.

Is there a way to get a normal screen back, or do I have to do another reinstall of Ubuntu?

---

### Post by phidia on 2008-06-11
When this happens or whenever you lose your desktop you can press the Alt+Ctrl+F1 keys simultaneously (function keys from F1-F7) should open up the commandline interface for you.
You need to naviagate, using commandline to your /etc/X11/xorg.conf file.
You can open that file for editing by typing > sudo nano /etc/X11/xorg.conf If you were already in the X11 directory then you could just type sudo nano xorg.conf. You need to revert to the vesa driver and also find out what gpu you have. lspic -v
Hope that helps.

---

### Post by philinux on 2008-06-11
Boot the pc and press escape at grub stage 1.5

Choose the second line - recovery mode.

Then choose xfix from the menu.

---

### Post by johnlvs2run on 2008-06-11
Thanks much for responses.  I've written these things and will try them next.  I was able to get in once from selecting the 2nd boot sequence out of the 4 + recovery modes on the boot screen but now none of them work.  I tried to edit them but kept getting them back. 

I don't know if it's related but the Hanns-G hw192dj monitor has been giving me the same message for the last two years of "No Signal Input, check video cable", when first booting up.  The video cable is connected.  I wonder if it's an issue with the Hanns-G monitor.

Will I ever be able to use the Nvidia driver?

I'll look around some more and then try your suggestions.

---

### Post by avtolle on 2008-06-11
Is there a problem with your video cable itself, e.g., a "short" caused by a broken wire in it? I'd take a look at replacing it given two years of messages about it.

---

### Post by johnlvs2run on 2008-06-11
I used the VGA cable for 2 years, and plugged in the DVI cable yesterday.

The message is the same.  

The computer revs up for a second, then slows as that message appears on the screen, it disappears, then the computer revs back up and starts.

---

### Post by johnlvs2run on 2008-06-11
The black screen came up again.
When this happens, cont-alt-f1 doesn't work and cont-alt-del doesn't work either.

I went to the 1st recovery mode choice on the boot screen (not sure what grub stage 1.5 is), pressed return, e(edit), c(command line) and got "grub >".  I typed the suggested commands here and got "error 27: unrecognized command".  I must have the wrong screen.  I'm still on the CD, not able to get a clear screen in the hard drive.  The screen is fine from CD, except 800x600 resolution.

Will I be able to get into the hard drive, or should I start over with install?

By the way, the blank screen appears after Ubuntu loads up.

---

### Post by johnlvs2run on 2008-06-11
Am I asking this the wrong way, or in the wrong forum; or am I asking right but people just don't answer very often.

Update:  The 3rd installation of Ubuntu is completed, including the updates.  This took just under 1 hour.  My screen is still at 800x600 instead of 1440x900.  I'm looking to improve that, change the desktop to solid brown (done, by right clicking the desktop), and am not going to enable the Nvidia driver.

---

