---
title: "Trying to add other partition to /etc/fstab: &quot;Read-only file system&quot;"
date: 2023-03-29
forum: New to Ubuntu
---

### Post by antonio-cpr on 2023-03-29
Hi!
I installed the last version of Lubuntu and I have a HD with a backup partition. I tried to add manually this partition to "/etc/fstab" with the following lines:
```
sudo mkdir /media/backup
id -u antonio
1000
sudo nano /etc/fstab
```
I added the following line at the end of the file:
```
UUID=7C026AC2026A80CE /media/backup ntfs rw,nosuid,nodev,user_id=1000,group_id=1000,allow_other,blksize=4096 0 0
```

After that I created links to the folders in ~/
```
ln -s /media/backup/softwares/ ~/
ln -s /media/backup/ ~/
ln -s /media/backup/texts ~/
ln -s /media/backup/videos/ ~/
ln -s /media/backup/programming/ ~/
ln -s /media/backup/music/ ~/
ln -s /media/backup/pictures/ ~/
ln -s /media/backup/downloads/ ~/
ln -s /media/backup/torrents/ ~/
```

The problem is when I try to create a file in one of these folders.
```
touch softwares/test.txt
touch: cannot touch 'softwares/test.txt': Read-only file system
```

And when I try to edit a file like "text/test.txt" using any text editor, like Sublime Text or FeatherPad it asks me for authentication.
How can I fix this? I just want to create, delete, edit files, in other words use the files of this partition normally.

```

lsb_release -a:
No LSB modules are available.                                                                                                                          
Distributor ID: Ubuntu                                                                                                                                 
Description:    Ubuntu 22.04.2 LTS                                                                                                                     
Release:        22.04                                                                                                                                  
Codename:       jammy
```

---

### Post by yancek on 2023-03-29
Any directory under /media would be root owned unless the user changes the ownership to that user.  Did you do that?
I also notice that you are using only Lubuntu, a Linux system (at least you mention no other OS) but the backup partition is on an ntfs filesystem.  Are you using this drive as a backup for some windows install also?

Do you get this failure with all files in all sub-directories under /media/backup?
If you have windows and use it also, is hibernation turned off?

Linux permissions don't mean anything on windows filesystems and fmask, dmask or umask need to be used.  See the link below which gives an example of an fstab entry for this. 

[https://askubuntu.com/questions/1241485/mount-a-ntfs-windows-harddrive-permanently-at-startup](https://askubuntu.com/questions/1241485/mount-a-ntfs-windows-harddrive-permanently-at-startup)

---

### Post by antonio-cpr on 2023-03-29
> **yancek said:**
> Any directory under /media would be root owned unless the user changes the ownership to that user.  Did you do that?
I also notice that you are using only Lubuntu, a Linux system (at least you mention no other OS) but the backup partition is on an ntfs filesystem.  Are you using this drive as a backup for some windows install also?

Do you get this failure with all files in all sub-directories under /media/backup?
If you have windows and use it also, is hibernation turned off?

Linux permissions don't mean anything on windows filesystems and fmask, dmask or umask need to be used.  See the link below which gives an example of an fstab entry for this. 

[https://askubuntu.com/questions/1241485/mount-a-ntfs-windows-harddrive-permanently-at-startup](https://askubuntu.com/questions/1241485/mount-a-ntfs-windows-harddrive-permanently-at-startup)


 > Did you do that?
No I did not. All I did I posted here.

> Are you using this drive as a backup for some windows install also? 
Yes, I have installed in the same hard drive Windows 10(dual boot) but the partition I want to mount is just for backup.

> Do you get this failure with all files in all sub-directories under /media/backup?
Yes.

> If you have windows and use it also, is hibernation turned off?
I use Windows 10 in dual boot mode. Do I need to do that?

---

### Post by yancek on 2023-03-30
If hibernation is on in windows, your Linux system will not mount the ntfs partition and will report it as being in an unsafe state.  This is due to the high likelihood of data loss.  Try turning it off in windows.  If this resolves the problem, remember that windows on some updates will turn it back on.  You will not be asked if you want this nor will you be informed that it has been turned on again.

Did you check the link I posted earlier for a proper rw fstab entry for windows?

---

### Post by antonio-cpr on 2023-03-30
> **yancek said:**
> If hibernation is on in windows, your Linux system will not mount the ntfs partition and will report it as being in an unsafe state.  This is due to the high likelihood of data loss.  Try turning it off in windows.  If this resolves the problem, remember that windows on some updates will turn it back on.  You will not be asked if you want this nor will you be informed that it has been turned on again.

Did you check the link I posted earlier for a proper rw fstab entry for windows?

I typed the command bellow in Windows and now everything is working fine.
```
powercfg.exe /hibernate off
``` 

Thanks a lot!

---

### Post by ActionParsnip on 2023-03-31
Your symlinks are bad, you need to specify the link file, specifying "~/" links to the home folder itself, not make a new link file. So the code would be:
```

ln -s /media/backup/softwares/ ~/softwares
ln -s /media/backup/ ~/backup
ln -s /media/backup/texts ~/texts
ln -s /media/backup/videos/ ~/videos
ln -s /media/backup/programming/ ~/programming
ln -s /media/backup/music/ ~/music
ln -s /media/backup/pictures/ ~/pictures
ln -s /media/backup/downloads/ ~/downloads
ln -s /media/backup/torrents/ ~/torrents

```

Personally I'd just symlink the backup folder to ~/backup and be done. This would be one command
```

ln -s /media/backup ~/backup

```

I'm assuming you are using the right case. Linux is VERY case sensitive

---

