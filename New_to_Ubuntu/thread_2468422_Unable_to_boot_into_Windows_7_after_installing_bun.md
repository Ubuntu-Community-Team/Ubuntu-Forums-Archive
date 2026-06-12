---
title: "Unable to boot into Windows 7 after installing buntu 20.04.3 LTS"
date: 2021-10-29
forum: New to Ubuntu
---

### Post by g1-worxs on 2021-10-29
Hi, I'm just getting started with Ubuntu. 
I installed Ubuntu 20.04.3 LTS on my PC with Windows 7 previously installed. 
At first I encountered a fatal error message saying something like grub fatal error - failed to install on dev/sda.
So, I used boot repair and successfully solved the issue.
But then, my PC boot straight away to Ubuntu without the boot menu where I could choose to boot on Windows 7. So, my now I'm having problem booting into my Windows 7 OS.url of the Paste from boot-repair:
[https://paste.ubuntu.com/p/jDywB8f2Rg/](https://paste.ubuntu.com/p/jDywB8f2Rg/)

---

### Post by grahammechanical on 2021-10-29
Did you see the comments at the end of the Boot Repair report? 

> LegacyWindows detected. Please enable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware,
The boot of your PC is in UEFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode

Did you follow these instructions? 

You have a UEFI motherboard and Windows 7 installed in BIOS/Legacy mode. It is the only mode that Windows 7 could be installed in on a UEFI motherboard. Ubuntu can be installed in either BIOS/Legacy mode or UEFI mode. I am guessing that you installed Ubuntu in UEFI mode. Now the two installations are incompatible.

From what I have learned if we load the Ubuntu installer USB memory stick in UEFI mode then Ubuntu will install in UEFI mode. If we load the Ubuntu USB memory stick in BIOS mode Ubuntu will install in BIOS mode. Try enabling BIOS/Legacy mode and see what happens. If Ubuntu loads you can run this command:

```
sudo update-grub
```

See if the printout records the existence of Windows 7. If it does then you should see Windows 7 in the Grub boot menu. Or, you may need to re-install Ubuntu in BIOS mode to be compatible with the BIOS mode boot of Windows 7. Some of us will surely advise to stop using Windows 7 altogether as it no longer receives security updates. Or, does it?

Regards

---

