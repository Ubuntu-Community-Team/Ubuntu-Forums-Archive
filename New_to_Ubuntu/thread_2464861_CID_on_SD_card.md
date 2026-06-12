---
title: "CID on SD card"
date: 2021-07-14
forum: New to Ubuntu
---

### Post by stovo on 2021-07-14
Hi,
I download lubuntu_16.04_32bit-mmc, on my laptop with SD reader built in. Please write me line/s command/s how to see CID on SD card?
Thanks

---

### Post by Holger_Gehrke on 2021-07-14
Lubuntu 16.04 has been out of support for quite a while now. Even 18.04 (the LTS release after 16.04) is out of support. Unless you keep that system completely isolated from the network it's an ideal entry point for any wanna-be hacker because you won't get any updates or bug fixes.

That said, this
```

cat /sys/block/**mmcblk0**/device/cid

```
should get you what you want. Replace the bold part with the name of your device.

Holger

---

### Post by stovo on 2021-07-14
Thanks Holger, but when code [COLOR=#000000][FONT=&quot]cat /sys/block/[/FONT][/COLOR]**sdc1**[COLOR=#000000][FONT=&quot]/device/cid, its prompt: No such file or directory. What wrong?[/FONT][/COLOR]

---

### Post by Holger_Gehrke on 2021-07-14
If there's no mmcblk? device, then you're probably using an USB card reader which doesn't expose the status registers of the SD card. The built-in card readers of many laptops are connected through PCI or PCIe and do expose those registers.

---

### Post by stovo on 2021-07-14
Yes, you are right (USBSTOR\GenDisk), I will tray on PC, thanks again

---

### Post by ActionParsnip on 2021-07-14
I suggest you use Focal (Ubuntu 20.04). It is LTS and supported until April 2025

---

### Post by jonatan72 on 2021-12-19
> **stovo said:**
> Hi,
I download lubuntu_16.04_32bit-mmc, on my laptop with SD reader built in. Please write me line/s command/s how to see CID on SD card?
Thanks

Hi
Where did you find that iso? and how did you installed it? I'm trying with usb pen drive but unsuccessfully.
Thank you

---

