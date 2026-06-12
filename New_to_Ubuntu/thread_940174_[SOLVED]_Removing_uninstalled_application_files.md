---
title: "[SOLVED] Removing uninstalled application files"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by gettinoriginal on 2008-10-06
I have searched, but can find no solution for this.  I am having problems with firefox 3.03 being extremely slow (1 minute) to load pages.  So I installed opera, but find it totally unusable in Unbuntu 8.04.  I uninstalled it in synaptic, but doing a file search shows 9 files left behind.  I have run auto clean, rm, etc in terminal, all to no affect.  These seem to be root only access, and no matter what I do, I cannot achieve root access to delete them.  Help please.

---

### Post by philinux on 2008-10-06
sudo apt-get autoremove

---

### Post by gettinoriginal on 2008-10-06
I have tried that, no help.  My problem is, how do I achieve root status while in search mode to have access to these files ??

---

### Post by bwang on 2008-10-06
If you want to run nautilus as root:
```
gksudo nautilus
```
Exactly what files are left behind? Its not a good idea to delete stuff as root unless you really know what you are doing.

---

### Post by hotrod6657 on 2008-10-06
... I'm slow ...

thanks bwang :D

---

### Post by gettinoriginal on 2008-10-07
nothing major, I just don't understand why they are there after removing opera, purging orphan files, autoremove, etc.

[ATTACH]87603[/ATTACH]

---

### Post by Flimm on 2008-10-07
You'll want to delete ~/.opera as well.

---

### Post by gettinoriginal on 2008-10-08
Response is:
Cannot delete .opera directory or file does not exist.

---

