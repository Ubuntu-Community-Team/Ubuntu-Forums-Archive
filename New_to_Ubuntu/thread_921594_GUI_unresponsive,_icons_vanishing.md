---
title: "GUI unresponsive, icons vanishing"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by dorite on 2008-09-16
Folks,

I need help.  My Ubuntu Hardy 8.04 desktop is unresponsive (“almost dead” would describe it).  The mouse moves the cursor around, but clicking does nothing much.  (Note that this is similar to, but not the same as the GUI freezing problem that StressedOne mentions in [http://ubuntuforums.org/showthread.php?t=861393](http://ubuntuforums.org/showthread.php?t=861393) )

It’s probably a coincidence, but the problem began about a week after I installed avant window manager and set it to run on startup.  Booting worked normally, the little icons moved to the bar at the base of the screen, but I could only do one thing (i. e. I could start any application, but do nothing with it after it displayed the first screen.)  I was able to stop avant from starting up, but the problem remained.  Then I lost all the icons and functions from the right side of the top bar (user, network, sound, date) except logout – which is unresponsive.

I tried the Options:Sessions variations from the Ubuntu login window: GNOME and Failsafe GNOME gave me the same functionality:  mouse moves cursor, clicking either does nothing or brings up a window that then does nothing when clicked, keyboard gets no response.

I went to a terminal, became root, and added a new user.  Same problem with that user.

Any advice?  I have some familiarity with Unix/Linux, but none with Gnome, so I have no idea where to look for configuration files or what they should look when I find them.

Thanks

PS:  I wish I could send you the outputs of cat /proc/cmdline and cat /proc/interrupts, but I can do nothing when I’m frozen:  I have to use the power switch to turn off the computer.  As an old Unix guy, I hate that:  I still clutch at the thought of file system corruption.

---

### Post by phidia on 2008-09-16
You say you can't do anything when your frozen-have you trying opening a tty (ALt+Ctrl+F1) and issuing "dmesg" or looking at messages; syslog in /var/log?

If you can't open a tty you can or should be able to boot in recovery mode and check those files-something should be leaving a log file behind to tell us what's going on.

Edit: If it were happening on my system I would use apt to remove awn and see if that made a difference. You can always reinstall it later.

---

### Post by scorchgeek on 2008-09-16
This seems silly, but are you sure a hardware problem hasn't started?

---

### Post by dorite on 2008-09-17
Thanks for your thoughts on this.  I don't think it's a hardware trouble:  it's a dual-boot computer, and I'm using the WinXP half as I type.  I have purged all the avant and awn packages (there are a lot of them, aren't there?) to no avail -- except that I got the icons on the right side of the top bar back.  Still no response to mouse clicks.  I **was** able to CTRL-ALT-F1 my way to a terminal, so I could get the dmesg and syslog files.  I don't see anything especially wrong with them, but then I don't know what I should be looking for.  Both are attached -- maybe somebody can find something and suggest a next step.

I'm hoping not to have to reinstall ubuntu -- I can find and save my important data files, but configuring my printer was not easy.

Thanks for your attention.

---

### Post by dorite on 2008-09-19
OK.  I tried purging all the gnome packages with aptitude and reinstalling them.  What a mess!  I finally rescued as much data as I could and reinstalled Ubuntu.  I'm back to a gnome desktop I can use, so I guess I'll mark this one "solved".  Thanks for your attention.
:(

---

