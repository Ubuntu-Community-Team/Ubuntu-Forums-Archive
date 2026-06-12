---
title: "How would I go about removing Ubuntu W/O losing XP"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by fosbinder on 2013-04-01
I like Ubuntu but dont love it =)

---

### Post by sandyd on 2013-04-01
> **fosbinder said:**
> I like Ubuntu but dont love it =)

Boot into your XP Recovery CD, open a console, and run
```
fixmbr
```
That will restore the windows boot loader. You can then delete the Ubuntu partition from Windows ( Control Panel -> Administrative Tools -> Computer Management -> Disk Manager )

---

### Post by wiired24 on 2013-04-01
Just reinstall Windows XP and overwrite the disk that Ubuntu is stored on i would recommend backing up your data first though for XP before doing a reinstillation.

---

### Post by fosbinder on 2013-04-01
All I have are Install disks

---

### Post by fosbinder on 2013-04-01
i would just really love to not have to go thru all the auto updates and driver reinstallation.. ^Great ways but not Best..Cant be lol.. Thank you =)

---

### Post by sandyd on 2013-04-01
> **fosbinder said:**
> All I have are Install disks

If you have the install disk, you can still run commands - see [http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

1. start the cd
2. press 'r' to boot into recovery
3. run fixmbr to restore windows xp bootloader

---

### Post by fosbinder on 2013-04-01
so I ran FIXMBR and deleted the 2 non windows devices.. is that it?

---

### Post by sandyd on 2013-04-02
yep

---

