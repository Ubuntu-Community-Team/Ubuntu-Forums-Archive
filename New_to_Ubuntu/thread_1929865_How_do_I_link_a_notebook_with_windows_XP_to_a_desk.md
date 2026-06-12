---
title: "How do I link a notebook with windows XP to a desktop with Ubuntu 11.10?"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by lfpoli on 2012-02-22
Is there any tutorial about linking a notebook with Windows XP to a desktop with Ubuntu 11.10?

The main objective is to transfer files to the desktop computer, which is a backup for my notebook files.

I think it can be done AdHoc or through my home network, is that correct? which is the best way to transfer the files?

Thanx!

---

### Post by xumuk37 on 2012-02-22
read something about ftp and samba setup

---

### Post by 3rdalbum on 2012-02-22
Through your home network would be best. You will want to use Samba to create a network share on the Ubuntu computer that the Windows computer will be able to see.

In the Ubuntu terminal, run

gksudo shares-admin

Input your password when prompted. It will also tell you that you need to install Samba or NFS - just install Samba. Then you can easily set up the shared folder, it is pretty self-explanitory from this point.

---

