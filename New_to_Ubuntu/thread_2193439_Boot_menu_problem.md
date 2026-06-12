---
title: "Boot menu problem"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by jamseal32 on 2013-12-12
Hi,
     I have Win7/Ubuntu dual booted but somehow I wound up with two boot menus.  The grub menu first and the Windows Boot Manager menu second.  I would like to know how to keep just the grub menu.  It is Ubuntu 13.10.  And if it's possible to add "burg"?;)

---

### Post by fantab on 2013-12-12
I don't think 'BURG' is in active development.

In your UEFI-BIOS menu choose to boot Ubuntu only. And you'll get only Grub menu.

---

### Post by jamseal32 on 2013-12-13
Hi fantab,
     How do i get to the UEFI-BIOS menu?  Went to UEFI in boot set-up menu and nothing happens.   When the grub menu comes up and i boot into win7 it goes to windows boot manager with two entries (1)Win7 and (2) Unetbootin  and how that ever got there i have no idea.   But if i boot into Ubuntu in the grub menu it goes right into Ubuntu bypassing the WBM.  Just want to get rid of the Windows boot manager all together or at least hide it.  It has never come up before.  Alway booted staight into windows without it.

---

### Post by fantab on 2013-12-13
Use [**BOOT-REPAIR**]("https://help.ubuntu.com/community/Boot-Repair") from Ubuntu Live DVD/USB.
Create a '**Bootinfo Summary**' and post the LINK, it wants you to note down, here.

---

### Post by oldfred on 2013-12-13
Boot-Repair can help on Linux or Windows boot.

But it seems like this is a  Windows issue. You can have multiple boot entries in Windows BCD. 
       BCDboot Command-Line Options Windows Vista/7/8 recreates boot files.
[http://technet.microsoft.com/en-GB/library/hh824874.aspx](http://technet.microsoft.com/en-GB/library/hh824874.aspx)


 BCDedit to remove
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu/145605#145605](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu/145605#145605)

---

