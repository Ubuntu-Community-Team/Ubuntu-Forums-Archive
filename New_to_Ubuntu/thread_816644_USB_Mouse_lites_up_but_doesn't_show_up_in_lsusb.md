---
title: "USB Mouse lites up but doesn't show up in lsusb"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by L0N3W0LF on 2008-06-02
Hi all. This is my third day running ubuntu hardy heron. I am trying to get my PC-GEAR USB (Optical mouse) to work. When I plug my USB mouse in it lites up and seems to work fine, worked on another PC running windows. But when I run lsusb in the console it doesn't show up o_o!. My other USB devices did show up. What could this possibly mean. Any help would be appreciated.

P.S: Could anyone tell me the command used to view the drivers that are being used in xorg.0.log. I read it somewhere but can't find it again. Thanks.

---

### Post by spiderbatdad on 2008-06-02
you can navigate to that file with the file browser /var/log/Xorg.0.log

or run in terminal: ```
cat /var/log/Xorg.0.log
```

---

### Post by L0N3W0LF on 2008-06-02
Thank you but now I remeber what it was. grep Driver /var/log/xorg.0.log. =P. Now if only I could find out why doesn't 'lsusb' detect my mouse. hmm

---

### Post by spiderbatdad on 2008-06-02
take a look at dmesg (run in terminal) after boot, with mouse plugged in.

---

### Post by memekthecat on 2008-06-02
I got something weird goin on with my mouse! after i shut down my pc its still lites up:confused: can anyone tell my what causing that to happen?

---

### Post by L0N3W0LF on 2008-06-02
Ok, so I booted my PC with the mouse (and a USB stick) plugged in. I read the output of the dmesg command (alot of scribbles =P). From what I could have gathered is that when it scanned for usb-storage devices it did find my USB stick but I didn't see anything that was related to a mouse besides this part:

```

[   16.908546] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.939389] mice: PS/2 mouse device common for all mice
[   32.606444] input: PS/2 Mouse as /devices/virtual/input/input8
[   32.661870] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input9

```

Coulnd't attach it because it was to big.
...no idea what I am doing. Maybe I should forget about it.

EDIT: Maybe my PC-GEAR USB mouse isn't supported?

---

### Post by spiderbatdad on 2008-06-02
you can do```
dmesg > dmesg.txt
```to write the small file to your home directory, for easier reading. Looks like it is trying to use a generic ps/2 mouse. You may need some special params added to xorg.conf...though it doesnt seem to have a driver. Also pci=routeirq will sometimes get devices working when added to the kernel line in /boot/grub/menu.lst

---

### Post by L0N3W0LF on 2008-06-02
So what you are saying is that the pc is configured to use a ps/2 mouse by default and I have to "tweak" the xorg.conf myself and add these "special params" you speak of to detect my usb mouse o_o? If that is so then I will go check out a tutorial about editing the xorg.conf file. The last part about the grub menu thing I will have to google later =P.

---

### Post by spiderbatdad on 2008-06-02
That is what I'm thinking. IDK if the mouse requires a special driver...maybe check the vendor. Sometimes vendor info gets included in xorg tweaks.

---

