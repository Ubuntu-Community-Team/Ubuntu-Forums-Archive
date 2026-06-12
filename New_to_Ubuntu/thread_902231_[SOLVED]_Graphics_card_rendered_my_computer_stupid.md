---
title: "[SOLVED] Graphics card rendered my computer stupid."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by roundidiot on 2008-08-27
I attempted to install a KFA2 Nvidia GeForce 8400gs PCIE card, got the "safe graphics mode message" and was unable to use mouse or keyboard.  Upon power down, uninstallation, and restart mouse and keyboard still don't work, although display appears normal through integrated graphics.

specs:
    500 W power supply
    XFX MG-610i-7059 775 mobo
    Pentium D 945 3.40 GHz processor

This feels like a hardware problem, I think I'm, you know, efed.  Please help.  Thanks.

---

### Post by northern lights on 2008-08-27
Reconfiguring X should resolve the mouse, keyboard, and resolution issues. Then, configure driver and 3D acceleration via 'nvidia-xconfig'.

Navigate to "Applications > Accessories > Terminal" and run ```
sudo /etc/init.d/gdm stop
```You will exit the desktop environment, so you might want to jot down the next few lines. Hit "Alt+F1" to log into the shell. Run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then, restart the desktop environment```
sudo /etc/init.d/gdm start
```

Navigate to "System > Administration > Software Sources" and enable every repository but "proposed" and "backports". Now run ```
sudo apt-get update && sudo aot-get install nvidia-settings nvidia-xconfig && sudo nvidia-xconfig
```

Then hit "Alt+F2", type "nvidia-settings" and configure the rest from there.

---

### Post by roundidiot on 2008-08-27
Thanks but I currently have no working input devices on that computer, I suppose I could try a USB mouse or keyboard if I could hunt them down...

---

### Post by northern lights on 2008-08-27
> **roundidiot said:**
> I currently have no working input devices on that computer
Crappola.

Have you tried booting into Recovery Mode? If not, choose the "Recovery Mode" entry in the GRUB menu. If you usually don't get to see the bootmenu during boot-up, hit "ESC" when during the boot process you get to Stage 1.5.

Drop into a root shell and run ```
dpkg-reconfigure -phigh xserver-xorg
```

Boot back into your regular Ubuntu, and follow this from my above post:> **northern lights said:**
> Navigate to "System > Administration > Software Sources" and enable every repository but "proposed" and "backports". Now run ```
sudo apt-get update && sudo aot-get install nvidia-settings nvidia-xconfig && sudo nvidia-xconfig
```

Then hit "Alt+F2", type "nvidia-settings" and configure the rest from there.

---

### Post by halitech on 2008-08-27
have you tried unplugging and replugging in the keyboard and mouse? You may have justled them enough during the install of the video card that they aren't actually plugged in

---

### Post by roundidiot on 2008-08-27
> **northern lights said:**
> Have you tried booting into Recovery Mode?

Yeah, but the keyboard doesn't work at that point either, I can't even get into BIOS to switch the boot order so I can boot from a recovery CD.

> **halitech said:**
> have you tried unplugging and replugging in the keyboard and mouse?

On startup the locks on the keyboard blink once however so it's for sure plugged in.

I'm wondering if this is a good indication that I have, in fact, fried my motherboard...I'm gonna try to clear the CMOS.

---

### Post by northern lights on 2008-08-27
> **roundidiot said:**
> I'm wondering if this is a good indication that I have, in fact, fried my motherboard...
While I don't wanna say that you did for sure on the basis of a long-distance diagnosis, I'd dare say it's the most likely case.

Whether you actually irreversibly fried your board or not, if it happens not only also in Recovery Mode, but also pre-boot (BIOS, bootloader menu) it's definitely not a software or OS issue.

Try different peripherals (keyboard & mouse) before giving up on the board.
Does it have a jumper that resets it to factory default? If so, that's the last straw...

---

### Post by roundidiot on 2008-08-27
> **northern lights said:**
> Does it have a jumper that resets it to factory default? If so, that's the last straw...

Yes!  Works now, running memtest w/o errors so far.  I'm not sure what I should do to ensure a second attempt at installing the graphics card goes more smooth.  Everything seems to be compatible...

---

### Post by mfeltman on 2008-08-27
Here's a dumb question maybe but can you telnet/ssh into the b0rked PC to reconfigure xorg remotely?

---

### Post by roundidiot on 2008-08-27
> **mfeltman said:**
> Here's a dumb question maybe but can you telnet/ssh into the b0rked PC to reconfigure xorg remotely?

That question was so far from dumb I didn't even understand it.  If you mean can I log on from a remote desktop, I probably could if I had an ethernet cable.  Seeing as how it's working now I might have to do that when I try to re-install.

---

### Post by lswest on 2008-08-27
you'd have to set up an ssh server on the PC first, but then it would work fine.  I'd just suggest changing the driver for the graphics card to vesa before installing the card again (if you have to), so that it doesn't have conflicting drivers that it tries to use.

---

