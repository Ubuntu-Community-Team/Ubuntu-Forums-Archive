---
title: "I've successfully installed Ubuntu 13.10 onto my SSD and would like to dual boot"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by malcolm3 on 2013-10-22
I recently bought an SSD to pair with Ubuntu 13.10. My Windows 7 OS is located on my old HDD and i've got them both running seperates without any link. Could you guys help me out? I want to be prompted on which operating system to enter? How would I do that?

---

### Post by conconbay on 2013-10-22
What size SSD are you using?

---

### Post by sudodus on 2013-10-22
Can you boot from Ubuntu, when the Windows 7 HDD is connected? And are both installations either conventional BIOS or UEFI? In that case it should be fairly easy.

- If BIOS, boot Ubuntu and run

```
 sudo update-grub
```

which should create an entry for Windows in the grub menu.

- If UEFI, download Boot-Repair and boot from it, and let it create a boot system for you.

But if Windows 7 is installed with UEFI, you need to install Ubuntu 64-bit with UEFI, and use Boot-Repair to fix the boot system.

---

