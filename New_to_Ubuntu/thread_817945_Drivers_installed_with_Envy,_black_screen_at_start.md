---
title: "Drivers installed with Envy, black screen at startup"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by primky on 2008-06-04
I am having problems with drivers for about one month now, from where i started using ubuntu.
I have Ubuntu Hardy 8.04. Kernel is 2.6.24-17-generic.

I found this program EnvyNG, which automatically finds drivers for your video card and installs it.

When i do it, everything is OK, my card is recognized and it says it is supported by the latest drivers. I have Ati Radeon X1650. 

But when i reboot and where it should show up login screen, the whole screen is black.

Any advice or any help would help me A LOT!

---

### Post by ZabiGG on 2008-06-04
Are you using a monitor or a LCD/plasma TV? If you're using the latter, can you plug in a monitor to troubleshoot your installation?

---

### Post by bumanie on 2008-06-04
I would try booting into safe graphics mode which uses the vesa generic driver and then I would uninstall envy. There are as many users who have problems with envy as envy seems to help. Envy is not officially supported by cnonical/ubuntu. It seems that sometimes it works, sometimes it doesn't. I have always found the driver from Hardware drivers always works well, but I use a nvidia card, can't comment for ati cards.

---

### Post by FlyingPenguin542 on 2008-06-04
I'm having this same problem (though not on vanilla ubuntu specifically, but Linux Mint 5 Elyssa RC2). I have a Nvidia 8800 GT, and upon installing drivers with EnvyNG, GDM wouldn't start. It just hangs on... eh, some important-sounding-boot-initiation.rc, blinks to a black screen w/ _ and back (sorry, short-term memory's horrible). If, on the grub OS chooser screen, I arrow down to 2.6.24-17 [recovery version] and then run the repair Xclient option before selecting resume normal boot, I can get to my normal GDM screen and log in like normal, difference being: no compiz-fusion. When I check the restricted drivers manager, it says the nvidia drivers are in use, but the "Installed" indicator isn't checked. From what I've garnered from a few other posts, I should attempt to remove envy-ng and reinstall drivers in Synaptic from Ubuntu?

Oh, and I believe this started around the time I updated my kernel, then was curious as to what this "envy" thing in my Administration menu did, and had it install video drivers.

Any and all advice/directions/confirmation-that-I've-got-the-right-idea would be greatly appreciated! :)

----------update------------

Uninstalled all envy stuff completely and reinstalled standard nvidia accelerated drivers, and well as the linux kernel + backends + restricted stuff etc etc, to try and cover all the bases. On restarting the first time, it appeared to work like normal, finally, aside from not being able to find the mint gdm theme thus reverting to debian default. BUT. accelerated options don't work, despite Restricted Hardware Drivers saying they are (compiz rejects requests for any spiffy graphix). Thus, I am stuck. What I think I'll do, cuz I'm tired of dealing with this crap, is transfer my personal files to a flashdrive and wipe the partition, then reinstall Linux Mint. Because it was working before I messed with stuff. Ah well. Lesson learned, I guess.

---

### Post by primky on 2008-06-04
ZabiGG, i use LCD and i don't have monitor to try with it. But i doubt that could be the problem.

FlyingPenguin542, i have the exactly same problem.. 
I found this topic:
[http://ubuntuforums.org/showthread.php?t=800535](http://ubuntuforums.org/showthread.php?t=800535)
But it doesn't help me.

I tried about 2 or 3 step-by step installations, but nothing worked.

If i select ATI proprietary driver from Restricted Hardware Drivers, i get black screen at login again.

I love Ubuntu, but this thing with drivers is really a big minus. They should fix this, so it would be as easy as in Windows.

---

