---
title: "Windows boot menu time out stuck at 0 sec"
date: 2019-02-11
forum: New to Ubuntu
---

### Post by notchandan on 2019-02-11
I am new.
I tried installing ubuntu on C: but forgot that my windows boot menu was stuck at 0sec delay and i cannot change between Windows and ubuntu.... While opening the windows show an error msg.:
https//plus.google.com/103062760077632204232/posts/Qrkj45mNEHQ
Only thing i can do is live boot to ubuntu :(
Please help

---

### Post by oldfred on 2019-02-11
Grub only boots working Windows. And that also means Windows cannot be hibernated. And fast start up in Windows sets the hibernation flag, so grub will not boot Windows.

Are installs UEFI or BIOS?

If UEFI just boot Windows directly from UEFI boot menu.

If BIOS and only one drive, you have to temporarily install Windows boot loader to MBR, fix Windows, then restore grub to MBR. You probably need your Windows repair disk with its repair console to run fixMBR command.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

