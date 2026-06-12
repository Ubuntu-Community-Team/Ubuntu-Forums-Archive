---
title: "Ubuntu via Wubi in XP --- &quot;Ubuntu Folder&quot;"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by czgirb on 2012-05-14
Currently, I'm have Ubuntu 10.04 installed in my XP.
I installed it with Wubi.
In **Ubuntu**, within **host > user** folder, I found **XP My Documents'** folder.
But in **XP**, I unable to found **Ubuntu**'s folder ... Why?
Cos some file which downloaded are needed to be joined with **HJ-Split**.
Please guide me ...
[B]
PS:[/B]
In C drive, I just found:
*** Ubuntu > Boot > Grub & > Install & > Winboot**

---

### Post by jerome1232 on 2012-05-14
XP won't be able to access Ubuntu's files, Windows can't read ext2/3/4 without 3rd party drivers and even then Wubi's use of a virtual disc will further complicate that. I would boot into Ubuntu and copy the files to somewhere under /host, which you can then access in XP normally.

---

### Post by roelforg on 2012-05-14
Simple (simplefied):
Wubi creates a file on the XP partition that is uses as a hd.
Ubuntu can mount NTFS FS and wubi makes it automount to /host.
Result: XP FS can be accessed via /host in ubuntu
But XP doesn't know how to work with ext* fs or how to mount a file anyhow.
Result: No ubuntu access from XP
This results in your "problem".
 
PS. The dir in C: is where wubi stashed ubuntu's root.disk and boot files (the root.disk is that hd-file)
 
I could give you the full technical explanation if you want,
but that's for advanced users/geeks only.

---

### Post by wilee-nilee on 2012-05-14
Ubuntu is a file in XP not a ext partition and is accessible look in the admins computer area I forget exactly where probably where the programs are. search with wubi if needed.

---

### Post by czgirb on 2012-05-14
Thank you very very much for the explanation

---

