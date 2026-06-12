---
title: "No display with kernel 3.2.0-39 or 3.2.0-40"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by mfe on 2013-04-23
I've been running Ubuntu 12.04 for quite a while.  Each time there are upgrades I load them.  Perhaps that's a mistake?  When the new kernel 3.2.0-39 arrived, I loaded it without thinking any more about it.  Next time I switched on my PC, there was nothing on the screen after the BIOS boot up.  I connected an old keyboard with a PS/2 connector - knowing that a USB keyboard will not work in this situation - and re-started the PC.  This time the GRUB menu came up and I was able to select an earlier kernel to use, 3.2.0-38 and that worked ok.  A few days ago, the next kernel, 3.2.0-40 arrived for download and installation which I did, thinking that it would fix the problems from 3.2.0-39.  Sadly not.  It does exactly the same thing - that is I boot up through BIOS then get a blank screen.  So it was back to re-starting, getting the GRUB menu and selecting 3.2.0-38 again.  I don't get GRUB at initial switch-on, so I can't select the working kernel first time, I have to press the restart button on the PC to get GRUB.  Now I have resorted to a bodge, taking all the files in my /boot/ directory which have 3.2.0-39 or 3.2.0-40 in the filename and renaming them so that they aren't recognised, but it doesn mean that I start up every time with kernel 3.2.0-38. 
What should I have done?
What should I do to get the latest kernel to work?
Any thoughts on this?

---

### Post by zero2xiii on 2013-04-23
Hay,

 I STRONGLY recommend not renaming random kernel files! So rename them back.

Then, I suggest you get to a grub screen (how ever you have to get there) and choose the latest kernel's "recovery mode".

After this loads up there should be a dialogue box that comes up, select the "fix graphics issues" option and then follow the prompts and restart your computer, this should fix the graphics problem.

Cheers and good luck :)

---

### Post by mfe on 2013-04-23
Hello zero2xiii,
Thanks for the advice.  I renamed the files back to the way they were, then attempted to get into grub the way I've done previously, pressing the reset button.  I'm now at a new prompt that I've never seen before, grub rescue>. Any suggestions how I get out of this one? None of the commands I enter seem to be recognised.

---

### Post by mfe on 2013-04-24
Having switched off my PC last night and re-started it this evening, I got a purple screen and then the grub menu.  I ran the recovery mode and, after a lot of screens of text, ended up with:
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4.1) built -in shell (ash)
Enter 'help' for a list of built-in commands.
I still don't know what to do though.
Any suggestions?

---

