---
title: "[SOLVED] Access shares from a PC (with static IP) in the LAN"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-07-02
Hi folks,

Recently, I switched to Xubuntu on my laptop. I followed the instruction on the forum and was able to use fusesmb to somehow gain access to other PCs in the LAN. However, it seems like only several PCs (with their workgroups are either "MSHOME" or "WORKGROUP") are shown in the mount point folder (I use ~/Desktop/smb). If they name their workgroup different names then they aren't shown in my ~/Desktop/smb

My question is if I want to access a certain PC with static IP (e.g 192.168.1.100 - with Ubuntu & Nautilus, it's "smb://192.168.1.100") in the same LAN then how do I do that?

(I have samba, smbfs & smbclient installed)

Thanks in advance! :D

---

### Post by iaculallad on 2008-07-02
Create a folder like /home/myshared

```
sudo mkdir /home/myshared
```

And mount the share:

```
sudo mount -t smbfs //192.168.1.100/share_folder_name /home/myshared -o username=your_windows_username,password=your_windows_password,uid=Xubuntu_UserID,gid=Xubuntu_GroupID

```

Username and password, are what you used when accessing 192.168.1.100.
While uid, and gid are your UserID and GroupID at your (x)Ubuntu PC.

---

