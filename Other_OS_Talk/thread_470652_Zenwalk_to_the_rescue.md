---
title: "Zenwalk to the rescue"
date: 2007-06-11
forum: Other OS Talk
---

### Post by LaRoza on 2007-06-11
Hi all. Last week I made a post about installing a distro of Linux on a computer with low RAM, as low as 128 MB. Well, the computer did not have 128 MB, but 64 MB. With that kind of RAM, Windows, which was preinstalled did  not run very well. 

Windows would not recognize newer flash drives, although the computer was physically capable of reading them.

I installed Zenwalk, as no live cd I had would work, and Ubuntu was too large. Zenwalk runs pretty well on the computer. I am surprised a modern operating system would run on 64 MB of RAM while keeping a GUI and modern apps.

---

### Post by ThinkBuntu on 2007-06-11
Cool! Zenwalk's hands-down the best option for low-spec computers.

---

### Post by LaRoza on 2007-06-11
If you didn't recommend it, I would be stuck, thanks. How easy is it to dual boot it with Feisty? Do I just make a partition and install it there and then install Lilo? Will Ubuntu boot?

---

### Post by ThinkBuntu on 2007-06-11
> **LaRoza said:**
> If you didn't recommend it, I would be stuck, thanks. How easy is it to dual boot it with Feisty? Do I just make a partition and install it there and then install Lilo? Will Ubuntu boot?

Configuring LILO is different from GRUB, and I only know GRUB. I highly recommend using GRUB as your bootloader for both distros: When you upgrade a kernel, you have to initiate a command to update LILO, or else your next boot won't find the kernel. GRUB has features that update it automatically.

---

### Post by LaRoza on 2007-06-11
Thanks, I liked Zenwalk-live and I would like it installed.

---

### Post by ThinkBuntu on 2007-06-11
> **LaRoza said:**
> Thanks, I liked Zenwalk-live and I would like it installed.
Just tell it to skip the bootloader step. ZW stubbornly keeps LILO because Slack uses LILO, and the Zenwalk way of doing thigns means you only have one option.

---

### Post by LaRoza on 2007-06-11
How would I boot?

If I installed Zenwalk to a partition next to Ubuntu, sda2, I believe it would be called?

---

### Post by ThinkBuntu on 2007-06-11
> **LaRoza said:**
> How would I boot?

If I installed Zenwalk to a partition next to Ubuntu, sda2, I believe it would be called?
GRUB always uses hd* to refer. If Ubuntu's already installed with GRUB, just add ZW to an extra partition and add its entry to your menu.lst. If Zenwalk's installed, Install Ubuntu, preserving yoru old partition, and make sure the MBR is in the Ubuntu partition, which will mean removing it from the ZW one. Again, add the ZW entry to the menu.lst.

---

### Post by LaRoza on 2007-06-11
How would I add it to the menu.lst? What would the entry look like? Thanks for your help.

---

### Post by ThinkBuntu on 2007-06-11
It's clear when you see the entries. They all follow the same logical pattern, and the file has a very long guide included.

---

### Post by LaRoza on 2007-06-11
Thanks :D

---

### Post by energiya on 2007-06-12
> **LaRoza said:**
> Hi all. Last week I made a post about installing a distro of Linux on a computer with low RAM, as low as 128 MB. Well, the computer did not have 128 MB, but 64 MB. With that kind of RAM, Windows, which was preinstalled did  not run very well. 

Windows would not recognize newer flash drives, although the computer was physically capable of reading them.

I installed Zenwalk, as no live cd I had would work, and Ubuntu was too large. Zenwalk runs pretty well on the computer. I am surprised a modern operating system would run on 64 MB of RAM while keeping a GUI and modern apps.

I managed to get it to use about 31-35 MB RAM

---

