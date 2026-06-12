---
title: "trouble trying Ubuntu and Ubuntu GNOME from live DVD"
date: 2014-12-31
forum: New to Ubuntu
---

### Post by Allen McBride on 2014-12-31
Hi folks,

I just bought a Dell Inspiron 7737 after 15 years of using Macs, with the intent of using Linux as my primary OS. It uses the i7-4510 and NVIDIA GeForce GT 750M. I have burned live DVDs of Ubuntu 14.10 and Ubuntu GNOME 14.10, to try before installing.

I can use Ubuntu from the live DVD until I try to wake up the computer: Waking from sleep, I can see the desktop but it won't take any input at all, mouse or keyboard. Waking from hibernation (which it seems to slip into after a short time of sleep), I get a black screen with a mouse cursor I can move around, but that's it.

When I try the Ubuntu GNOME live DVD (just because I like what I've seen of GNOME 3), I get an MMIO write fault [edit: from nouveau] and then the command line. From what I read, this has something to do with Ubuntu trying to use open source drivers for my nvidia card. I read somewhere to add "nomodeset" after "quiet splash" in the boot line thingy. When I do that, I still just get the command line, but this time with a "cannot turn on display power on i915" error.

Any suggestions? I'm not a beginner with using *NIX in general, so I'm comfortable with a command line and all, but I am a beginner when it comes to installing Linux on my own machine, especially when there's a dedicated GPU involved.

Thanks!
--Allen

---

### Post by Tuxclear on 2014-12-31
Usually there is no connection between liveCD and installed system. Try to install Ubuntu, do the updates when you finish and see if there are any problems.
If you can't do the installation because of this disable auto-sleeping in System settings>Brightness and lock>Disable screen if left inactive for: (set never) and set Lock: off.

---

### Post by Allen McBride on 2014-12-31
Thanks! I'll give it a try.

---

### Post by grahammechanical on 2014-12-31
A Ubuntu live session does not hibernate. It does have a screen lock that activates after about 5 minutes of inactivity. During installation the screen will go blank unless we move the mouse. That usually restores the desktop.

The Ubuntu live session does not use proprietary video drivers because proprietary software is not included in the Ubuntu ISO image that we burn to DVD. The Ubuntu live session uses an open source video driver and if it was not working with your Nvidia card then you would not be getting a live session desktop.

When we install we get an option to install third party software at the same time. This third party or proprietary software includes video and audio codecs and a proprietary video driver. I have an Nvidia video adapter and I find that the open source video driver (called Nouveau when used with Nvidia cards) works very well.

The above information also applies to the live sessions of all the Ubuntu flavours including Ubuntu Gnome. I am guessing that you have hybrid graphics. That means an Intel graphic adapter on the motherboard and an Nvidia video adapter in a motherboard slot. It may be called Nvidia Optimus technology.

In this case you need either the Nvidia driver or the Bumblebee open source video driver. A driver for the onboard Intel adapter is built in to the Linux kernel. If you do indeed have hybrid graphics then I guess that using the BIOS/UEFI to set the video adapter to Intel would be better during installation than running on the Nvidia card.

Regards.

---

### Post by Allen McBride on 2015-01-01
Thank you grahammechanical; this is helpful! Sorry I didn't see your post earlier; I thought I'd get an e-mail notification but I didn't. --Allen

---

