---
title: "Dual Boot XP &amp; Ubuntu 10.04 (Ubuntu Installed First)"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by SEECo on 2012-08-12
Hi Guys, I have Ubuntu 10.04 install on my Laptop now I want to install XP on and have dual boot. Can anyone tell me what will be the best way to install XP and not losing Ubuntu. Thanks in advance.

---

### Post by GreatDanton on 2012-08-12
Shrink Ubuntu partition with Gparted (make sure you have backups and enough free space on the hard disk, otherwise you will lost your data), and don't format the partition you have created. Windows installer will take care of it (proper format etc.). Make sure you have live cd/ USB since you will have to repair Grub. After Windows installation boot with your live cd/usb and install boot-repair. Run boot repair and hopefully it will repair your Grub menu.

Regards.

---

### Post by TheFu on 2012-08-12
> **SEECo said:**
> Hi Guys, I have Ubuntu 10.04 install on my Laptop now I want to install XP on and have dual boot. Can anyone tell me what will be the best way to install XP and not losing Ubuntu. Thanks in advance.

Before you begin, create a raw-metal backup AND test it.  WinXP will screw with the MBR so booting Ubuntu will be an issue. Expect it.

Not directly related to your question, but you can use this as an opportunity to rearrange your HDD partitions to be more flexible.  There are lots of considerations based on the total HDD size, how much you'll be using XP, whether you want to easily share data between both XP and Ubuntu and possibly other OSes later when booted in each, etc.  Ask if you have any interest.

---

