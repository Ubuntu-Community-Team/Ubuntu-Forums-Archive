---
title: "Lost USB with Upgrade"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Ellaine on 2008-11-03
This maybe windy! I found that on my new second system I had installed Gusty Gibbon & updated to Hardy Heron in 32 bit, and everything worked fine. The mobo is 64 Bit, so I blanked the drive to install 64 bit Ubuntu. I d/l the 7.10 64 bit .iso and installed. Worked PERFECT. Installed the Video stuff I wanted from Stchman.com. Rebooted and everything including USB worked fine & played a DVD movie. With foresite I made a acronis image running 7.10. I then updated to 8.04 thru the Update Manager. Install took about an hour and works fine: except I have NO USB. I mean the front hub panel doesn't work and the direct mobo usb ports are dead. This is a single Hard Drive system with only Ubuntu loaded on an 80GB drive  (No Windows). Bios has all USB ports enabled. I removed the 8.04 drive and booted to XP and the usb works fine. I then reinstalled the 8.04 drive and using the acronis image reverted to 7.10 & it works perfect with USB. 

Did I do anything wrong? Any ideas?

---

### Post by brandoncolorado on 2008-11-03
> **Ellaine said:**
> This maybe windy! I found that on my new second system I had installed Gusty Gibbon & updated to Hardy Heron in 32 bit, and everything worked fine. The mobo is 64 Bit, so I blanked the drive to install 64 bit Ubuntu. I d/l the 7.10 64 bit .iso and installed. Worked PERFECT. Installed the Video stuff I wanted from Stchman.com. Rebooted and everything including USB worked fine & played a DVD movie. With foresite I made a acronis image running 7.10. I then updated to 8.04 thru the Update Manager. Install took about an hour and works fine: except I have NO USB. I mean the front hub panel doesn't work and the direct mobo usb ports are dead. This is a single Hard Drive system with only Ubuntu loaded on an 80GB drive  (No Windows). Bios has all USB ports enabled. I removed the 8.04 drive and booted to XP and the usb works fine. I then reinstalled the 8.04 drive and using the acronis image reverted to 7.10 & it works perfect with USB. 

Did I do anything wrong? Any ideas?

I am fairly new to this, but I think this may give us some more information.

Terminal >     lsusb

---

### Post by brandoncolorado on 2008-11-03
Does it make a difference if you have the devices plugged in when you restart, or after the system has fully booted?

---

### Post by Ellaine on 2008-11-03
I can't run terminal isusb since I replaced 8.04 with 7.10. Also I didn't boot with a usb traveldrive installed. Put in after running from the desktop like I always do. In 7.10 if i put in a traveldrive it is found right now and opens. In the upgraded 8.04 No usb was found. Previously in the 32 bit 7.10>8.04 upgrade the USB worked just fine.

---

### Post by brandoncolorado on 2008-11-03
> **Ellaine said:**
> I can't run terminal isusb since I replaced 8.04 with 7.10. Also I didn't boot with a usb traveldrive installed. Put in after running from the desktop like I always do. In 7.10 if i put in a traveldrive it is found right now and opens. In the upgraded 8.04 No usb was found. Previously in the 32 bit 7.10>8.04 upgrade the USB worked just fine.

Lsusb

---

### Post by Ellaine on 2008-11-04
Solved: Upgraded to 8.04 again. Still no usb. Ran lsusb in terminal and USB started working. Thanks much!

---

