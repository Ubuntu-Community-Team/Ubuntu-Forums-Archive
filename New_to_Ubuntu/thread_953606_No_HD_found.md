---
title: "No HD found"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by mormor on 2008-10-20
Hi there. Due to purchasing a new computer I would like to change the setup on my ubuntu-laptop.

I want to format it completely and install xp + ubuntu in a dual boot enviroment. Problem is, when i start the xp install, it cannot find any HD's. How do I format and make the partition ntfs(dont know if I need to do this.)


(Acer Travelmate 6291)

---

### Post by damis648 on 2008-10-20
It will probably be connected with SATA then,which means the XP installer does not have any drivers. Looks for the SATA drivers from the computer's manufacturer site and download them to a floppy or CD or something. When the installation is just starting and it says "Press F6 to install a third-party SCSI or RAID driver" do that and locate the driver.

---

### Post by philinux on 2008-10-20
> **mormor said:**
> Hi there. Due to purchasing a new computer I would like to change the setup on my ubuntu-laptop.

I want to format it completely and install xp + ubuntu in a dual boot enviroment. Problem is, when i start the xp install, it cannot find any HD's. How do I format and make the partition ntfs(dont know if I need to do this.)


(Acer Travelmate 6291)

Does the laptop function/boot now. Whats on it?

---

### Post by bumanie on 2008-10-20
Usually you can go into bios and disable the settings from automatically recognizing sata drives - once disabled, xp 'sees' that there is a hard drive there.

---

