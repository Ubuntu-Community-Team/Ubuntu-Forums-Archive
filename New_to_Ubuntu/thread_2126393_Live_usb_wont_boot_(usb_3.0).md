---
title: "Live usb wont boot (usb 3.0)"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by the most naive user on 2013-03-16
I have a Ubuntu live usb .. and have set usb as the first device
When I try to boot . all I see is a black screen with a cursor blinking forever. When remove the USB drive . I get a Operating system load error on the black screen and then windows loads.
I tried installing Suse Linux . after I was unable to install Ubuntu 12.10 64-bit. Suse Linux had exactly the same fate. Black screen with blinking cursor.

1)Right now my bios is in legacy mode. Also my windows sysinfo32 shows secure boot as unsupported.

2)I am using windows 8 ( though my computer has bios in legacy mode)
3)the usb drive I am using is a usb 3.0 drive formatted as fat32 . I used universal boot installer and then unetbootin to write the iso to usb.

Where can I be going wrong . Both Ubuntu and suse Linux do no boot ??

---

### Post by Bashing-om on 2013-03-17
the most naive user;


Only the more likely cause: graphics driver.
If you are running ATI (AMD) or Nvidia cards:
Cold boot the ubuntu install usb;
As soon as the bios screen clears depress and hold the shift key ->language screen, escape key to accept the default ->
boot options screen -> f6 key for the preset options; try the "nomodeset" option first; f10 key to continue to boot.

advise on results, further instructions are pending.

---

