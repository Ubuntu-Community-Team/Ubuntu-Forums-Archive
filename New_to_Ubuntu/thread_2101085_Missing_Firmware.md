---
title: "Missing Firmware"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by 122jdh on 2013-01-03
Finally got the installer running on my Ibook G3 (Lubuntu Alternate ISO 12.10) and going through the installation when detecting my network hardware I get this message: missing the non-free firmware file "agere_sta_fw.bin". Now I've read that this can just be skipped, but then the next screen asks me which network interface to use, my wired or wireless? Can I select my wireless? And will my Airport card work without that file, or should i install orinoco, and do i have to install that after installation or can i during?

---

### Post by coldcritter64 on 2013-01-03
**If** the firmware file is for the wireless card, then the wireless won't work until it is installed. You can still use ethernet (wired) to do the install, hence I suspect that is why you were told the firmware file can be skipped.

If a piece of hardware is not critical during installation its firmware can be added from the repos as necessary later, after the base install is completed.  I have the impression that "orinoco" is the brand of your wireless card, and googling indicates the missing firmware is for it. In such a case the wireless interface should NOT be chosen during install.

---

