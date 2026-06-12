---
title: "Ubuntu 11.10 not booting correctly.  Purple screen then black prompt screen. Help!"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by lawndart2 on 2012-01-19
I am new to Ubuntu and just installed it this morning on my Windows 7 hp computer as a partitioned os.  My Windows OS still works, but not Ubuntu.  This is the course of events...

Once installed Ubuntu worked just fine then I shut down my computer and when starting it into Ubuntu I got a purple screen that wouldn't go away, even after waiting 10 minutes.  I therefore read a thread on one of these forums which directed me to restart the computer and edit a kernel parameter in the grub menu.  I changed "quiet splash" to "nomodeset", rebooted and everything worked fine.  Then after restart I got the purple screen again.  I tried another fix which resulted me in changing "quiet splash" to "text" in nano editor. It then took me directly to my desktop.  I then restarted again to see if it worked and AGAIN I got the purple screen this was then immediately followed by the black screen which read a bunch of udevd errors followed immediately by terminated by signal 9(killed).
Now, when I try to run Ubuntu in recovery I just get the black screen with it saying,"Missing modules (cat /proc/modules; Is /dev) ALERT! /dev/disk/by-uuid/fbca7e3f-838c-4c5a-a170-1d1ea1854604 does not exist. Dropping to a shell!"

What is happening!? and how do I fix this?

Windows 7
AMD Turion 64X2
4GB RAM
NVIDIA GeForce 7150M/ nForce 630M

---

### Post by Rubi1200 on 2012-01-20
Hi and welcome to the forums :-)

First of all, you need to set nomodeset permanently if the drivers are not available otherwise you will always end up in this loop.

In other words, boot using the nomodeset option and then either check if additional drivers are available for your card or, if not, set nomodeset permanently using the following guide:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For the other problem, I suggest you post the results of the boot info script. There is a link at the bottom of my post with instructions.

---

### Post by lawndart2 on 2012-01-20
I went ahead and reinstalled Ubuntu (deleted first one via gparted and reinstalled) and now I have the purple screen of death cycle problem only.  I will go ahead and apply the first fix you mentioned and let you know of the results.  I have a question regarding the driver though, how do I check if my driver is good to go? currently it is running with: Broadcom STA wireless Driver and NVIDIA accelerated graphics driver (version current)[recommended].  Even with these drivers set it still goes to the purple screen on restart.

---

### Post by lawndart2 on 2012-01-20
After applied fix

So I did exactly what that link directed me to; i.e. went into gedit and put "quiet splash nomodeset" where I was supposed to, saved exited.  Then Alt+f2 and typed "sudo update-grub" and restarted my computer.  It brought me back to the purple screen again?!  So when I checked the grub menu (pressed "e" after restart) there was that line of code with "quiet splash" but no "nomodeset".  The only reason I am able to make it to this forum via Ubuntu is if I restart my computer and edit grub every time.  which is followed by 5 minutes of the black prompt screen filling my monitor with udevd[number] failures and signal 9(killed).

---

### Post by Rubi1200 on 2012-01-21
Hmm, that is odd.

Please post the contents of the file:
```
/etc/default/grub
```

---

### Post by lawndart2 on 2012-01-21
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

**Update**
I said before that grub wasn't showing "nomodeset" it was because I didn't update grub correctly.  Now that I have it is showing "quiet splash nomodeset", it doesn't matter because even after I fixed it I still either go to a purple screen (1/4 of the time) or 3/4 of time I get the black command prompt giving me all those "udevd" messages following by a command prompt again then I launch into Ubuntu.

---

