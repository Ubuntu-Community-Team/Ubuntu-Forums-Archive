---
title: "hard drive clicking and random crashes"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by 0004tom on 2008-09-18
I've been using ubuntu 8.04.1 now for a month or so. And for every 10-20seconds, sometimes less my hard drive clicks. I've search the internet, and found a thead on the forums, that says my hard drive is "parking heads" with a code that stops this from happening, i've put the code in and i then experience a random lock up with in a few hours.

This brings me to my next problem, I'm still experiencing random lock up's. this can be from 2minutes from logging in to 15hours of no trouble at all. After each lock up I've gone though system logs, and can't find a thing, around the time I had my latest lock up.

I using a Hp g6030ea, with a Sata 80gb hdd, Broadcom 4311rev02 wireless card, that i've not set up, I do however use, a linksey WUSB54G v4 setup using ndiswrapper. also have Nivida 6100 graphics card, using restriced drivers, plus i'm using the 2.6.24-21-generic kernel. Can anyone help me solve my two little problems ?

Thanks in advance

---

### Post by hellion0 on 2008-09-18
Notebook?

Is it overheating? Sometimes that can cause the lockups you describe (and that's a problem I have on my own HP as well).

---

### Post by blazemore on 2008-09-18
When the computer freezes up, do the numlock, capslock keys etc, light up when you press them? If not, this is kernel panic. You have the same network card as me. I have found, on 8.04 and below, that the ndiswrapper driver for this causes kernel panics. Your hard-drive here is not the problem (Or it might be a different problem). In a month or so, 8.10 will come out. This has support for your wireless card out the box (I've found), and contains a more recent kernel, which fixes a known problem with laptop hard-drives (could apply to your system, I don't know).

My advice would be to back up your important files IMMEDIATELY (In case of hard-drive faliure), and then wait for 8.10, and do a clean reinstall with this version (rather than a dist-upgrade). This will make sure the system is using the kernel driver rather than the buggy ndiswrapper.

Good luck!

---

### Post by MegaJim on 2008-09-18
You can periodically check your hard drive's temperature using this command:

```
sudo hddtemp /dev/sda/
```

where /dev/sda is the device in question.

In the majority of cases high hard drive temp by itself isn't an issue, but if it is causing other components to go above their thermal limits this could indeed explain the lockups.

I would suggest using something like lm-sensors to monitor your temps for a start;  When you lockup, can you restart the X Server with ctrl+alt+backspace?  or swap to a terminal with ctrl+alt+f1?  Also, if neither of these work to recover your computer, can you restart the computer using this method:

[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891).

---

### Post by 0004tom on 2008-09-18
Thanks for the speedy replys

I'm not sure if it's overheating, but the fan isn't used as much as it is in Windows.

No the lights do not light up, I can turn the touchpad of and on a few times, before that stops tho. I don't use the onboard wireless card, I use a USB dongle, as said in the first post. Not even setup the broadcom card. 8.10, i tried Alpha5 and still got a lock up with in minutes booting the new install.

No, I can restart Xserver, nor anything, the system just stops working, if sounds playing at the time, it's repeated, the screen stays at it is, the cursor doesn't move, it becomes un-interactive(is that a word ?) the code you surpuylied returns command not found.

---

### Post by blazemore on 2008-09-18
So when you tried the alpha, did you still use ndiswrapper? I think it's ndiswrapper that's the problem, or try cleaning your laptop with compressed air.

---

### Post by MegaJim on 2008-09-18
You need to install the tool first

```
sudo apt-get install hddtemp
```

---

### Post by 0004tom on 2008-09-18
> **blazemore said:**
> So when you tried the alpha, did you still use ndiswrapper? I think it's ndiswrapper that's the problem, or try cleaning your laptop with compressed air.

Clean my computer with compressed air ? 
No, i received the lock up with the alpha, before installing ndiswrapper

---

### Post by karlr42 on 2008-09-18
I had the same problem, I found a solution somewhere. The clicking is caused by the power management system "turning off" the HD by parking the heads if it's idle for 5 seconds. The command was ```
sudo hdparm -B192 /dev/sda

```
which apparently sets the power management for /dev/sda to a lower level. Works fine for me, I run a little one-liner script to do it
EDIT: [there](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking), under the possible Linux solution

---

