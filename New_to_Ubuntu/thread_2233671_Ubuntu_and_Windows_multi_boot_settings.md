---
title: "Ubuntu and Windows multi boot settings"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by shalom3 on 2014-07-10
My laptop came in with pre installed windows 8. [COLOR=#000000][FONT=Helvetica Neue]Then I installed Ubuntu on my external hard drive (connects with USB 3.0). [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]I want to choose operating systems whenever I turn on the computer, but i can't. I always have to go to Win 8's "CHANGE PC SETTINGS" and restart the laptop with advanced settings so that I can select Ubuntu on the OS list. [/FONT][/COLOR]

[COLOR=#000000][FONT=Helvetica Neue]Is there anyway to configure my laptop to choose OS at the boot menu without having to go to all that trouble?

Thanks[/FONT][/COLOR];)

---

### Post by slooksterpsv on 2014-07-10
What kind of laptop is it? You should be able to go into BIOS disable fast-boot and press a key like F12 to get a boot menu where you can select hard drive, cdrom, network, or usb.

---

### Post by oldfred on 2014-07-10
Did you partition external drive with gpt and its own efi partition and install Ubuntu in UEFI boot mode? 

If Ubuntu is in BIOS mode you have to reboot as UEFI and BIOS are not compatible and once you start booting in UEFI mode you cannot change to boot in BIOS/CSM mode except from UEFI/BIOS menu.

But Windows seems to want to always shut down to boot anything else.

If both are UEFI, you may be able to set external as first in boot order to boot from the Ubuntu efi partition and chain load to the Windows efi to boot Windows. Then if external not plugged in, it will boot Windows directly. 

If not in same boot mode slooksterpsv suggestion should work.

---

### Post by shalom3 on 2014-07-11
thank you, there was an option named "Legacy settings" when i enabled it, prompts me to boot options.

---

