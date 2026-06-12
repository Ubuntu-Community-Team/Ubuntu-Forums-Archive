---
title: "Installation Problems | Failed to load ldlinux.c32"
date: 2021-01-19
forum: New to Ubuntu
---

### Post by glitcheddata on 2021-01-19
Hello, I am very new to ubuntu and I'm trying to install it on an old, Windows 7 PC via a bootable USB. I have followed the guide on the Ubuntu website on how to make a bootable Ubuntu USB. However, when i try to boot from the USB it gets as far as.
```
Verifiying DMI Pool Data .............
```
And then gives me this error
```
Failed to load ldlinux.c32
Boot failed: please change disks and press a key to continue
```
Things I have tried:
[LIST]
[*]Changing the boot priority so that the USB is first
[*]Booting from the USB via the boot menu
[*]re-flashing the .iso (I have tried Rufus, Universal USB Installer and UNetBootIn)
[*]renaming the 'isolinux' folder, 'isolinux.bin' and 'isolinux.cfg' to 'syslinux', 'syslinux.bin', and 'syslinux.cfg' (this was suggested in another forum)
[/LIST]

I have tried all of the above but to no avail. Any help would be much appreciated.

PS: System specs are

[LIST]
[*]CPU: Intel Pentuim(R) Dual-Core CPU @3.20GHz
[*]RAM: 4.00 GB
[*]GPU: NVIDIA GeForce GTS 450
[/LIST]


UPDATE:
I eventually found a DVD that I could burn the iso to. That worked perfectly. I beleive it is possible that i may have not set up the bios right for booting from usb but i guess i'll never know

---

### Post by ActionParsnip on 2021-01-19
Did you MD5 test the ISO you downloaded?

---

### Post by glitcheddata on 2021-01-19
no i didn't. although i'm not sure how. as i said. i'm very new to this stuff

---

### Post by glitcheddata on 2021-01-19
no, i didn't. although i'm not sure how. as i said. I'm very new to this stuff

---

### Post by grahammechanical on 2021-01-19
From an internet search I see that this problem has been around for a few years. I would post a link to other forums where this question was asked but they do not seem to provide a clear answer.

Some claim that getting the latest version of Rufus & UNetBootin solved the matter. Others claimed that burning the ISO image on a different PC fixed it. One person suggested burning the ISO to CD/DVD and then burning it to USB and copying certain files from the CD/DVD version to the USB version. Some suggested installing an older version of the Linux distribution as that worked and then upgrading to the newer version. Installing Ubuntu 14.04 or 16.04 and then working your way forward does not seem to me to be the answer for today.

These replies are old, but then Windows 7 is also old. Perhaps the Windows utilities that you are using on Windows 7 are in need of an upgrade to newer versions. What version of Ubuntu do you wish to install?

Regards

---

### Post by glitcheddata on 2021-01-19
Thanks for your reply. I am using a Windows 10 laptop to flash the files. I am trying to install Ubuntu 20.04.1 LTS(Focal Fossa)

---

### Post by yancek on 2021-01-19
I'd definitely start with verifying the download because if it was bad, nothing with any software can overcome that.  Go to the Ubuntu download site below and click on verify your download on that page.

[https://ubuntu.com/download/desktop/thank-you?version=20.04.1&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=20.04.1&architecture=amd64)

---

### Post by glitcheddata on 2021-01-19
I verified the download and it said it was valid. What now?

---

