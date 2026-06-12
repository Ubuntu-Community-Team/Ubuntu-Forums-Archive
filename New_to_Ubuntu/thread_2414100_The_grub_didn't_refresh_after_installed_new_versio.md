---
title: "The grub didn't refresh after installed new version Ubuntu 18.04LTS"
date: 2019-03-05
forum: New to Ubuntu
---

### Post by sed_faster on 2019-03-05
Hello folks,

I am trying install ubuntu 18.04 LTS in parallel with Lubuntu 18.04 LTS. The Lubuntu it is in sda and the new version of Ubuntu installed in sdb.
The message error is:

Message1: [https://snag.gy/M7fr9R.jpg](https://snag.gy/M7fr9R.jpg)
Message2: [https://snag.gy/DxYPXf.jpg](https://snag.gy/DxYPXf.jpg)

As presupposed the grub didn't refresh:

Message1: [https://snag.gy/G3hb0s.jpg](https://snag.gy/G3hb0s.jpg)
Message2: [https://snag.gy/v4dN0g.jpg](https://snag.gy/v4dN0g.jpg)

What should I do?
I can access sdb partition through system on sda (Lubuntu). I should edit grub file through terminal in sdb partition (Ubuntu new version)?

Thanks

---

### Post by oldfred on 2019-03-05
Normally with gpt you use UEFI and must  have an ESP - efi system partition.
But if you are using gpt with old BIOS boot you must have a bios_grub partition on the gpt drive in the first 2TiB for grub to correctly install to gpt's protective MBR.
How you boot install media UEFI or BIOS is then how it installs.
Windows only boots in UEFI mode from gpt partitioned drives and only in BIOS mode from MBR(msdos) drives.
Ubuntu is more flexible but should be in same boot mode as Windows. 

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

