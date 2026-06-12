---
title: "Horizontal lines across the screen"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by FourFourSeven on 2014-07-22
Yesterday, I downloaded and installed ~50-60 MBs worth of OS updates for Lubuntu (I'm current on the latest version, 14.04). However, after rebooting to complete the update, a series of horizontal white stripes appeared on the screen from top to bottom. I'm not yet knowledgable on basic Linux administration, much less on how to change the video settings & drivers, so I'm at a loss as of what to do at this point besides doing a full reinstallation. Any ideas?

---

### Post by Bucky Ball on 2014-07-22
Welcome. Reboot the machine. Are you getting to the grub list? A list of kernels/OSs to choose from? If not, hit the shift key directly after the BIOS screen at boot. Once you're at the menu, choose the kernel you'd like to boot (probably the one at the top) and hit 'e' key. This will let you edit the entry. 

Find the line that ends with 'quiet splash' or one of those words or either in any order (the kernel line). After a space at the end of that line add:

nomodeset

Follow the instructions at the bottom of that screen to save and boot (ctrl+x, F10 from memory, but check).

My punt here is that the update has somehow obliterated your video drivers and that your card is Nvidia. I could be totally off the mark, but see if this works first before we move on. 

Did you install a video driver from 'Hardware Drivers' (could be Additional Drivers in your flavour)? I'm also presuming that you can't get to a regular, workable desktop, only the horizontal bars?

---

### Post by FourFourSeven on 2014-07-23
The "quiet splash" didn't come at the end of the line, only before "$vt_handoff". Regardless, I placed "nomodeset" at the end of that line and rebooted. My monitor resolution then went down to 640x480 after reboot, with no other option to change from in "Monitor Settings". However, after going back to the boot parameters, I noticed that nomodeset was gone and the horizontal bars returned after the subsequent restart.

I have not installed any other hardware drivers, only the ones that came preinstalled with Lubuntu. And you're right about using Nvidia, but it's not the graphics brand used, it's the board chipset (graphics are PowerColor ATI HD3850).

---

### Post by Bucky Ball on 2014-07-23
Do the nomodeset routine again, and this time, when you're at the desktop, check 'Additional Drivers' (might be Hardware Drivers for you). Anything there for the ATI graphics? Give it a bit of time to think ...

---

### Post by FourFourSeven on 2014-07-23
It couldn't find anything. I even checked "Canonical Parters" in the "Other Software" tab, and Software & Updates still couldn't find anything.

---

### Post by QIII on 2014-07-23
Unfortunately, you won't find a driver that will work.  AMD/ATi no longer provides a proprietary driver for that adapter that will work for current versions of Ubuntu or any distro that uses the current X Server.  ATi support in Linux has been discontinued for HD 4xxx graphics adapters and earlier.  So you'll need to use the default open source Radeon driver that is installed with Ubuntu (all flavors) by default.  

Not to worry.  The Radeon driver has improved by leaps and bounds over the last couple of years.

You can make the nomodeset permanent by (this is from memory, so maybe wait for someone else to see if I have missed something.):

```
gksudo whateveryourtexteditoris /etc/default/grub
```

find the line 

```
GRUB_CMDLINE_LINUX_DEFAULT="......
```

and add nomodeset, for instance:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Don't remove any other stuff set there, just add "nomodeset" into the list.

Update grub

```
sudo update-grub
```

and reboot.

---

### Post by Bucky Ball on 2014-07-23
@QIII: I think your memory serves you correctly. ;)

---

### Post by FourFourSeven on 2014-07-23
> **QIII said:**
> Unfortunately, you won't find a driver that will work.  AMD/ATi no longer provides a proprietary driver for that adapter that will work for current versions of Ubuntu or any distro that uses the current X Server.  ATi support in Linux has been discontinued for HD 4xxx graphics adapters and earlier.  So you'll need to use the default open source Radeon driver that is installed with Ubuntu (all flavors) by default.  

Not to worry.  The Radeon driver has improved by leaps and bounds over the last couple of years.

You can make the nomodeset permanent by (this is from memory, so maybe wait for someone else to see if I have missed something.):

```
gksudo whateveryourtexteditoris /etc/default/grub
```

find the line 

```
GRUB_CMDLINE_LINUX_DEFAULT="......
```

and add nomodeset, for instance:

```
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

Don't remove any other stuff set there, just add "nomodeset" into the list.

Update grub

```
sudo update-grub
```

and reboot.

What would I do about the 640x480 resolution? Nomodeset causes that, and Monitor Settings won't show any other option besides it.

---

### Post by Bucky Ball on 2014-07-23
So nomodeset has gotten rid of the horizontal lines? We have gotten that far?

---

### Post by FourFourSeven on 2014-07-23
Yes, with nomodeset the lines are gone, but I am not able to switch the resolution higher than 640x480.

---

### Post by FourFourSeven on 2014-07-30
Bump.

---

### Post by FourFourSeven on 2014-08-04
Bump (still having problems with the lines).

---

