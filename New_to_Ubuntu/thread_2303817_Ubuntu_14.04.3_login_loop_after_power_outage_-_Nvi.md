---
title: "Ubuntu 14.04.3 login loop after power outage - Nvidia driver related"
date: 2015-11-21
forum: New to Ubuntu
---

### Post by Peter_Marchetti on 2015-11-21
Hello. I installed Ubuntu onto my desktop earlier this year, and am currently dual-booting with Windows 10. Earlier today we had a short power outage while Ubuntu was running, and after turning it back on I've been stuck in a login loop whenever I try to log in through the gui, whether through my account or a guest account, and the resolution on the login screen was faulty. So far, based on research on these forums and elsewhere, I've done the following:  first, tried fsck, after booting from a live CD. This failed, apparently because the disk was encrypted. I followed various sets of instructions to try and solve this, and they invariably reached a step where either a tool that was supposed to be installed as a result of previous steps wasn't, or the result of a command was drastically different from what was described.  Next, tried booting in recovery mode and running fsck from there. This failed, due to what are apparently known bugs with the recovery mode causing it to hang partway through the fsck.   UPDATE: for some reason, I am now unable to boot from the live CD to a graphical interface. Ctrl+Alt+F1 goes to a terminal, as it's supposed to, but Ctrl+Alt+F7 takes me to a black screen or a screen with some graphical glitches.  Next, tried logging in through the terminal. Successfully logged in. Most problems of this sort seemed to be due to problems with the privileges of Xauthority, but fixing that didn't change anything.  Finally tried uninstalling all nvidia packages, and was able to log in through the GUI. However, I still have the following problems:   installing any nvidia package (so far tried nvidia-340, nvidia-setup and nvidia-current individually) seems to restore the login loop. rebooting from the console usually results in a black screen the next time it boots\ ubuntu does not correctly find the native resolution of my monitor, so everything is low-resolution and pixelly. And I can't run many programs/games that require the graphics card and associated drivers to run, of course.   Before the power outage, the computer was working fine. If I boot windows, everything works fine. Before the outage the drivers were a bit glitchy, but worked and corrected the problem with the resolution. I do not know if the reboot problem existed before the outage because I had never before rebooted from the terminal.   Other information, that may or may not be relevant: Graphics card is an nvidia GeForce GTX 750 Xorg.0.log contains many errors, including several copies of '[    12.120] (EE) [drm] KMS not enabled' and various things not existing. previously installed nvidia drivers include nvidia-340, nvidia-304 and various others with long names that I cannot remember. Ubuntu is installed, along with all relevant drivers etc, on a ~100 gig SSD, and Windows is installed on a separate 1 tb disk drive. Currently Ubuntu does nothing at all with the 1 TB volume, so I'm hoping if I free up some of Windows' claim on it I can move it over in the near term.   My current plan is to back up all my files and make a list of installed programs, and then back up everything, then do a fresh install, and re-install everything. Which is a huge pain, since I lose all my settings etc. Is there anything else I should try before doing that?

---

### Post by tgalati4 on 2015-11-22
Welcome to the forums.  Perhaps try *nomodeset *when booting.  KMS stands for kernel mode setting which is used to detect and change the resolution and display mode during boot so you can get fancy graphics during boot.  When this fails, you get a blank screen and often boot freezes.  Try setting *nomodeset*--there are several ways to do this and report back.

Welcome to the forums.

My mother's Father was a Marchetti from Piacenza.  Perhaps we are related.

---

### Post by Peter_Marchetti on 2015-11-22
Hello, thank you for the response! I'm not aware of anyone in my family from Piacenza, but my father's father was born in a small town near Modena.  Unfortunately, nomodeset did nothing for the boot problems. I just noticed I forgot to mention- the problems in question happen after selecting ubuntu (or whatever) from the grub menu, but before unlocking the disk.

---

### Post by tgalati4 on 2015-11-22
Perhaps your UEFI settings got messed up during the power outage.  Try turning off the internal graphics.  Then try the open *nouveau* driver and see if that at least gets you a full boot. Examine the Xorg errors carefully after each step.

```
grep EE /var/log/Xorg.0.log
```

---

### Post by Peter_Marchetti on 2015-11-22
> **tgalati4 said:**
> Perhaps your UEFI settings got messed up during the power outage.  Try turning off the internal graphics.  Then try the open *nouveau* driver and see if that at least gets you a full boot. Examine the Xorg errors carefully after each step.  ```
grep EE /var/log/Xorg.0.log
```  I have no idea what that is supposed to mean. I'm assuming that it's supposed to mean something like, 'disable the nvidia drivers, then try to boot using the nouveau driver and somehow access Xorg logs at various points in the booting process' but I don't think that last part is possible, though I could be mistaken.  In any case, I went ahead and reinstalled nvidia drivers to see what the logs said when they broke, and noticed the message 'module build for the currently running kernel was skipped since the kernel source for the currently running kernel does not seem to be installed'. This jogged my memory, and sure enough one of the big multiply-appearing errors in the Xorg.0.log was something along the lines of 'can't find nvidia module' (lost the exact text because my laptop crashed between me recording the errors and posting this. It's been a great day.). Reinstalling the linux headers seems to have fixed that, in that installing the drivers after doing that did not give the same error message, so I'm going to try rebooting now and seeing what happens. Posting this first in case it doesn't fix anything or breaks something further, as my backup computer may no longer be working for the next while.  Other notable errors are the 'KMS not enabled' appearing twice, several searches for nonexistent devices (I believe something like '/dev/dci/something' and '/dev/pd0?') and several instances of something like 'screen0 error- missing a config file' followed by the removal of the same two modules in a row.

EDIT: It seems to have worked. Graphics are being setup properly now, no login loop. Can't confirm that other problems are solved, and the laws of probability dictate that I never will. Only error remaining in Xorg is '(EE) open /dev/fb0: No such file or directory' which, while bizarre, doesn't seem to matter.

Also, I figured out how to format my posts correctly. Sorry for my earlier blocks of text.

---

### Post by tgalati4 on 2015-11-23
/dev/fb0 is a framebuffer device used for low-level graphics, like LCD sceens and game consoles.  You don't need to worry about it.  It's possible that the Linux headers got removed during an autoremove process, since they are only used for compiling code (and needed when installing proprietary drivers).  Check the SMART status of your disk drive to make sure that you have no disk errors.

I would get an UPS and reduce the Agony Units of fixing a system that is damaged by a power outage.

---

### Post by Peter_Marchetti on 2015-11-23
Believe me, a UPS is on my Christmas list, unless I land a paying job first.

I've  had no problems rebooting and am not finding any disk errors, so I'm  going to tentatively consider this one solved. Thanks for the advice,  everyone.

---

