---
title: "need help booting windows from grub rescue"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by bogitiman on 2012-06-23
I had an old laptop that I had Ubuntu and MS vista dual booting. Everything worked fine, then the motherboard went and the computer was unusable. I got a new laptop with Windows 7 on it. With the new laptop I set it up to boot via USB first in the bios. I took the old hard dive from the broken computer and hooked it up through USB. This set up works fine, but now when the hard drive is not plugged in I can not boot into Windows 7 from the untouched internal hard drive. It gives Me the grub rescue prompt. I want the laptop to boot into windows 7 again, would appreciate any help thanks

---

### Post by drs305 on 2012-06-23
bogitiman,

Welcome to the Ubuntu Forums!

If the BIOS is looking at the USB drive to boot, you can rewrite the MBR of your Windows drive (most likely sda) so that Windows boots with it's own bootloader if the BIOS is changed to boot sda first.

You can repair the MBR with a Windows CD. You can also do it from within Ubuntu if the Windows files are intact and the sda boot flag still points to the correct Windows partition.

Install an app called *lilo* with the first command, and run the second to point the MBR to your Windows (sda) drive. The commands will ask you to fully configure lilo, but only run these two commands. If you reboot without the USB drive connected BIOS should display the Windows bootloader:
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by bogitiman on 2012-06-24
Sweet that worked, I figured it would be an easy fix. DRS305 thanks for the quick and helpful response.

---

