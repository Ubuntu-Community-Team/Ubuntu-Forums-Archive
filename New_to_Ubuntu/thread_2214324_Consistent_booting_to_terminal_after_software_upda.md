---
title: "Consistent booting to terminal after software updater crash"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by Chessgeek2900 on 2014-03-31
Greetings.

Be warned, I am still very new to Linux (which is probably why this happened...)

This morning, after leaving my laptop up all night, I decided to try and see if I could find an updated driver for my ATI Mobility Radeon graphics card (it's either a 9100 or a 9200, I believe.)  Right in the middle of a download, Ubuntu Software Center stopped responding, then closed itself.  As the computer continued being sluggish, and that can sometimes be fixed in Windows with a simple reboot, I decided to shut it down and do a cold boot.  Unfortunately, however, I seem to have broken something, as I cannot utilize the gui at all; I can only log in using the command line.  After seeing another post with intermittent booting to terminal issues, I decided to watch for the process that supports the gui--lmdlight, I think it is.  Anyway, the best I could see was a quick flash on-screen, and it looked like the service started then stopped again immediately.  Typing "grep lmdlight" into the command line came back with no output, and my attempt to run the process as "sudo lmdlight -d" (for debug information) resulted in a screen full of text and no responsiveness from the system aside from using ctrl+alt+F2 to switch to tty2

I have checked tty7 on several reboots to see if anything was there.  Sometimes, it is simply a black screen.  Others, it is full of text.  One line in particular caught my eye: 

"*Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated   [fail]"

Further reading revealed another error, probably resulting from my not having installed all of the ACPI utils that I had been considering.

"Starting Toshiba hotkeys utils: FnFX Daemon v0.3 (c) 2003, 2004 Timo Hoenig <thoenig@nouse.net>

fatal error: Could not open /proc/acpi/toshiba/keys.
Please make sure that your kernel has enabled the Toshiba option in the ACPI section.
For more information read the documentation and/or http://fnfx.sf.net/index.php?section=doc#kernel."


I doubt this is it, however, as that survived at least one reboot without causing system problems (that I know of.)

I tried booting using the bootable USB drive I created using Unetbootin for Windows, and ran Boot Repair from there.  [http://paste.ubuntu.com/7185801/](http://paste.ubuntu.com/7185801/) is the URL it gave me.

Computer and Operating System specs (as best I can remember them) follow.

Intel Pentium 4 laptop running Xubuntu 13.10 (Saucy Salamander)
Dual-Core Processor, speed 2.80 Ghz.
approximately 800 MB of RAM
ATI Mobility Radeon 9000 graphics card

Any advice on this would be appreciated.  Much of the above information is the result of my reading troubleshooting guides or other threads on boot issues on my old desktop while trying to figure out what was going on with my laptop.  (Old as in 15+ years, custom-built for Windows 98 and now running XP--but, funnily enough, it is my only usable computer right now.)  I sometimes have difficulty understanding written instructions, so please do not assume that I will notice an implied step, or that I will realize in time what hitting the delete key with a file selected will do.

Thank you,

Chessgeek2900

EDIT:  I realized this afternoon that it would be quicker to reinstall Xubuntu than to troubleshoot this, especially since I will be losing virtually no data.  As a result, I now have my computer up and running again, and am marking this thread as solved.

---

