---
title: "Black screen at booting with GRUB"
date: 2011-05-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-05-15
I'm using grub-pc 1.99~rc1-13ubuntu3 and GRUB_GFXPAYLOAD_LINUX is set to a resolution (for example 1680x1050-24) and GRUB_CMDLINE_LINUX_DEFAULT is empty but the screen is black until the desktop environment starts (but I see a few lines text before the desktop environment starts).

But if the system is booted the virtual consoles has a resolution of 1680x1050 without any graphic errors. If I set GRUB_GFXPAYLOAD_LINUX to text I can see the boot screen with a resolution of 640x480. The boot screen worked with 1680x1050 some weeks ago without a problem. update-grub is done and in /boot/grub/gfxblacklist.txt is no graphic card listed. How can I get the bootscreen back or is this maybe a bug?

---

### Post by kansasnoob on 2011-05-16
I suspect a bug, this may be helpful:

[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I made some personal notes about how to revert to Maverick's grub2 (along with a couple of other things):

[http://ubuntuforums.org/showpost.php?p=10778491&postcount=55](http://ubuntuforums.org/showpost.php?p=10778491&postcount=55)

NOTE: I only stuck that in my old "revert to legacy grub" thread because I needed a 'placeholder' so I could refer folks to it as a simple copy-n-paste procedure.

I'm not able to troubleshoot the bug myself since I've not been able to duplicate it on my own hardware.

---

### Post by Sworddragon on 2011-05-16
I have now tried the things in the thread but they hasn't helped. At least I reverted to GRUB from maverick and purged before the old GRUB installation. But the screen is still black at booting (but the maverick version worked some time ago without a problem). It seems the problem is not GRUB. It must be something else.

---

### Post by MAFoElffen on 2011-05-19
> **Sworddragon said:**
> I'm using grub-pc 1.99~rc1-13ubuntu3 and GRUB_GFXPAYLOAD_LINUX is set to a resolution (for example 1680x1050-24) and GRUB_CMDLINE_LINUX_DEFAULT is empty but the screen is black until the desktop environment starts (but I see a few lines text before the desktop environment starts).

But if the system is booted the virtual consoles has a resolution of 1680x1050 without any graphic errors. If I set GRUB_GFXPAYLOAD_LINUX to text I can see the boot screen with a resolution of 640x480. The boot screen worked with 1680x1050 some weeks ago without a problem. update-grub is done and in /boot/grub/gfxblacklist.txt is no graphic card listed. How can I get the bootscreen back or is this maybe a bug?
/etc/default/grub
```

GRUB_GFXMODE=1680x1050x24

```You can also add more resolutions if you separate them with a semi-colon
Especially if you are running 64bit kernel, you could add a VGA=xxx kernel set mode switch, where xxx is a vesa mode support by your video card...

If you used startup-manager, it set's both those, but in doifferent places (where they would get overwritten by an update-grub...)

Refer to this sticky:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Sworddragon on 2011-05-19
I tried already setting GRUB_GFXMODE but this hasn't helped (is 1680x1050x24 valid? Shouldn't it be 1680x1050-24? On my tests GRUB hasn't accepted a depth with x. Only - worked successful). I tried even vga=369 (in the GRUB console too) some time ago but this hasn't changed anything. The screen is still black.

I know your thread from a previous post in this thread and tried the things listed there. But nothing helped.

---

### Post by Sworddragon on 2011-07-31
I have now complete reinstalled my system with Ubuntu 11.04 and made a dist-upgrade to 11.10 dev but there is no change. The screen is the most time still black.

---

