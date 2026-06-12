---
title: "Problems deleting files from mount bind directories"
date: 2011-11-08
forum: New to Ubuntu
---

### Post by geminigirl3000 on 2011-11-08
I'm working on setting up my new dual-boot Linux/Windows 7 system (though I would happily part with Windows, I have too much software that only works on Windows). So, I have a Windows OS partition, Linux OS partition (Onieric), and file partition that's supposed to be shared. To make file access easier, I wanted to mount my Documents folder into /home/user/Documents, Music folder into /home/user/Music, etc. This is my /etc/fstab dump:

proc   /proc   proc  nodev,noexec,nosuid    0
UUID=4d7255fe-5ad1-4a62-b168-097184c64f25       /               ext4  errors=remount-ro    0
UUID=629d7271-57e1-4dde-ba19-7217c3914b59     none          swap  sw    0
UUID=D691-6189                     /mnt/share       vfat uid=1000,owner,umask=007,gid=1000,users,dmask=007,user,fmask=007  0
/mnt/share/Documents            /home/ellen/Documents  none  bind   0
/mnt/share/Music/iTunes/iTunes\040Media/Music     /home/ellen/Music     none     bind   0
/mnt/share/Pictures       /home/ellen/Pictures   none  bind   0
/mnt/share/Music/iTunes/iTunes\040Media/TV\040Shows  /home/ellen/Videos  none bind 0

So far, so good. All the files show up in the right place. But when I try to delete...weird things start happening. If I go in in Nautilus through home/user/Documents and delete a file, it goes into /home/user/.Trash-1000/files but doesn't show up in Nautilus trash. If I manually delete from there, it disappears for a second, and immediately reappears as filename.2...so on and so forth, renaming itself but never being deleted. But if I just go into mnt/share/Documents and delete, it goes into /mnt/share/.Trash-1000, shows up in Nautilus trash, and can be deleted with the "Empty Trash" button with no complaint at all. But they're *physically* the same folder! Have I missed something here? Am I mounting wrong? Is there a better way? I'm open to any and all suggestions, so please help!

---

### Post by geminigirl3000 on 2011-11-09
Update: I don't know what I was doing wrong the first time, but it seems the same effect can be produced by deleting the home folders and then creating symbolic links to the corresponding folders on the mounted partition. So now it works!

---

