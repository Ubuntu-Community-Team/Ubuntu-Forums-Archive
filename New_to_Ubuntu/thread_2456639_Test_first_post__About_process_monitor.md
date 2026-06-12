---
title: "Test first post:  About process monitor"
date: 2021-01-16
forum: New to Ubuntu
---

### Post by Swan_DB on 2021-01-16
If I go into my process monitor, and start killing processes, are there certain process that I *absolutely should not* kill?  I ask this because I have no CD drive to re-boot Windows 7, and my USB Ubuntu is an old batman usb stick that I don't think has much life left.

So what processes can I kill, and what should I not kill?  Or can I kill all processes, and just restart my pc, and all is good?

Sorry if this makes little sense, I have brain problems.

---

### Post by ActionParsnip on 2021-01-16
Why are you killing processes? Killing processes in Ubuntu is absolutely nothing to do with Windows 7 in any way. Processes are spawned when needed so if you cause issues then just reboot.
What are you trying to achieve by killing processes? What is your goal?

---

### Post by TheFu on 2021-01-16
> **nonpoliticalusername said:**
> If I go into my process monitor, and start killing processes, are there certain process that I *absolutely should not* kill?  I ask this because I have no CD drive to re-boot Windows 7, and my USB Ubuntu is an old batman usb stick that I don't think has much life left.

So what processes can I kill, and what should I not kill?  Or can I kill all processes, and just restart my pc, and all is good?

Sorry if this makes little sense, I have brain problems.

Kill away. It is your system.  Don't be surprised when you do that if bad things happen.  Also, there are hundreds of different "signals" that the kill command can send to a process which conveys how to shutdown.  These are in the "signals.h" file, somewhere on your system.  I think kill without any signal specified sends a -15 signal.  There are singles that say to restart, reread config files, and that the OS tells the program to die-die-die, now!  The manpages for "kill" and "signal" (section 7) have more details. You'll want to learn more about manpages and getting specific sections information displayed to see some.

SIGTERM, SIGKILL, HUP, SIGCORE are the most common, but there are lots and lots of others.

Probably should avoid using **sudo kill -1** if your file systems aren't all journaled file systems.

---

### Post by Swan_DB on 2021-01-16
My back up plan, in case I destroyed my Ubuntu install, was to re-install my old OS (Windows 7), but I can't since I have no CD drive now (it broke).  I do have Ubuntu saved on a USB stick, but it's an old USB drive, and I'm afraid it might die, leaving me with no options for installing an OS.

The reason for killing processes is just for learning purposes, another commenter here said to read up on the man pages, which I will begin to do.

You're response leads me to believe that if I do kill a process that crashes my system/operating system (not sure if that's possible), that I can just reboot either from the saved Ubuntu OS on my ssd drive, or reload from my USB drive. does that sound correct?

---

### Post by TheFu on 2021-01-16
USB "thumb drives" are pretty cheap these days.  Saw a 3-pack of 32GB for $4.99 a few days ago. "PNY 32GB Attaché 4 USB 2.0 Flash Drive 3-Pack"  Not speed demons, but more than acceptable for emergency boot needs or running an OS for online banking.

How you kill processes matters.  All support the default SIGTERM signal.  That's what a WindowManager sents to a process when we tell the window to close from outside the application menu. Perfectly safe and programs will automatically close files cleanly.  Killing daemons can have undesirable side-effects, but it is dependent on the daemon.  Some won't respawn. Others will, but only for a certain number of times.  The manpage for each program should be clear about issues.

As an end-user, you can't really harm the OS.
If you are killing and using sudo with that, you can.  sudo isn't a toy. There are often unintended repercussions.  When you break your system, it won't be convenient and you'll have to learn to fix it. As long as you are prepared for that, great!  If you are going to experiment with sudo, it would be smart to have automatic, daily, versioned, backups that you can restore.  

That is the #1 security tool that I know - versioned, automatic, backups.  Just be certain to have the backup storage disconnected when doing these tests.  It would be bad if you accidentally wiped the backups out, right?

Or you can follow a well-organized guide to learn the basics for a month or two, before heading off into the forests.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is one.  LPI has a number of free resources.  Many of the posters here have links in their signatures to free resources.  Or find a local Linux group, hand out with them, and see how they learned.

When I was teaching Linux classes, I was asked by people who couldn't attend how to learn it. 
My answer: [https://blog.jdpfu.com/2017/03/31/learning-linux-condensed](https://blog.jdpfu.com/2017/03/31/learning-linux-condensed)

BTW, I've never used process monitor.  That's a GUI program right?  GUIs don't exist on Linux servers.

---

### Post by grahammechanical on 2021-01-16
I would not experiment with my install of Ubuntu if I had not learnt how to re-install it. In fact it was by messing up that I was forced to learn how to re-install. I, now, have more than one installation of Ubuntu and some other Linux distributions. If I mess up one install can I can easily switch to another OS. 

Why do you need a CD drive to reboot Windows 7? Perhaps you mean re-install Windows 7? Microsoft stopped supporting Windows 7 on 14th January 2020. The installation disc that you have will need security updates once you have re-installed and they may not be available.

[https://support.microsoft.com/en-us/windows/windows-7-support-ended-on-january-14-2020-b75d4580-2cc7-895a-2c9c-1466d9a53962](https://support.microsoft.com/en-us/windows/windows-7-support-ended-on-january-14-2020-b75d4580-2cc7-895a-2c9c-1466d9a53962)

Would it not be better to get an in life ISO image of Ubuntu on that USB memory stick? Or on a new USB stick and then you can experiment and learn in the knowledge that you can erase the drive and start over again.

Through experience some of us have found that a lot of time and energy can be spent trying to fix what is broken. A re-install is quick and clean. With backups of our data it is also painless. 

Regards

---

### Post by Swan_DB on 2021-01-16
I appreciate this reply, it gives me peace of mind, thank you.  As for 32GB tumb drives for $4.99, I'm about $4.99 short, lol.  Looking for work now though, but life has a way of kicking you when you're down, and then just keep kicking.  Thanks again, worst case is I have to walk to a library, if those still exist, lol.

---

