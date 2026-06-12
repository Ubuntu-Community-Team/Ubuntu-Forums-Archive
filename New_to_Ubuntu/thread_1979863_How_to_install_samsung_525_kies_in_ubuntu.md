---
title: "How to install samsung 525 kies in ubuntu"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by vutuntu on 2012-05-14
hello all,

i have samsung 525 mobile. i tried to install samsung kies .exe in wine but could not do successfully.
Is there any trick (or application) that i connect my mobile with ubuntu and could synchronize files.

---

### Post by Lisiano on 2012-05-14
Wine can _not_ provide a way for Windows applications to talk to USB devices. There is no way to make Kies run in Wine. You can always just connect the phone as Mass Storage to copy files, there was some software to import/export contacts but I do not remember the name nor am I at my own PC. Try looking in Ubuntu Software Center for anything mentioning Samsung.

If you _must_ use Kies, then you have to install a Virtual Machine and install Windows on it, then you can connect your phone to the VM and run Kies. Popular VMs are VirtualBox (Free) and VMware (Commercial software),

---

