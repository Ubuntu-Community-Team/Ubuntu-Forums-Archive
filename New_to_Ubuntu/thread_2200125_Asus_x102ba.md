---
title: "Asus x102ba"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by john_stambaugh on 2014-01-17
I have tried several Linux distros on my new asus x102ba. none work. closest is saucy salamander which I got in a magazine. it boots up  until it gets to a screen that says "running in low graphics mode". I click ok
(touch screen works). then a screen says "run in low graphics for just one session" there are other options, but cannot click on any of them. I click ok, then it says "stand by for one minute while displays restarts"
I click ok and screen goes blank and the computer goes completely inert. the only thing that has any effect is the on/off switch. according to device manager it has the following in it:
video is AMD radeon HD8180
it is ACPI x64 based 
wifi  Atheros ar 9485  which I think works because when it is booting before it says running in low graphics, at the top the little wifi sign is on and I can see local wifi
processors  AMD A4-1200APU with radeon (TM) HD graphic

I went to AMD site and they have Linux drivers which I downloaded, onto windows 8.1. but I have no idea how to proceed from here. any help I would be most grateful for. I really like the small 10in computer and am
learning to live with windows 8.1 altho we still have major issuses. I think windows 8 is mostly for watching video's and playing games, not for use at work.

---

### Post by grahammechanical on 2014-01-17
It might be a problem with the video driver. The best I can offer is to select Advance Options for Ubuntu at the Grub menu and then select Recovery Mode. At the Recovery menu select Resume. That may load to a desktop without activating the proprietary video driver. The user experience may not be that good because you will have a fallback video mode for machines that cannot run accelerated graphics but if it gets us to a working desktop we can experiment with other video drivers.

Once at the desktop open System Settings (power/cog menu). load Software and Updates and open the Additional Drivers tab. We need to be on the Internet and to allow time for the utility to search for appropriate drivers. We will need to reboot afterwards.

Regards.

---

### Post by john_stambaugh on 2014-01-17
thanks for reply. but it never gets to a grub screen. it just says low graphics and then goes blank and never comes back on. evidently there are drivers but I don't see how they can be installed when there is nothing on the screen.

---

