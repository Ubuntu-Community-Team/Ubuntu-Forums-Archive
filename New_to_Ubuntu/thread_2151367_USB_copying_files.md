---
title: "USB copying files"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by edward1100 on 2013-06-04
Hi everyone, 

I'm very new to ubuntu still, and I'm having some trouble copying some photos from my phone to my computer. Normally on windows when I plug in my phone a little popup box appears, and I can access the contents of whatver has been plugged in the usb. When I plug in my phone in ubuntu nothing happens! I can't find the folder where my phone will be either. So can someone please help me? :)

Thanks in advance.

---

### Post by MidnightGrey on 2013-06-04
Hi,

Most likely, your phone is set to MTP (Media Transfer Protocol) which doesn't play nicely with ubuntu. The easiest solution would be to switch your phone over to USB Mass Storage (it is usually under settings) if your phone supports it.
Otherwise the alternative would be to look up how to detect and mount MTP devices in ubuntu.

Hope that helps.

---

### Post by ptn107 on 2013-06-04
If your phone is Android, you can enable USB Debugging in developer settings.  This allowed me to transfer files without the need for special software.

---

### Post by Inoki on 2013-06-07
> **ptn107 said:**
> If your phone is Android, you can enable USB Debugging in developer settings.  This allowed me to transfer files without the need for special software.
This doesn't work for me either. I'm on Xubuntu 13.04 x64 and own a HTC Desire X and tried developer mode / debugging. When I connect my phone though, it appears, see below:

```
lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 10f1:1a2a Importek 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 008: ID 0bb4:0dd5 HTC (High Tech Computer Corp.) 
Bus 002 Device 004: ID 125f:a11a A-DATA Technology Co., Ltd. 
Bus 002 Device 005: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
```

---

### Post by Inoki on 2013-06-09
With Unity when plugging the phone in it says "Couldn't find / open corresponding Android device".

---

### Post by Inoki on 2013-06-14
I don't get it, today I plugged the one in and it worked. Sometimes it works, sometimes not, but I noticed, that in order to enable it to work I had to switch my USB connection to "share PC internet with phone" or "share phone connection (internet) with the PC".

Has there been an update?

---

