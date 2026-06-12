---
title: "Help mounting ntfs partitions and alsa sound configurations"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by Laxman_prodigy on 2012-08-02
Hi.
I installed from minimal Ubuntu netinstall iso. Got openbox up and running and installed other software. But, I can't mount ntfs partitions from my dual booting Windows system. I installed thunar and they all show up by the side of it, but when I click on them, it says unauthorized access. Yes, I have ntfs-3g installed.

Also, I installed alsa-base and alsa-utils, but cannot get command "alsamixer" to run. It says, "No directory and something".

Edit:  Its 12.04.

Any help is greatly appreciated as I am banging my head since two days. 
Thanks.

---

### Post by Laxman_prodigy on 2012-08-02
Any help about getting thunar to open the ntfs partitions would be greatly appreciated. I see them on the left panel, but its always, "cannot mount, not authorized"

Edit: Installing some softwares solved the sound issue. :-D But, this one still remains. :-(

---

### Post by lukeiamyourfather on 2012-08-02
> **Laxman_prodigy said:**
> Any help about getting thunar to open the ntfs partitions would be greatly appreciated. I see them on the left panel, but its always, "cannot mount, not authorized"

Edit: Installing some softwares solved the sound issue. :-D But, this one still remains. :-(

The links shown in the file browser are not the actual mounted disks, just an indication that disks are there that could be mounted. Mounting a disk requires root permission. Some file browsers will facilitate this process by asking for the password and then mounting the disk, other's might not.

To be safe I'd just mount them using fstab or a script so they're always there even before you try to browse to them through a file browser. There's some more information about it on the wiki.

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

