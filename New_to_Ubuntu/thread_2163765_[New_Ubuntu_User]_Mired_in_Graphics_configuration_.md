---
title: "[New Ubuntu User] Mired in Graphics configuration hell-lost desktop.  Help!"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by llathos on 2013-07-19
Quick background:
Some Linux experience with CentOS, but new to Ubuntu.  Just did a fresh install of Ubuntu 13.04 to it's own internal hard drive.

The progression:

1)  Completed install, set up development tools and code (valuable...don't want to wipe install!).  I set display up (3 monitors).
2)  Used Ubuntu Software Center to attempt an NVIDIA driver installation.  Saw the "face" item used to get nvidia-current.  Ran installer, but when complete nothing happened (no display cycle, no reboot, no nvidia tools appeared).
3)  Downloaded the 64-bit Linux drivers directly from NVIDIA's site.  Rebooted, stopped lightdm, and ran the .run file.
4)  Installer warned of 'Nouveau', shut it down, and rebooted so it would be disabled.
5)  Installer warned of "failed pre-install scripts" but continued anyway and completed "successfully"
6)  Rebooted and got a blank screen with a flashing cursor on it.
7)  Booted into Recovery mode, did a [U]sudo apt-get purge nvidia-*
[/U]8)  Rebooted and got desktop back, hooray!
9)  I get notified this morning of system updates including kernel updates(140MB of them?!).  I install them and reboot.
10)  I get only my single screen, with 2 desktop icons, and all of Unity interface is missing.  Desktop is useless.
11)  I go to virtual console Ctl-Alt-F5, stop lightdm, and decide screw it...might as well try nvidia again: [U]sudo apt-get install nvidia-current
[/U]12)  I reboot and now I get all 3 screens!  Hooray!  Oh wait....all of the Unity desktop is still missing.
13)  From some online articles, I try the following mixture:  _dconf reset -f /org/compiz_ which results in errors b/c org/compiz doesn't exist, or something.  I also try _unity --reset-icons &disown_ and _setsid unity_.  These result in the same output which is a long page full of compiz related errors mixed with GLX errors.  
14)  I retreat from NVIDIA doing another purge (See step 7) and _sudo apt-get install ubuntu-desktop_ , _echo 'nouveau' | sudo tee -a /etc/modules_ , and check for an xorg.conf to remove (there isn't one)
15)  Now expecting to be running Nouveau, I reboot.

Single center monitor, no Unity interface.


I'm stumped.  All I want to do is go back to the default driver with a working desktop.  I would PREFER to be using the nvidia driver, but apparently that's a bridge too far...

Help!

Llathos

---

### Post by llathos on 2013-07-19
Fixed.

Problem was some corrupted folders in home directory.  I isolated by seeing that the Guest account Unity was loading properly with all 3 monitors...so it had to be account specific.  Backed up all hidden folders and rebooted to rebuild from defaults, then recovered app-specific folders as necessary.

Still would love to know how that happened....

---

