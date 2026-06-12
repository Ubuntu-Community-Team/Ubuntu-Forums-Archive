---
title: "Sometimes booting in 14.04 Need some help!"
date: 2015-04-16
forum: New to Ubuntu
---

### Post by Lightarms001 on 2015-04-16
Ok, fresh install from a DVD burnt with the 14.04 .iso from the main Ubuntu website. The computer is a toshiba satellite with a Radeon 6520 installed, 8 gigs ram, and a AMD Quad-Core A6. Installed no issue. Runs beautifully. Recognized all divers and installed correctly (no additional drivers icon or proprietary software used). Once I choose to restart or boot from a shutdown state the system will hang after briefly displaying a purple screen and then shortly a black screen and nothing will load. I power off the computer and begin to boot again I am successful in loading Ubuntu. It seems as if every other time it will load after it hangs.

I have:
Disabled quiet splash to no splash. Still will hang and will not display text until a successful boot so I can't see what the issue is.
Memory Test - Pass 100%
Used the Additional Drivers program to ensure my drivers are using non-proprietary software. 

Ubuntu will operate absolutely fine- when it will boot in.  I disabled the splash screen to see if any certain software or hardware is causing the hangup. Yet when the system hangs on boot it will only display a purple screen, then black, and then stop. If there is anything more I can do to help troubleshoot this please explain it to me like a five year old. This is my first experience with Ubuntu.

---

### Post by Vladlenin5000 on 2015-04-16
New AMD APUs really need proprietary drivers. Because it's a tightly integrated all-in-one solution the drivers are required not just for graphics but for everything else as well.
Your insistence in using the open source Radeon is comendable, but that's it.

---

### Post by QIII on 2015-04-16
I don't know that I would go so far as to say they are "required."

However, when I have suggested installing the proprietary driver to users of APU-equipped laptops/notebooks, in most cases they have reported greatly improved cooling and battery life.

Although the open source driver has improved immensely over the last couple of years with regard to power management, the proprietary driver is clearly superior in that regard.

But that is up to the user.  Nothing wrong with supporting open source if you can.

It is possible that heat is the issue.  When you shut down, the temperature of a CPU or APU can sometimes rise very sharply for a few moments after the fan stops.  Try shutting down and waiting three or 5 minutes before restarting.  Let us know how that works out.

---

### Post by Lightarms001 on 2015-04-17
I did end up downloading the latest driver from the AMD website and it has solved the issue causing my system to boot every other time. Now I have a new problem where this new driver is installed and I cannot change my resolution. "xrandr" has been tried and won't play ball as the minimum, maximum, and default settings are in a 4:3 aspect and the laptop itself is a 4:9 aspect device.

---

### Post by mastablasta on 2015-04-17
what about in Catalyst Control Center? can you configure it there?


[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by Lightarms001 on 2015-04-17
Well I was able to fix the issue. I followed Mastablasta's included guide. Was able to "sudo apt-get install dh-make dh-modaliases execstack libc6-i386 lib32gcc1" Then attempted a terminal amd console manager or something of the like. Was prompted to install a certain AMD package. Did so. Rebooted and was able to install AMD Catalyst&#8482; 14.12 Proprietary Ubuntu 14.04 x86_64 Video Driver for Graphics Accelerators even though it asked me if I did trust the issue. Rebooted and everything looks ok and runs fine. 

Now, can anyone explain to me what I just did? I am glad for the directions but I would like to begin to understand why "sudo apt-get install dh-make dh-modaliases execstack libc6-i386 lib32gcc1" seemed to be the beginning of the fix.

---

