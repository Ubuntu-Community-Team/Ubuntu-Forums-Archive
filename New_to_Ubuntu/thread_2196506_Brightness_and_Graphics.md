---
title: "Brightness and Graphics"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by kenton.nieman.cast on 2013-12-29
So, I can't adjust my brightness. My computer is a Dell Inspiron N7010. Please help. :O
I have Ubuntu 13.10... Or is it 13.01... I don't think one exists so whichever one is correct! :P
Hmm... It is also quite slow at times. I was looking around here some time ago and I think it might be a graphics issue?
It might be tied to the birghtness too. :(
Anyway. Please help if you can. :)

---

### Post by oldfred on 2013-12-29
Dell's are pretty common across models.

 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
> Running in legacy BIOS mode or in UEFI mode both work, but for now  you'll need to enable "Legacy Option ROM" in the BIOS if you're running  in UEFI mode because of the display's backlight. This is because of an  issue with the Intel i915 driver that currently affects several systems  from many vendors. If you don't enable this BIOS option, the backlight  will be stuck at the lowest setting in Linux.


 Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

---

### Post by kenton.nieman.cast on 2013-12-30
> **oldfred said:**
> 
 Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)

I found that thread soon after I posted this and it isn't much help either.

---

### Post by joe4ska on 2013-12-30
have you tried xbacklight?
It can be used to manually map your keys to control backlight
[http://manpages.ubuntu.com/manpages/raring/man1/xbacklight.1.html](http://manpages.ubuntu.com/manpages/raring/man1/xbacklight.1.html)

once you install it you can simply type a terminal command to set, increase or reduce your backlight.
Then if you like you can go into the keyboard preferences and manully set a key or keys. In the past I've done this prior to my laptop being fully supported.

---

### Post by Toz on 2013-12-30
Which graphics card(s) do you have?
```
lspci -k | grep -iA2 VGA
```

Which, if any, kernel boot parameters are you using?
```
cat /proc/cmdline
```

And how many and which backlight interfaces do you have?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

Note: Open a terminal window, run the above commands and post back the results.

---

### Post by kenton.nieman.cast on 2013-12-30
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
    Subsystem: Dell Device 0457
    Kernel driver in use: i915
```

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
    Subsystem: Dell Device 0457
    Kernel driver in use: i915
```

```
/sys/class/backlight/dell_backlight
15
15
15
/sys/class/backlight/intel_backlight
4882
4882
4882
```

---

### Post by Toz on 2013-12-30
What is your kernel boot line:
```
cat /proc/cmdline
```

Are you using acpi_backlight=vendor?

---

### Post by kenton.nieman.cast on 2013-12-30
```
BOOT_IMAGE=/vmlinuz-3.11.0-14-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7
```

---

### Post by Toz on 2013-12-30
Try this:

Create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...and log out and back in again to test.

---

### Post by kenton.nieman.cast on 2013-12-30
So... I did that and I had to reinstall Ubuntu because it wouldn't do anything after start-up. Just a blank screen.

---

### Post by Toz on 2013-12-30
> **kenton.nieman.cast said:**
> So... I did that and I had to reinstall Ubuntu because it wouldn't do anything after start-up. Just a blank screen.

Did you try to adjust the brightness using the brightness function keys when the screen was blank? There was no need to reinstall, you could have booted into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode") and deleted the file. I think what probably happened was that it started to use the intel_backlight interface and unfortunately the brightness was set to 0 so you didn't see anything.

Are you back at square 1 again? If you're willing to try another approach, follow the "Temporarily Add a Kernel Boot Parameter for Testing" instructions [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") and add the **acpi_osi=Linux acpi_backlight=vendor** kernel paramaters during the boot up (if the screen is blank again, simply restart and it will return you to your current configuration).

If it boots up properly, check your brightness function keys and post back the results from my first reply in this thread.

Also, as a follow-up, did you make the change to your bios as oldfred recommended earlier?

---

