---
title: "Ubuntu 18.04 LTS / Windows 10 dual boot: eMMC shows up as SD card"
date: 2019-09-07
forum: New to Ubuntu
---

### Post by hypofalex on 2019-09-07
Hi everyone!

Today I dual booted Ubuntu 18.04 LTS with Windows 10 on my laptop. During the install I chose the option to install Ubuntu alongside Windows. However, my main storage (a 128 GB eMMC) is mislabelled as a SD card in Ubuntu. I've attached a screen shot of the "Disks" window. The 97 GB NTFS partition called "OS" is for Windows and the 26 GB Ext4 partition is for Ubuntu. 

What can I do about this? I'd be very grateful for any help!

---

### Post by cruzer001 on 2019-09-07
It needs t be free space and not ext4, then the installer will see it as usable.

---

### Post by hypofalex on 2019-09-07
I've already installed Ubuntu, so the problem is not the installer. The ext4 partition was created during the Ubuntu install. The problem is that the eMMC storage shows up as a SD card.

---

### Post by CatKiller on 2019-09-07
eMMC (embedded Multi-Media Card) is pretty similar to SD (Secure Digital) cards. They were developed by the same people for the same purposes out of the same stuff. It's not particularly surprising to see one identified as the other. Nothing bad is going to happen as a result of it, except the wrong icon.

---

### Post by hypofalex on 2019-09-07
I see! The thing that worries me a bit is that SD cards are removable while the eMMC isn't. The windows partition shows up as a SD card with the option to unmount it, but I haven't dared to try it as I thought strange things might happen. I guess I'll just make sure not to unmount it by accident, haha?

---

### Post by CatKiller on 2019-09-07
Hotswap is possible with hard drives, too.

Unmounting your Windows partition wouldn't be an issue; it should wait until all the writes have finished before it unmounts. Unmounting your / partition, should it not simply refuse to do so, would likely mean that you'd need to reboot your computer.

It's all just flash chips, not much different to an SSD.

---

### Post by hypofalex on 2019-09-07
Okay, thank you for your help!

---

