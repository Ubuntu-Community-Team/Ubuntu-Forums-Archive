---
title: "Cannot access root folder (wubi)"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by Lexwebb on 2012-02-21
I recently installed ubuntu 11.10 through wubi, and I am trying to access my windows files and such. I know I can find these in the disk/root directory. However, whenever I try to access this folder, i get the error message: This folder cannot be displayed: you do not have the permissions necessary to view the contents of 'root'.

Does anyone know what I can do to solve this problem?

---

### Post by yetiman64 on 2012-02-21
> **Lexwebb said:**
> I recently installed ubuntu 11.10 through wubi, and I am trying to access my windows files and such. I know I can find these in the disk/root directory. However, whenever I try to access this folder, i get the error message: This folder cannot be displayed: you do not have the permissions necessary to view the contents of 'root'.

Does anyone know what I can do to solve this problem?
For your Windows files look for a folder called /host in the filesystem, they are in there.[[COLOR=Blue] --info link-- (look at section 8 subsection 13)[/COLOR]]("https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F") **Edit2:** This is just for the main Windows "C:\" drive, all other windows partitions will be mounted directly under /media (for nautilus: Places > Removable media)

**Edit:** **caution:** /root is a system folder you really shouldn't mess with unless you know fully what you are doing.

---

