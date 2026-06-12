---
title: "Ubuntu 17.04, Mounted Drives, Samba Share, Need to CRUD from Windows machines"
date: 2017-05-24
forum: Programming Talk
---

### Post by tim76 on 2017-05-24
I've been trying to get a few things working on my Ubuntu desktop server for quite some time now and after reading quite a few threads, trying out multiple solutions, I figured it's time I ask the community. 

**Background**
I've got an old desktop that I've installed 16.10 *(but recently updated to 17.04) *on and use it as my media server and local dev machine. I then have a Windows 10 machine that I use to map drives to it and then edit code via my IDE's and run various CLI tools and other things required. 

**The problem**
The issue I run into is when I install packages via *[FONT=courier new]node/bower/git[/FONT]*, or create any files on the Ubuntu machine via the CLI, those files/folders are not editable from my Windows machine and I need to run a [FONT=courier new]*sudo chmod 0777 -R locationfolder/*[/FONT]

This is not something I want to continue to do and I would like to be able to seamlessly add/edit/delete/move files on either machines and not have to run into [FONT=courier new]*chown*[/FONT] or [FONT=courier new]*chmod *[/FONT]issues - and preferably not [FONT=courier new]*777 *[/FONT]everything and to have to continue to run this when new files are pulled/added. 

**What I can and have done**
 
[LIST]
[*]I do have the drives being mounted on the Ubuntu at startup, and they are being mounted as my local user **sga**.
[*]I then do also have those mounted locations shareable in my [FONT=courier new]*smb.conf*[/FONT] file and
[*]I can access those from my Windows machine.
[*]I can then also map those drives to a lettered drive in Windows and be happy days
[*]When I add new files in windows, they are added as my local ubuntu user **sga**
[/LIST]

Hopefully this is enough background and describes the issue enough, but if not please ask and I will update accordingly. I have also added the necessary conf files below so you can checkout if I may have miss configured anything. 

**fstab**
    ```
#Entry for /dev/sda1 :
    UUID=924b3a00-6bb1-4b7a-bcb1-c13efb84df49 / ext4 errors=remount-ro 0 1
    #Entry for /dev/sdd2 :
    UUID=88529CC1529CB582   /home/sga/media/Movies  ntfs-3g auto,users,uid=1000,gid=1000,umask=000,utf8    0       0
    #Entry for /dev/sdc2 : 
    UUID=F046FE3746FDFE62  /home/sga/media/TV-Series        ntfs-3g auto,users,uid=1000,gid=1000,umask=000,utf8     0       0
    #Entry for /dev/sdb2 :
    UUID=60EAEC94EAEC67AC   /home/sga/media/TV-Series-Cont  ntfs-3g auto,users,uid=1000,gid=1000,umask=000,utf8    0       0
    #Entry for /dev/sda5 :::
    UUID=36881df5-86a1-4d0a-9422-a1221eea332d       none    swap    sw      0       0
```
*Please note that my www folder is not here, but as soon as I solve a different issue with an MBR on a separate drive, I will add it here. 

**smb.conf**
    ```
[global]
      workgroup = SGC
      usershare allow guests = yes

    [Public Server]
      path = /home/sga/Public/www
      browseable = yes
      guest ok = yes
      read only = no
      create mask = 777
      public = yes
      writeable = yes

    [Movies]
      path = /home/sga/media/Movies
      browseable = yes
      guest ok = yes
      read only = no
      create mask = 777
      public = yes
      writeable = yes

    [TV Series]
      path = /home/sga/media/TV-Series
      browseable = yes
      guest ok = yes
      read only = no
      create mask = 777
      public = yes
      writeable = yes

    [TV Series Cont]
      path = /home/sga/media/TV-Series-Cont
      browseable = yes
      guest ok = yes
      read only = no
      create mask = 777
      public = yes
      writeable = yes

```
*Please note, I've only added the items I have customised in [FONT=courier new]*smb.conf*[/FONT] - Everything else I have kept default.
**Also good to note that my [FONT=courier new]*Public Server*[/FONT] resides on my root drive that Ubuntu is installed on with the other shares are mounted drives. 

Ok, I hope this covers it and I hope someone is able to help... would really love to edit freely on my machines and not have to run the [FONT=courier new]*chmod *[/FONT]commands often. 

Thanks in advanced!

---

