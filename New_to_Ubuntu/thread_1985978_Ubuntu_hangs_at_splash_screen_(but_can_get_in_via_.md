---
title: "Ubuntu hangs at splash screen (but can get in via recovery)"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by wormbuntu on 2012-05-24
Hi,
 
I installed Ubuntu for the first time a couple of weeks ago. 
 
The porblem I have encountered is that on booting, I freeze at the screen that says 'ubuntu' with 5-6 dots underneath it.
 
If I boot via the recovery option, this does not happen. (This is confusing as I merely boot into the recovery menu and then choose to continue with the normal boot.
NB that when I boot through the recovery menu I seem to have lost customisation made to the desktop (eg transparency of dash, icon size etc.) I have also lost the Compiz effects such as desktop cube.
 
I strongly suspect that I've messed something up in the process of tinkering with Compiz settings. But not sure of the easiest way to reset it all.
 
Other info:
Clean install (dual boot) on Dell L502X. Dual graphics card/optimus solution provided by bumblebee.
 
Thanks in advance for any help.

---

### Post by Peter09 on 2012-05-24
Sounds like its your graphics drivers. Check to see if the third party software app is asking you to install a graphics driver.
 
What graphics card have you got?

---

### Post by wormbuntu on 2012-05-24
> **Peter09 said:**
> Sounds like its your graphics drivers. Check to see if the third party software app is asking you to install a graphics driver.
 
What graphics card have you got?
 
Hi - thanks for posting.
 
Am using Bumblebee, which uses nvidia proprietry drivers. But the PC was working fine with this from day 1. The only change I can think of, which could have broken it, would have been tinkering with Compiz.
 
Graphics card is GT 540M, with optimus. Bumblee basically disables this and uses the onboard intel card for normal computing (am not playing any games).

---

### Post by Peter09 on 2012-05-24
You could try
 
```
unity --reset
```
 
and I think there is a switch in myunity to return compiz to default (but not sure on that).

---

### Post by wormbuntu on 2012-05-24
> **Peter09 said:**
> You could try
 
```
unity --reset
```
 
and I think there is a switch in myunity to return compiz to default (but not sure on that).
 
Hi - yep have tried this. But to no avail.
I also uninstalled and re-installed graphics drivers and bumblebee. I've turned off quietsplsh to try to see what's happening during boot - but no clues there.
This morning the PC hung at a different point from before. I think I'm going to have to do a clean install - and this time, no compiz.

---

### Post by lilmagnus on 2012-05-24
Maybe you can find some help [in here]("http://ubuntuforums.org/showthread.php?t=1981181"). References to nvidia+compiz on 12.04.

HTH

---

### Post by |{urse on 2012-05-24
Output of 

dmesg | grep failed

Prease

Edit: Can you boot in at all or does it just hang for a loooong time without livecd?

---

### Post by wormbuntu on 2012-05-27
> **|{urse said:**
> Output of 

dmesg | grep failed

Prease

Edit: Can you boot in at all or does it just hang for a loooong time without livecd?

Hi - will post asap.

To answer your other question. It sits there forever (OK I left it for an hour and that is forever for booting).

Key thing I just noticed - it seems to happen on battery power only. Will dbl check this.

Thanks in advance for your help - will post the dmesg data asap.

---

### Post by wormbuntu on 2012-05-28
> **|{urse said:**
> Output of 

dmesg | grep failed

Prease

Edit: Can you boot in at all or does it just hang for a loooong time without livecd?

 results of dmesg (failed):  [    0.072512] x2apic not enabled, IRQ remapping init failed [    1.180432]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d [   14.226745] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed [   14.226793] [drm:intel_dsm_platform_mux_info] *ERROR* MUX INFO call failed   Please note, that this is what I get when I have booted successfully (IE when power is connected)  Thanks

---

