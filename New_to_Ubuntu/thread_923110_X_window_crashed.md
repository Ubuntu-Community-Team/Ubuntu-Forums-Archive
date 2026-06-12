---
title: "X window crashed"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by DanielChan on 2008-09-18
Hi there,
I am a newbie in Linux. I installed my Ubuntu recently and have been OK with it. However, it crashed one day - x window quits and return to text mode. I rebooted the computer and I can see the normal logon screen. But it does the same thing immediately after logon. I re-logon and it insists to quit!
My computer is a Dell Optiplex 745. Display chip is intel 965Q. I've been suffering from this problem for weeks. Could any body help, please?
I've extracted the (WW) lines from /var/log/Xorg.0.log :
.
.
.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist. Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
.
.
.
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 965Q found
.
.
.
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000b00
(WW) intel(0): Register 0x70024 (PIPEASTAT) changed from 0x00000000 to 0x00000207
(WW) intel(0): PIPEASTAT before: status:
(WW) intel(0): PIPEASTAT after: status: VSYNC_INT_STATUS SVBLANK_INT_STATUS VBLANK_INT_STATUS OREG_UPDATE_STATUS
(==) Depth 24 pixmap format is 32 bpp
.
.
.
(WW) intel(0): Failed to set up write-combining range (0xc0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
.
.
.
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i965_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 473 x 296
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
.
.
.
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) intel(0): EDID vendor "DEL", prod id 53268
END

Thank you.
Daniel Chan

---

### Post by cmnorton on 2008-09-18
You can try logging into recovery mode, and running

dpkg-reconfigure xserver-xorg

accept all defaults, and see if that fixes it.

I note from the log that a directory is missing and was removed from the font path. I've got the same thing, and my X works fine:

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.


[B]
[/B]

---

### Post by DanielChan on 2008-09-19
Dear cmn,
Thanks for your tips. I tried, but the same problem still exists. I also found that it crashes only when I tried to launch an application like firing up Firefox or opening a terminal. When I do this, a message will display saying that the session will be down and I'll be returned to login screen after pressing OK. 
When I tried to change screen resolution, the screen will display alternatively all blue and white screens and I have to reboot the system. Also when I tried to display the hardware drivers(from System->Preference), the list is empty.
However, I can launch add/remove program without any problem. Could it be a driver problem. How can I reinstall a display driver?
Thanks again.
Daniel Chan

---

### Post by cmnorton on 2008-09-20
It depends on the graphics chip in your PC. You can use the instructions listed before to change to a different driver. For my Kubuntu Thinkpad T61p, I use vesa, which does not take advantage of the graphics chip, but allows me to work properly in a KVM environment.

You can also change drivers under the system administration menu.

---

### Post by anubhavrocks on 2008-09-20
What version of Ubuntu do you use?Also once you have X working properly make a copy of xorg.conf so that if things screw up you can restore the working xorg.conf file.

---

### Post by DanielChan on 2008-09-21
Hi,
I'm using Ubuntu 8.04. Although i can backup the xorg.conf, but I still cannot do any meaningful work in X environment. The whenever I try to launch, eg, Firefox, it just display a message saying that my session will be terminated, and it quits and returns to the login screen after clicking OK.
Please if anybody knows what has gone wrong? Let me know if you need more info.
Thank you.

---

### Post by willca on 2008-09-23
Sounds like an X file in your home directory is corrupted or something.

Do you have another user account setup on this box?
If not try to create one and login as that and see if it happens again.

Otherwise, you can delete all the .X* .x* in your home directory and then relogin.

---

### Post by DanielChan on 2008-09-29
I tried to log in as another user but still getting the same result. Could it be a bug somewhere in the OS?
Anyway, I give up. I'll reinstall my Ubuntu box. Thanks for all the gentlemen who have tried to help.

DanielChan

---

### Post by Tom--d on 2008-09-29
> **DanielChan said:**
> I tried to log in as another user but still getting the same result. Could it be a bug somewhere in the OS?
Anyway, I give up. I'll reinstall my Ubuntu box. Thanks for all the gentlemen who have tried to help.

DanielChan

If it stil does it in a new user, its a global effect on the system. So yeah, a bug somewhere I guess.

---

