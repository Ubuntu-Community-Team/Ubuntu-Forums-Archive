---
title: "Booted u14.04 in recovery mode. Now What do I do?"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by nu2u904 on 2015-01-19
My hpZ400 w/s [u14.04] was running fine and I tried suspend; it did not recover; used AltsysRq reisub to shutdown. Attempted to boot to recovery mode ; got text menu options:  resume, clean, dpkg, failsafeX, fsck, grub, network, root, system-summary.  I tried grub with no sucess; also failsafeX. I don't know what to do next

I used suspend to minimize power use. Does disk spin-down itself alone save as much power even though my computer is on? 

Donald

---

### Post by grahammechanical on 2015-01-19
You do not tell what happened after you shut down and restated. It could give us a clue as to what you are asking help for.

Do you get a Grub boot menu? If so, then you do not need the Recovery Grub option because that updates the boot loader configuration files. But the boot menu is loading and selecting Ubuntu loads Linux but I am guessing at some point the loading of Ubuntu breaks down.

Why did you select the  failsafeX option? If we have a problem with proprietary video drivers we can use Recovery Resume to get to a desktop using an open source video driver. It is also the way to get out of Recovery mode and back to a desktop.

The purpose of the other options seem clearly explained by the accompanying comments. But not knowing what happened on restart it is difficult to suggest what to do next.

_Suspend to RAM (Linux)_
> [COLOR=#252525][FONT=sans-serif]
Machine state is held in [/FONT][/COLOR][RAM]("http://en.wikipedia.org/wiki/Random-access_memory")[COLOR=#252525][FONT=sans-serif] and, when placed in sleep mode, the computer cuts power to unneeded subsystems and places the RAM into a minimum power state, just sufficient to retain its data. Because of the large power saving, most laptops automatically enter this mode when the computer is running on batteries and the lid is closed. [/FONT][/COLOR]


Now think what happened when you powered off the machine. Also, hard disk spin down cannot achieve the same power savings as suspend because many other hardware components are still using power.

_Hibernation, also called Suspend to disc in Linux_

> [COLOR=#252525][FONT=sans-serif]saves all computer operational data on the hard disk before turning the computer off completely. On switching the computer back on, the computer is restored to its state prior to hibernation, with all programs and files open, and unsaved data intact. In standby mode, computer's state is saved in RAM; in hibernation mode, computer's state is saved on the hard disk.[/FONT][/COLOR]

[http://en.wikipedia.org/wiki/Sleep_mode](http://en.wikipedia.org/wiki/Sleep_mode)

Regards.

---

### Post by nu2u904 on 2015-01-20
Thank you gram [I am writing thon a laptop  running u14.04 on which suspend works.]

The computer in question is a desktop work station hpZ400. There is no hibernation option.

I just now attempted a boot. I got only a blank screen after several lines of Attempting to boot ... which I couldn't read.
the boot 
After the shutdown sequence, I got the hp splash screen, A page of  error messages saying could not open evinc... something that I could not read; some more code and then the the grub menu. I selected advanced option and then the recovery option at which point recovery menu appeared.

Is there a way to captusre these screens?  one code line read ... nvidia taints ....

---

### Post by whitesmith on 2015-01-20
> **nu2u904 said:**
> My hpZ400 w/s [u14.04] was running fine and I tried suspend; it did not recover; used AltsysRq reisub to shutdown. Attempted to boot to recovery mode ; got text menu options:  resume, clean, dpkg, failsafeX, fsck, grub, network, root, system-summary.  I tried grub with no sucess; also failsafeX. I don't know what to do next

I used suspend to minimize power use. Does disk spin-down itself alone save as much power even though my computer is on? 

Donald

If you can get to recovery mode, drop to a shell and type```
nano /etc/default/bootlogd
```and then look for```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No
```Change that to Yes. All your boot messages will then be in /var/log/boot.log, so you should be able to figure out errors from that. This answer is modified and corrected from the thread [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925).

---

### Post by nu2u904 on 2015-01-24
> **whitesmith said:**
> If you can get to recovery mode, drop to a shell and type```
nano /etc/default/bootlogd
```and then look for```
# Run bootlogd at startup ?
BOOTLOGD_ENABLE=No
```Change that to Yes. All your boot messages will then be in /var/log/boot.log, so you should be able to figure out errors from that. This answer is modified and corrected from the thread [http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925).

I attemted that and only got blank in file space on nano. I repeated usung gedit, got the error message 'XDG_RUNTIME_DIR '  not set in the environment.

(gedit: 782): GtK-WARNING **: can not open display:

ls /etc/default [no file 'bootlogd' listed]

Donald

---

