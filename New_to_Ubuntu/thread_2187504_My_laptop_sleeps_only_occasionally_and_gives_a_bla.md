---
title: "My laptop sleeps only occasionally and gives a blank screen when opened."
date: 2013-11-12
forum: New to Ubuntu
---

### Post by jakebuscher on 2013-11-12
I have a Lenovo T61p with Ubuntu 13.10 and most every time I close the laptop and go to reopen it, the screen only shows my background and there is nothing I can do but restart it in order to get to my programs. Also when I do leave the screen closed it sometimes decided not to sleep and instead bakes itself inside my laptop bag, another neat feature. 

Any help would be great! BTW I know little about Linux and would appreciate something I can simply put into the terminal.

---

### Post by germanix on 2013-11-12
What do you mean exactly that when you open the laptop lid "you only see your background". Are you refering to the desktop? Are you saying that the desktop shows but not the launcher ( launcher isthe dock on the left side of the screen with the program icons).
If this is the case then please go to "system settings" then to "displays" and check if there are any settings for the launcher there. I know I have but then i have two monitors connected.
As far as the screen not going to sleep, there are two things you can do.
1. check the settings under "system settings" and then "power" make sure that you have the setting "suspend when lid is closed" activated.
2. When you close your laptop the screen is automatically switched off by a mechanical switch build into the lid. maybe that switch is not fully or always functional or maybe the book moves around in your bag and the lid opens slightly causing the screen to wake up. make sure you carry the machine in a tight fitting sleeve if that is the case. This specific problem sounds more like a hardware problem to me.
I also run Ubuntu 13.10 on an Lenovo machine and have none of these problems. Sorry to hear about yours. Hope you get it sorted.

---

### Post by jakebuscher on 2013-11-12
The screen is always off when it it shut that has never been a problem. When I open it I do not see my launcher, screen-lets, or the top bar that shows stuff like time ect.. Most every time I open and close the lid this is the problem. Ocationally if i open and close it quickley it will display a login screen like it ought too. Yes, under power, suspend is selected for both battery and plug power.

---

### Post by jakebuscher on 2013-11-13
I have tried shouting at my laptop, but strangely, this too proved ineffective.

---

### Post by Toz on 2013-11-13
> **jakebuscher said:**
> I have tried shouting at my laptop, but strangely, this too proved ineffective.
lol. Perhaps its how you shouted?

Can we get some more information about the specifics of your computer? Open a terminal window, type in the following commands, and post back the results:

1. Your current kernel boot command line:
```
cat /proc/cmdline
```

2. Information about your video card(s) and drivers:
```
lspci -k  |grep -iA2 VGA
```

3. Your suspend log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the lik that is generated.

4. Any specific PM-related messages in your syslog:
```
cat /var/log/syslog | grep PM:
```

5. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

Lets see if we can get some clues from these commands as to what is happening to your computer.

