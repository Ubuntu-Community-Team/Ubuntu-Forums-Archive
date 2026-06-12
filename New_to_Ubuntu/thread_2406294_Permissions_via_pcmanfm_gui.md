---
title: "Permissions via pcmanfm gui"
date: 2018-11-18
forum: New to Ubuntu
---

### Post by mookie60 on 2018-11-18
Lubuntu 16.04.    
Trying to change folder permissions with pcmanfm, but can't make it work.  Also installed nautilus, but had the same issues.   I know these changes can be made via the terminal, but i'd like to stick with the gui, please.

I have a usb stick.  I format the stick (FAT) using "Disks".  All seems well.  Pull up the device in pcmanfm and create a folder.  I try to change the folder permissions for "anyone" to have read/write access ("make changes"), so i can use the disk in other machines.  It seems to accept the change, there's no error notices - but it doesn't register the permission change - reopen permissions and it's back to the way it was.  

I haven't changed user, the "owner" is my username, but I still can't change permissions.   I tried making the changes to the disk (instead of the folder) in the same way, same problem.   I tried opening pcmanfm as root, but had the same problem with a folder I created as root.  

obviously I don't understand something.  apologies if this isn't the proper topic area.

thanks

---

### Post by angisky on 2018-11-18
All the instructions I find online are for using chmod. I've run into this same issue with other GUI applications in the past. Not sure how to help other than to say you can probably resolve it with chmod. If you want detailed instructions on how to use chmod you can run the command "man chmod" which will give you an entire manual on how to use the command.

---

### Post by TheFu on 2018-11-18
My only advice is not to manage permissions using a GUI and to learn 90% of what chown and chmod and chgrp commands can do.

Running file managers under sudo can cause bad permissions problems, BTW.

---

### Post by mookie60 on 2018-11-19
As I have only a very rare need for the terminal, the syntax just doesn't stick.  What can I say, for the most part Ubuntu "just works".  I suppose one downside has been my reliance on guis.  All I wanted to do was give my wife some videos to watch for her thanksgiving trip.

So I tried:  sudo chmod 777 /media/user/disk/folder    (basically just read the tree as it showed in pcmanfm)

It seemed to accept it, no errors - unfortunately, still can't copy anything to the folder, or drive - says it's read-only.   I tried different usb sticks: sandisk, pny, no-name.  It's all the same.   My habit of running the file manager under sudo may well have given me the "bad permission problems" TheFu mentioned.   At least creating/using folders on the HD hasn't been an issue . . . damn it, why did I say that.

I'll investigate some of the chmod options, but really, times up - my wife is off tomorrow, very early.   Most likely I'll rely on my friend, an IBM linux guy.  He's on a trip and will be back in a couple days.

Thanks all, and have plenty of turkey

---

### Post by TheFu on 2018-11-19
If the file system isn't Linux-based, chmod won't work.  
If it is NTFS or FAT32, the permissions have to be setup at mount time.
Something like:
```
sudo mount -t vfat -o uid=$UID,gid=$GID LABEL=$LABEL3 /mnt/$LABEL3
so
sudo mount -t vfat -o uid=1003,gid=1003 LABEL=60G /mnt/60G

```
Your values will be different, almost certainly.  I like to use the partition label for the USB flash partition to mount things temporarily.

All the variables must be set or replaced with the correct values.  And the mount point (empty directory), needs to already exist.

---

### Post by cmcanulty on 2018-11-19
See this article

[https://askubuntu.com/questions/118199/how-do-i-change-file-permissions-on-a-fat32-drive]("https://askubuntu.com/questions/118199/how-do-i-change-file-permissions-on-a-fat32-drive")

---

### Post by mookie60 on 2018-11-20
Ah!  Never considered things being different in different files systems.  

Thanks you

---

### Post by TheFu on 2018-11-20
> **mookie60 said:**
> Ah!  Never considered things being different in different files systems.  

Thanks you

File systems are designed for different specific purposes, making trade-offs in each implementation.  There are probably 50 file systems that are popular today, each trying to be great for the things the designer wants while minimizing the down sides.  Most people running Windows never consider file systems, since there are basically 3 for them:
* NTFS
* FAT32
* exFAT

But really there are multiple versions of NTFS, FAT16, FAT32, exFAT.

Off the top of my head, Linux has a few file systems:
* ext2
* ext3
* ext4
* jfs
* xfs
* zfs
* reiserfs
* btrfs
and those are without looking anything up.  Wikipedia has a long list of file systems. [https://en.wikipedia.org/wiki/File_system](https://en.wikipedia.org/wiki/File_system) has more info than most people want to know.  [https://en.wikipedia.org/wiki/List_of_file_systems#File_systems_optimized_for_flash_memory.2C_solid_state_media](https://en.wikipedia.org/wiki/List_of_file_systems#File_systems_optimized_for_flash_memory.2C_solid_state_media)

For optimized flash storage use, Linux has a few file systems [https://en.wikipedia.org/wiki/Flash_file_system](https://en.wikipedia.org/wiki/Flash_file_system) created by different project teams and companies.  But alas, MSFT has so much market power that all the others are ignored by 3rd party devices like camera makers, video cameras, and playback devices for the inferior FAT32 or exFAT.

---

### Post by cmcanulty on 2018-11-20
This probably isn't the case but some USB sticks have a physical switch that can be set to lock. Often it isn't that  visible either.

---

