---
title: "USB_Modeswitch Modem ZTE 2971"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by guragura on 2012-08-17
Hello all,

I am newbie user of Ubuntu 12 in my HP Mini notebook. Installation was clean, however when i plugged in my ZTE 2791 modem, i can't start the connection. However the modem was detected and new connection was available to be selected and added. 

I tried to use the lsusb command and it shown as 19d2:fffe. Then i am using the usb_modeswitch and add 19d2:ffde and 19d2:fff5 files to refer the device. But nothing change, unless the modem was detected as cdrom then usb storage.

But now I can't even detect the modem. Even after i erase configuration within the files.

Please helppp.. :confused:

---

### Post by guragura on 2012-08-17
Hm.. Okay i remove all the settings and rule in modeswitch, the modem detected as 19d2:fffe again. the modem also detected to connect eventhough its failed. looks like im returning to square one.

i can only hope there are updates for this modem to connect correctly. meanwhile ill keep posting my updates on the modem, hope it will also usefull for others.

---

### Post by NikTh on 2012-08-17
Hi , 
can you please post the output of 
```
lsmod 
lsusb
df
``` with usb attached ? 

Put the output between ```
 tags. 
[noparse][code]the output here
```[/noparse]

---