(Also, making note of [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1232007") which might be related.)

---

### Post by jakebuscher on 2013-11-13
**1**```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-genericroot=UUID=cb4251f1-6d62-4af7-bf80-e2896a2fc9cd ro quiet splashvt.handoff=7
```


**2**```
01:00.0 VGA compatible controller: NVIDIA Corporation G84GLM [QuadroFX 570M] (rev a1)
	Subsystem: Lenovo ThinkPad T61p
	Kernel driver in use: nouveau
```


**3**```
The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selectedpackage>
```


**4**```
Nov 13 09:35:54 jake-ThinkPad-T61p kernel: [ 3746.192808]PM: Syncing filesystems ... done.
Nov 13 09:35:54 jake-ThinkPad-T61pkernel: [ 3746.386055] PM: Preparing system for mem sleep
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3747.350512] PM: Entering mem sleep
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3751.120276] PM: suspend of devices complete after 3755.771msecs
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3751.120666] PM: late suspend of devices complete after0.385 msecs
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3751.216076] PM: noirq suspend of devices complete after95.409 msecs
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3751.220968] PM: Saving platform NVS memory
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3751.324391] PM: Restoring platform NVS memory
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3751.596406] PM: noirq resume of devices complete after157.290 msecs
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3751.596562] PM: early resume of devices complete after0.115 msecs
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3754.532115] PM: resume of devices complete after 2935.548msecs
Nov 13 09:43:06 jake-ThinkPad-T61pkernel: [ 3754.532606] PM: Finishing wakeup.
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x0009d000-0x0009dfff]
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x0009e000-0x0009ffff]
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000a0000-0x000d1fff]
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000d2000-0x000d3fff]
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000d4000-0x000dffff]
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000e0000-0x000fffff]
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.089223] PM: Registering ACPI NVS region [mem0xbeecc000-0xbeefffff] (212992 bytes)
Nov 13 09:47:38 jake-ThinkPad-T61pkernel: [    0.627433] PM: Hibernation image not present or could notbe loaded.
Nov 13 12:14:13 jake-ThinkPad-T61pkernel: [ 8820.544550] PM: Syncing filesystems ... done.
Nov 13 12:14:13 jake-ThinkPad-T61pkernel: [ 8820.809061] PM: Preparing system for mem sleep
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8821.701211] PM: Entering mem sleep
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8825.460204] PM: suspend of devices complete after 3758.617msecs
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8825.460580] PM: late suspend of devices complete after0.371 msecs
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8825.556081] PM: noirq suspend of devices complete after95.497 msecs
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8825.561042] PM: Saving platform NVS memory
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8825.664392] PM: Restoring platform NVS memory
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8825.920499] PM: noirq resume of devices complete after156.753 msecs
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8825.920653] PM: early resume of devices complete after0.113 msecs
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8828.848194] PM: resume of devices complete after 2927.536msecs
Nov 13 17:58:33 jake-ThinkPad-T61pkernel: [ 8828.848738] PM: Finishing wakeup.
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x0009d000-0x0009dfff]
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x0009e000-0x0009ffff]
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000a0000-0x000d1fff]
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000d2000-0x000d3fff]
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000d4000-0x000dffff]
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000e0000-0x000fffff]
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.089223] PM: Registering ACPI NVS region [mem0xbeecc000-0xbeefffff] (212992 bytes)
Nov 13 17:59:43 jake-ThinkPad-T61pkernel: [    0.626348] PM: Hibernation image not present or could notbe loaded.
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x0009d000-0x0009dfff]
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x0009e000-0x0009ffff]
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000a0000-0x000d1fff]
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000d2000-0x000d3fff]
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000d4000-0x000dffff]
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    0.000000] PM: Registered nosave memory: [mem0x000e0000-0x000fffff]
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    0.136622] PM: Registering ACPI NVS region [mem0xbeecc000-0xbeefffff] (212992 bytes)
Nov 13 21:09:18 jake-ThinkPad-T61pkernel: [    1.420608] PM: Hibernation image not present or could notbe loaded.
```


**5**```

The program 'pastebinit' can be foundin the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selectedpackage>
```

---

### Post by jakebuscher on 2013-11-13
Thanks for helping me out Toz

---

### Post by Toz on 2013-11-13
Can you please install the **pastebinit** program found either in the software centre or via the terminal:
```
sudo apt-get install pastebinit
```
...and redo #3 and #5? Those log files will be useful to see.

---

### Post by jakebuscher on 2013-11-15
I tried to run the line you posted and only this resulted???

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by Toz on 2013-11-16
> **jakebuscher said:**
> I tried to run the line you posted and only this resulted???

E: dpkg was interrupted, **[COLOR="#FF0000"]you must manually run 'sudo dpkg --configure -a' to correct the problem[/COLOR]**.
Did you run:
```
sudo dpkg --configure -a
```
...and did it fix the problem?

---

