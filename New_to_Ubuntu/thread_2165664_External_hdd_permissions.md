---
title: "External hdd permissions"
date: 2013-08-05
forum: New to Ubuntu
---

### Post by UncleMonty on 2013-08-05
My external hdd is set in fat32. I am using ubuntu 12.04 LTS. The files are set at read only - possibly because it was detached without properly ejecting it. How can I change the permissions please?

---

### Post by TheFu on 2013-08-05
At mount time, the permissions - owner, group are set. Are you manually mounting or using some GUI tool or do you allow automounting to figure things out?

Is the read-only for your userid or for root?  It could just be that the uid was not specified on the mount command, since FAT32 doesn't actually have any permissions.

---

### Post by Jake Sweeney on 2013-08-11
You could try and use the command ```
gksu nautilus
```. It displays the Nautilus file browser GUI with sudo permissions, which usually emable you to bypass any file system permissions

---

### Post by squakie on 2013-08-13
If you have done nothing manually - like using the mount statement in a terminal window or editing the /etc/fstab file, then your drive is being mounted automatically as owned by root (all file systems are unless you do something special) with any other users having read-only access.

You are going to need to do the following:

- a new folder to mount the file system on the external drive to, say perhaps /home/myextdisk  [COLOR=#b22222]EDIT:  you can do this by opening a terminal window and typing sudo mkdir /home/myextdisk[/COLOR]

- change permissions on that folder to allow group read/write and world read/write via opening a terminal and typing sudo chmod 766 /home/myextdisk

- find the uuid of the disk via opening a terminal window and typing sudo blkid

- back up current file system table via opening a terminal and typing sudo cp /etc/fstab /etc/fstab-orig

- edit the file system table (fstab) via opening a terminal and typing gksudo gedit /etc/fstab and then adding a line to the end of the file in the following syntax:

UUID=<the uuid from your disk goes here> /home/myextdisk <file system type> defaults 0 0

so it would look something like this:

UUID=12345abcdef /home/myextdisk ntfs defaults 0 0

(if you are using ntfs on the external disk - if ext4 you'd put ext4 in place of ntfs, etc.)

then save the file and exit the editor

- plug the external drive in and reboot

- open a terminal window and check to be sure the files on the external disk shows via typing ls -al /home/myextdisk

In this way the disk (actually the file system on the disk) will always be mounted to the same place and the permissions will allow everyone to read and write to the disk (in my case only root can execute anything on the disk).

Someone here can probably walk you through the specifics for your case, step by step as easy as you need in order to get this working for you.

Best of luck!

ADDITION:  using UUID instead of the /dev/sdxx format here for a good reason:  if you have any other devices, such as flash drives, and plug one (or more) and then plug the external drive in the /dev/sdxx will be in flux and not something static like "/dev/sdb1".  The UUID is unique to each drive and doesn't change so you use it on the mount statement and never have to worry about some other device picking the /dev/sdxx name.

---

