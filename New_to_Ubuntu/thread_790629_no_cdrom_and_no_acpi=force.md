---
title: "no cdrom and no acpi=force"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by frustated8.04 on 2008-05-11
Im totally a windows guy and Im experimenting with ubuntu I install 8.04 on a machine by removing hard drive and istalling it into another because the it would not boot from the cdrom in this pentium 2 Acer machine 350mz any way when i boot the bios reads that **the acpi=force is required**. Iread some of the other forums about the same problems but I wasnt able to successfully complete the task I couldnt make changes It said I didnt have permission
Problem #2 **[B]why doesnt the cdrom wor**k[/B] it doesnt show any information in the properties window and it tells me that there is no media in the drive when I try to right click to view files  where do I go from here?????

---

### Post by frustated8.04 on 2008-05-18
**Im surprised that no one can offer any assistance with these problems Im sure some else has run into this before can anyone help?**

---

### Post by spiderbatdad on 2008-05-18
To have permission to edit /boot/grub/menu.lst use the command sudo with your choice of editor. For example, to edit the file with gedit: ```
gksu gedit /boot/grub/menu.lst
``` Or with nano: ```
sudo nano /boot/grub/menu.lst
```If you are attempting to boot from the grub menu, press F6 and remove --quiet splash from the end of the kernel line and replace with acpi=force

---

### Post by Nosferatu1 on 2008-05-18
> **frustated8.04 said:**
> ...I install 8.04 on a machine by removing hard drive and installing it into another because the it would not boot from the cdrom...
If I understand correctly, you removed the HD from the pentium II computer, installed it in another computer, installed Ubuntu on it, then replaced it into the pentium II computer. Is this correct ?
You should consider that there may be a hardware problem with your cdrom. Replace it with another cdrom & try booting up with the Ubuntu cd.
Are your bios settings correctly set to boot from cdrom _first_?
Did any of spiderbatdad's suggestions resolve the problem?
Please let us know.

---

