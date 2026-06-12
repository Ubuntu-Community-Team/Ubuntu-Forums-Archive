---
title: "Can't Boot To USB"
date: 2019-09-18
forum: New to Ubuntu
---

### Post by venomx2 on 2019-09-18
[COLOR=#14233C][FONT=Helvetica]Used rufus to mount ubuntu to a sandisk 16GB
Turned PC off, put USB in and then turned on. But it wont load

I have “removable” selected in the bios for the primary boot device but no luck
Also have USB selected in hdd group priority[/FONT][/COLOR]
[COLOR=#14233C][FONT=Helvetica]Got into boot menu and hit enter on my SanDisk USB drive “usb-hdd0” but no luck[/FONT][/COLOR]

---

### Post by oldrocker99 on 2019-09-18
Do you get a "Operating System Not Found" message?

Then, try reburning the USB. Etcher is nearly perfect for the purpose. Also, double-check to see that the USB **is** set for first boot device.

You should also check the SHA256 checksum against the posted one.```

sha256 filenanme
```

Good luck!

---

### Post by Autodave on 2019-09-18
I have seen 2 different machines that would only boot from an external DVD player.  If you have access to such a thing, you may want to try that.

---

