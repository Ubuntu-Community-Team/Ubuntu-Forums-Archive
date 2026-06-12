---
title: "Install problem of ubuntu 12.04 64 Bit"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by coffarok on 2012-08-10
Newbie here, be gentle.  :-)

Dell Inspiron 530
Intel Core 2 CPU6300 @1.86 GHZ

Trying to install ubuntu 12.04 64 Bit (I've tried both AMD & 386 from USB and CD).
Whether I choose install to disk or run from cd rom, the install/boot always hangs.

Researched a bit and tried different Boot Params to no avail.  Tried checking disk and that comes out fine.

When I try to install and the screen comes up with Ubuntu and the 5 small circles below, I press F6 and see the console.  Lines scroll by and I see some errors, but don't know what they mena
"pwconv: failed to change the mode of /etc/passwd- to 0600" is one error.
It goes through the part where it starts "* Starting... [OK]" and "* Stopping [OK]" items.
Always seems to stop @ "* Stopping save kernel message [OK]"

Seems to be having a hardware issue with something but I don't know what.

Thanks in advance for any help.

---

### Post by oldfred on 2012-08-10
Welcome to the forums.

What video card? And did you try nomodeset? I have nVidia and have to use nomodeset for liveCD or USB and first boot. I think now as part of install you can also tick off to add the drivers.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by coffarok on 2012-08-11
The card for the video is integrated into the motherboard.  I don't have a separate video card.  I doubt this helps...



I tried your suggestion for using nomodeset, to no avail.  I tried a couple of other settings too, no worky.
I did try using the Ubuntu boot CD on my work laptop and was able to get it running on that, so it definitely isn't a bad CD.

Thanks for trying.
Keith

---

### Post by coffarok on 2012-08-11
screen print didn't post, sorry...

the display adapter is Intel(R) G33/G31 Express Chipset Family

don't know if that helps determine what boot option to use.... I'm at a loss for what to try now.

thanks.

---

### Post by oldfred on 2012-08-12
Sometimes the Intel or the generic settings work also. But Intel usually just works without settings. 

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

