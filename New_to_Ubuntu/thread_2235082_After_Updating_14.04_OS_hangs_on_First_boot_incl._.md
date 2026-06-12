---
title: "After Updating 14.04 OS hangs on First boot incl. keyboard, 2nd boot onwards works"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by machinesmith2 on 2014-07-18
Hi, 

Here's my problem so far: 

[LIST]
[*]Got Ubuntu 14.04 ISO on release, and everything ran perfect, I had disabled updates by mistake. 
[*]Switched updates on, and now everytime I Power cycle the PC (i.e. Shutdown PC, turn back on after sometime) The OS ALWAYS hangs right before the Login screen with the drum sound pops up - keyboard and mouse is also frozen. 
[*]However,  if I press the RESET button while the PC is frozen, the 2nd boot will load absolutely fine. I can restart the PC a hundred times and it will load the OS without a problem. But if I shut down and power on again, it will hang again. 
[*]I have been booting my OS like this for a month now - turn on PC, hang, hit reset, reboot all over again, now Ubuntu loads. 
[*]I hope someone can help, here are my PC specs: 
[/LIST]
```
[COLOR=#808080][SIZE=2][I]Core2Duo E8500 3.0Ghz
4GB RAM DDR2
Gigabyte GA-G31M-ES2L Motherboard
1 x 128GB SSD (ubuntu boots from this)
1 x 1TB HDD
HIS Radeon 6670 GPU
Ubuntu 14.04 (dual boot with Win7, yes Win7 works fine on every boot including the first)[/I][/SIZE][/COLOR]
```

P.S. I've reinstalled Trusty 3 times. Each time it messes up on the update, the rest of the thread will be documenting the things I've tried until I eventually fix it, or just give up and move to another distro. Thanks for reading.

---

### Post by yancek on 2014-07-18
I had a similar problem in that on booting 14.04 from a cold boot, the computer having been shut down previously, I would get to the login screen and could here the little login drum roll one gets at login.  Could not see anything.  Tried entering password, didn't work.  Not able to shut down unless I pressed the power button.  The difference in my case was that the bottom half of the screen was black.  The top half of the screen had what looked like horizontal lines going from the left at an angle to the right top.  After doing a hard reboot, I got the login screen and was able to login.  This happened 6-8 times or more, can't remember exactly as 14.04 isn't my primary system so I don't boot it every day.

I installed the proprietary drivers for my nvidia card yesterday and it booted today, I think.  I'll have to wait a few more days to test.  I don't know if this is the same problem but you could try going to System Settings, Software & Updates and Additional Drivers and see if you have som other driver recommended.

---

### Post by machinesmith2 on 2014-07-23
@yancek thanks for the reply, I'd tried the proprietary drivers for my AMD card before but the problem remained - however a new batch of updates took place recently so I'm going to try it again on your suggestion, will report back if it works. Also I found that each time I power cycle my PC this issue happens (as in, I shutdown my PC, wait a few seconds, turn it back on, my screen hangs). Hitting the reset button and re-booting still works though.

Edit: Just tried with proprietary drivers, pretty much the same, although with a slight difference: I could see the mouse pointer this time before the system froze. Just to clarify this is just before the login screen with the drum sound. Once I rebooted via the reset button I was able to get my login screen and was able to login.

---

### Post by machinesmith2 on 2014-07-25
Tried the following, which have NOT worked:

[LIST=1]
[*]Proprietary AMD Radeon drivers from both the official repository and the latest release on AMD's website. 
[*]Trying the following lines within the defualt grub config
[LIST=1]
[*]GRUB_CMDLINE_LINUX="reboot=bios" 
[*]GRUB_CMDLINE_LINUX="reboot=acpi" 
[*]GRUB_CMDLINE_LINUX="reboot=pci" 
[/LIST]
  
[*]Updated to a newer mainline kernel from kernel.ubuntu.com (3.15.4) 
[/LIST]

My next attempt is to downgrade to an older kernel and see how it goes from there. I hope it works.

---

### Post by machinesmith2 on 2014-07-26
Nope, I've tried Kernels from the latest stable (3.15.6) to ones from March (3.13.8) both give the exact same result, PC still hangs on Power Cycle, will try a few other things I've noticed on other forums about boot related problems. Don't have much hope they'll work so will probably desert Ubuntu for something that works.

---

### Post by machinesmith2 on 2014-07-27
And So After Reading through ArchWiki and feeling like an AMD Radeon KING - I conclude that this was never meant t....HAH! NOPE! After going through some harrowing steps to figure out what was wrong I came across one culprit called the AMD Radeon Kernel / MiniPort drivers. No, I have no clue what it is either. However out of curiosity I found the Windows equivalent in the file called atikmpag.sys. I decided to uninstall the driver in windows to update it to the latest one (I barely use windows and my card is pretty ancient so I never saw any reason to update the drivers) - lo and behold, I now had the exact same problem on windows 7! 

 Surely Windows users would have the answers right?? Turns out quite a few people suffer from BSODs on their WinBox thanks to this particular file (and its brother, atikmdag.sys) Most Answers revolved around:

[LIST=1]
[*]Uninstalling your drivers via a software called DDU.
[*]Reinstalling JUST the driver - no Catalyst.
[*]'Resetting' the BIOS.
[/LIST]

And there you have it, Step 3 was the answer, While I was a little confused about WHAT to reset in the BIOS, I didn't ponder too long and went with "Load Failsafe Options" found in my Award BIOS options. That did the trick. For both Windows AND Ubuntu I no longer have the system freezes on Power Cycling AND my Radeon is actually performing FASTER (fps wise!) Hope this helps someone (and more-so, I hope no one ever faces this issue!!) Take care all! ):P

---

