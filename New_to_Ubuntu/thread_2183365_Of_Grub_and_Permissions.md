---
title: "Of Grub and Permissions"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Luc_Lacombe on 2013-10-24
Hello  I just installed Ubuntu 12.04 in a new system with Win XP alongside.   Everything is fine, I have access to both system with Grub. OK!   But I want to edit Grub  and for this I found a recipe, using Gedit and terminal.OK.    I have to edit etc/default/grub and adjust some values inside with GEDIT.   I made these changes but I can't save this file because...I don't have permissions.   Ok it's a new install but ...please...I want to have 100% of permissions!!!!!   How can I change this permissions thing to save  my Grub changes.    Luc    PS. I repeat the question is about permissions, not grub!

---

### Post by oldos2er on 2013-10-24
Use ```
gksudo gedit /etc/default/grub
``` You might want to make a backup copy of the file first, something like ```
sudo cp /etc/default/grub /etc/default/grub.backup
```

---

### Post by deadflowr on 2013-10-24
Yep, as stated, use sudo/gksudo(gksu) to elevate your rights.

When you've made the changes run
```
sudo update-grub
```
This will insure that the changes are actually made to the system.

---

### Post by Luc_Lacombe on 2013-10-24
If I understand right I never have full rights unless I use the terminal with SUDO?  luc

---

### Post by Impavidus on 2013-10-25
That's correct. It's for security. Read [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

---

### Post by oldos2er on 2013-10-25
> **Luc_Lacombe said:**
> If I understand right I never have full rights unless I use the terminal with SUDO?  luc

For graphical programs like gedit use [gksudo]("http://www.psychocats.net/ubuntu/graphicalsudo"). For CLI programs **sudo** is appropriate.

---

