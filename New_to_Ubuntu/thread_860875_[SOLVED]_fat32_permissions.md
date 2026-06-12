---
title: "[SOLVED] fat32 permissions"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by 7aboobs on 2008-07-16
ok. ive google it, and tried everything but it just wouldn't work and right now, when i type gksudo gedit /est/fstab, the thing is empty. i dunno why, i did paste something like " LABEL=data /mnt/data vfat users,noauto,gid=100,umask=007 0 0" there coz the 'how to fstab guide' din tell where to paste and i just tried that.

 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=77881&stc=1&d=1216186420[/IMG]

this is how the partition table look like. now, all i want to is, to be able to del and write files on the fat32 partition with full access.

---

### Post by alfalfa31 on 2008-07-16
Is there a reason you chose FAT32 over NTFS?

---

### Post by iaculallad on 2008-07-16
To edit your fstab file: Do the command below on your terminal.

```
gksudo gedit /etc/fstab
```

And to automount your FAT32 partition:

Create the mount point first:

```
sudo mkdir /media/data
```

Then insert the line of text below on your fstab file:

> /dev/sda4 /media/data vfat iocharset=utf8,umask=000 0 0

---

### Post by 7aboobs on 2008-07-16
i don't have any external storage device, and the fat32 is kinda half full, so i don't know where to keep it, and i'm kinda lazy to burn stuff. i've trie chown chmod and that still din work.

---

### Post by alfalfa31 on 2008-07-16
> **7aboobs said:**
> ok. ive google it, and tried everything but it just wouldn't work and right now, when i type gksudo gedit /est/fstab, the thing is empty. i dunno why, i did paste something like " LABEL=data /mnt/data vfat users,noauto,gid=100,umask=007 0 0" there coz the 'how to fstab guide' din tell where to paste and i just tried that.

You need to edit **/etc/fstab**, and you are editing **/est/fstab**.  Big difference...

---

### Post by 7aboobs on 2008-07-16
thanks! worked perfectedly! problem fixed!

---

