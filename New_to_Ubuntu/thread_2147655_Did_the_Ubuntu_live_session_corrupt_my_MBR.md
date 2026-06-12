---
title: "Did the Ubuntu live session corrupt my MBR?"
date: 2013-05-22
forum: New to Ubuntu
---

### Post by mskitty on 2013-05-22
My MBR was corrupted trying Linux Ubuntu 13.04. I created a bootable live usb drive for Ubuntu, then changed the boot order so it boots from the USB drive first. Then I selected the first option - Try Ubuntu.....then my computer froze during the live session, so I held down the power button to reboot and removed the usb stick. The system rebooted with the following message Error: BOOTMGR is missing. Press Ctrl-Alt-Del. But when I press ctrl alt delete it just brings me right back to the same error message. 

It's a possibility that my MBR was damaged or corrupted - how? 

Do I need a Windows 7 64 bit repair disk to fix this problem?    :confused:

---

### Post by monkeybrain2012 on 2013-05-22
I don't think it is possible (if it didt then I learn something new)

---

### Post by holycow131415 on 2013-05-22
no, it is just looking for your usb stick again, and thought it was still inserted. go back to your bios and change the boot order again.

---

### Post by Mark Phelps on 2013-05-23
The BOOTMGR message refers to it being unable to correctly find or use the Windows boot loader.  If GRUB was still in the MBR, it would try to use that boot loader and you would see something very different.

If changing the boot order doesn't fix this (which I think it won't), you will need to do boot repair on Win7 with a repair disk or install disk.

You can also try using Boot-Repair (see link) but it has mixed results with repairing Windows boot problems:  [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

