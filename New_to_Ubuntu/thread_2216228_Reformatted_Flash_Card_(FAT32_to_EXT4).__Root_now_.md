---
title: "Reformatted Flash Card (FAT32 to EXT4).  Root now owns, how to change?"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by JeQhdMD on 2014-04-10
Hello,

I needed a larger flash card for my ubuntu backups, so I purchased a PNY 32gb card which came with the standard fat32 file system.  As I only use this card with my Ubuntu 13.10 system, I reformatted the card to ext4 using Gparted.  As I attempted to manually copy the first directory from my /home to the flash card, the system advises I don't have write/change permissions.  I checked the card properties in Nautilus and see it is owned by root.   I've heard of a command (chown) to change ownership of files and folders, but I would like to change ownership of the device itself to my user (greg1) so all subsequent added folders will be owned by me.  

Is that do-able and if so, what would be the terminal command to accomplish this?    There are no files or folders yet on flash card (unless they are hidden).

Thanks for your help.

---

### Post by slickymaster on 2014-04-10
```
sudo chown -R $USER:$USER /media/NAME_OF_YOUR_MEDIA
```
```
sudo chmod -R a+rwX,o-w /media/NAME_OF_YOUR_MEDIA
```

Using those two commands you will update not only ownership but also permissions.

Please refer to [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Dennis N on 2014-04-10
> Is that do-able and if so, what would be the terminal command to accomplish this? There are no files or folders yet on flash card (unless they are hidden).

Definitely.

If your card appears as: **/media/x/a** where **x** is your user name, and **a** is either a label or perhaps a UUID, and you have just formatted it, plug in the card, and use the terminal and execute:

**[FONT=Courier New]sudo chown x:x /media/x/a[/FONT]**

**x** will become owner and group of this folder (even if you unplug it and plug it in again later), and give you the owner's permissions, including write*, allowing you to save and modify files in there. You will also be the owner of any additional files (or folders).

*assuming the default permissions rwx for the owner. 

Here is the same situation except with a newly formatted USB drive:

[http://ubuntuforums.org/showthread.php?t=2211159&p=12957049#post12957049](http://ubuntuforums.org/showthread.php?t=2211159&p=12957049#post12957049)

---

### Post by JeQhdMD on 2014-04-10
Upon input of:

sudo chown greg1:greg1 /media/greg1/e95a6909-21ac-4ffb-8f0e-60094bb1c0

the response after password input is:

"chown:  cannot access '/media/greg1/e95a6909-21ac-4ffb-8f0e-60094bb1c0': No such file or directory"

the flash card is device sdb1 - should that be used instead of the long string e95a . . . ?

note:  before input of above, I used gparted to change file type from ext4 to reiserfs(if that makes any difference)

---

### Post by JeQhdMD on 2014-04-10
Success at last!   Used the command again as shown (**[FONT=Courier New]sudo chown x:x /media/x/a) and made sure prior to command input to copy device ID from the nautilus file properties tab.  So, for whatever reason, the original copies may have picked up and extra character.   Thanks to each contributor, both replies helped clarify the situation. [/FONT]**

---

