---
title: "[SOLVED] &amp;quot;Failed to start the X server&amp;quot; with new P4M900-M4 motherboard"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by ricardisimo on 2008-08-12
I recently installed a new P4M900-M4 motherboard in my home desktop as an upgrade over one that wouldn't allow me to upgrade past 7.04, but now when it starts up I get the Ubuntu loading progress bar graphics, and then eventually:
```

Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?
```
When I hit "Yes" I get:
```
(EE) No devices detected
Fatal server error: No screens found
```
I tried running 8.04 off the LiveCD to see if maybe Feisty just didn't recognize the board or card, but the LiveCD desktop screen is covered in "noise" and double-images. Please see attached photo.

I also tried (as per a nearly identical laptop thread) reseating the RAM and changing the RAM chips. We tried two identical 512s, two different ones, just one, two identical 1Gig sticks, etc. No change at all (well, one configuration wouldn't even boot up.)

Is it possible that I will just need to configure X manually? Where do I begin, and how? Configuring X has proven to be next to impossible for me on 8.04, but I never had problems (with detailed instructions) in Edgy or Feisty. Thanks in advance for any help.

---

### Post by tech0007 on 2008-08-12
Google tells me your graphics chipset is VIA Chrome9 HC IGP which, IMHO is poorly supported.  Try to boot to recovery and use 'vesa' in xorg.conf. See if that gives you a decent display.

---

### Post by ricardisimo on 2008-08-12
I'll try vesa. Would "sudo lshw" or "lspci" in recovery mode give me the exact info for the onboard graphics? Once I have it, should I post here and ask, or is there a web resource I could check for the proper driver? Thanks for replying!

---

### Post by ricardisimo on 2008-08-15
I haven't had a chance to hook up the comp yet and try the vesa driver, but it occurred to me that this would not explain the screwed up screen off of the LiveCD. Theoretically, the Hardy installer would have selected the proper driver, no?

---

### Post by ricardisimo on 2008-08-18
vesa works quite well! I thank you very, very much.

Now I have another challenge: how do I set the driver to vesa in Hardy if [LIST=1]
[*]I can't see the screen;
[*]I'm working off of the LiveCD installer, not the hard disk;
[*]Hardy&#347; version of xorg.conf has everything listed as "configured" rather than as an actual option.
[/LIST]
Very frustrating. Thanks in advance for any further help.

---

### Post by ricardisimo on 2008-08-18
I upgraded successfully to Gutsy via Update Manager, and provided I don't notice any glitches in the system, I'll probably upgrade to Hardy right away. [Normally I'd do a fresh install at each upgrade] However, is there any way to guarantee that the video driver will remain "vesa" after upgrade? If not, how do I change it, given that the xorg.conf in Hardy is going to be completely different from the ones for both Feisty and now Gutsy. Thanks again.

---

### Post by markbuntu on 2008-08-18
Hardy should start up with the vesa driver by default. It always did for me and my many installations. You can always log in in gnome safe mode if something goes wrong, that always uses the vesa driver. If it does not, you can edit the etc/X11/xorg.conf file from terminal mode and change the driver from Chrome or whatever to VESA.

---

### Post by ricardisimo on 2008-08-18
I thought that the new xorg.conf files just say "configured device" instead of listing the driver and resolutions, etc. Can I add in a driver line in the xorg.conf later if I need it?

---

### Post by ricardisimo on 2008-08-19
{bump}

---

### Post by markbuntu on 2008-08-19
> **ricardisimo said:**
> I thought that the new xorg.conf files just say "configured device" instead of listing the driver and resolutions, etc. Can I add in a driver line in the xorg.conf later if I need it?

Yes, you can. In fact that is how x knows which driver to use when there is a choice. ATI and Nvidia restricted driver users have a "Driver" line in their xorg.conf. Here's mine. You can change driver to VESA and you will get the VESA driver. I have done exactly that in the past when a kernel upgrade pooched my fglrx driver..

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

---

