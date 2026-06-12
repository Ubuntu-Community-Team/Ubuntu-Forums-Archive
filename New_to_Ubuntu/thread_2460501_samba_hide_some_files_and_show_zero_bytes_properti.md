---
title: "samba hide some files and show zero bytes properties"
date: 2021-04-12
forum: New to Ubuntu
---

### Post by Anime4000 on 2021-04-12
I run clean Ubuntu install, samba usershare somewhat unable to list files:
1. Some folder missing
2. Some file are missing
3. Cannot copy file to Windows
4. Large file cannot copy into samba (New SSD, Not broken)
5. File become folder

[ATTACH=CONFIG]288291[/ATTACH]

been a week to solve samba issue, I dont know what happen,

without using usershare, same problem:
```

[DATA]
    comment = Global Sharing
    path = /mnt/sde1/DATA
    read only = no
    guest ok = no
    browsable = yes
    writable = yes
    create mask = 0644
    directory mask = 0755
    force user = anime4000

```

```

anime4000@HITOHA-VM:~$ samba --version
Version 4.11.6-Ubuntu

```

anyone know why???

---

### Post by Morbius1 on 2021-04-12
I cannot explain all those symptoms but the "file becomes folder" problem may be due to a change Samba made a few versions ago. See if this resolves anything:
[https://askubuntu.com/questions/1328978/ubuntu-samba-copied-files-inaccessible](https://askubuntu.com/questions/1328978/ubuntu-samba-copied-files-inaccessible)

---

### Post by Anime4000 on 2021-04-12
OMG, this works with existing file & folder (NTFS Disk > SSD: sdb1, sdc1, sdd1 & HDD: sde1)
```

store dos attributes = no

```
I can access these file now, I wonder why that not default inside smb.conf?

I come across [Launchpad Bug #1872476](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1872476) and found [unofficial patch](https://launchpad.net/~linux-schools/+archive/ubuntu/samba4.12)

These patch works but usershare are being disabled, so no quick way to enable/disable share within File Manager.

---

Both are works, I prefer _store dos attributes = no_ looks clean without need patching

---

### Post by ActionParsnip on 2021-04-12
What file system is the share using? Sharing NTFS with Samba is less than fun

---

### Post by Anime4000 on 2021-04-13
I see, NTFS and Samba is bad combination...

here my fstab on Kubuntu
```

# Samsung QVO 1TB SSD: sdb sdc sdd
# Seagate ST1000LM024 HDD: sde
# Managed by gnome-disk-utility 3.36.1
/dev/disk/by-uuid/30591CB40494A64E /mnt/sdb1 auto nosuid,nodev,nofail,x-gvfs-show,uid=1000,gid=sambashare 0 0
/dev/disk/by-uuid/621BFAA802EA7BD6 /mnt/sdc1 auto nosuid,nodev,nofail,x-gvfs-show,uid=1000,gid=sambashare 0 0
/dev/disk/by-uuid/1EE89D3623B41F12 /mnt/sdd1 auto nosuid,nodev,nofail,x-gvfs-show,uid=1000,gid=sambashare 0 0
/dev/disk/by-uuid/19E093BE26F46212 /mnt/sde1 auto nosuid,nodev,nofail,x-gvfs-show,uid=1000,gid=sambashare 0 0

```

Which File System is best for samba beside ext4?

---

### Post by ActionParsnip on 2021-04-13
If you are using Linux, then a Linux file system will give fewer headaches. If you need to move the drive around then NTFS is good but Samba may be problematic. You have to remember that NTFS is a proprietary file system and only Microsoft truely understand it's workings. The NTFS access you enjoy is a best effort attempt by the NTFS-3G
 guys which is awesome but will not match what Microsoft know as Microsoft won't share how their file system works

---

### Post by Morbius1 on 2021-04-13
For the vast number of use cases in a home lan NTFS makes an ideal choice for Samba simply because it's permissions are immutable. Even the share definition becomes easier since all the create mask, directory mask, and the few dozen other parameters become irrelevant. Of course this depends on how complicated a share definition you want to create.

The only way to achieve the same result on a Linux filesystem would be to do a bindfs remount which gives it the same immutable property.

The only argument for not using NTFS would be if the server was Linux only since if something did happen to the partition there would be no safe way to repair it.

---

