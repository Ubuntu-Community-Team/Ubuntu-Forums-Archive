---
title: "external hdd for backup"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by men28 on 2008-09-08
I have bought today an 160G IDE hard disk. I have chosen disk with IDE interface because I have an old IDE external HDD disk case and I decided using it for backup purposes.

I inserted the new HDD into the case, connected USB cable to the computer, installed gparted package, formatted the disk as ext3 file system and mounted it.

The problem is that I can copy files to this external usb disk only under the root account in terminal. I can not use simple copy and paste commands. And all this is not very comfortable.

Is it right what I did or there are better solutions?

---

### Post by bumanie on 2008-09-08
For cut and paste you would possibly have more luck with FAT 32, but it has limitations as you are probably aware.

---

### Post by men28 on 2008-09-08
I saw in forums people write that the maximum partition size in FAT32 is 128G and maximum file size is 4G. And I wanted using this hdd in linux only.

May be there are some programs for more comfortable backup? I saw scripts for backup on the internet. May be are there some ideas about permissions?

---

### Post by kansasnoob on 2008-09-08
Look here:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Especially pay attention to the section:

> Using pmount

There is a program called pmount available in the repositories which allows unprivileged users to mount drives as if they were using sudo, even without an entry in /etc/fstab. This is perfect for computers that have users without RootSudo access, like public terminals or thin clients. 

You can either install pmount from synaptic or:

```
sudo apt-get install pmount
```

If this doesn't suit you, you could alternatively try "usbmount" but I've come to prefer "pmount", just don't install both at the same time!

---

### Post by unutbu on 2008-09-08
Perhaps you need to give yourself ownership and permissions:
```

sudo chown -R $USER:$USER /media/disk
sudo chmod -R 755 /media/disk
```
Change /media/disk to the correct mount point for your HDD.

---

### Post by men28 on 2008-09-08
Thank you, kansasnoob. There are a lot of useful information in the your link about USB devices.

Thank you, unutbu. I like this idea about change ownership and permissions on the connected device. I thought about leave original permissions. But I think it will be quite difficult.

---

### Post by The Cog on 2008-09-08
If you're backing up all users files, you need root privileges. I use a script that runs rsync to backup users directories. I use sudo to launch it, and regard that as normal.

---

### Post by Peter Alien on 2011-03-22
I'm using an External HD IDE 80 GB that uses NTFS to backup my files from Ubuntu 10.04 LTS.

Is there any restrictions using NTFS with Ubuntu 10.04?
The File System i'm using with Ubuntu is EXT4 with Journal.


Many thanks.

---

### Post by Ghost_Mazal on 2011-03-22
> **Peter Alien said:**
> I'm using an External HD IDE 80 GB that uses NTFS to backup my files from Ubuntu 10.04 LTS.

Is there any restrictions using NTFS with Ubuntu 10.04?
The File System i'm using with Ubuntu is EXT4 with Journal.


Many thanks.

I have backed up to NTFS external for quite a while and haven't had any issues.

---

### Post by Peter Alien on 2011-03-22
Ok Ghost_Mazal :)

Thank you for the feedback.

---

### Post by vanadium on 2011-03-22
Bad advice throughout, except for unutbu. Why would you advice to use any file system, as long as it is not a linux file system?

Please use ext4. You must only know that in Linux, you do not automatically have permissions to write anywhere (nor has a computer virus).

You first need to change ownerships of the folders where you want to be able to write as a user. To change ownership, you must act as administrator.

An easy graphical way to change ownership is to use nautilus (file management) with root permissions:
- Press Alt+F2
- type "gksudo nautilus" and press the enter key
- A file manager window (nautilus) appears. Navigate to the file/folder where you want to change permissions. Change permissions with Right-click - Properties, Permissions tab. Change "owner" from "root" to your own user name to grant yourself full rights.

---

### Post by Ghost_Mazal on 2011-03-23
I have never needed that with my NTFS external. My backups run three times a day , everyday , with my normal user without any issues. And the upside is in case of disaster I have immediate access to my files on another pc that might be running Windoze.
For that reason I have never seen the need to make my external EXT4.

---

### Post by vanadium on 2011-03-23
Any file system should regularly be checked for errors and consistencies. ntfs can only be checked on a Windows machine (there is ntfsfix, but this is not a true replacement for Windows checking tools). Thus, as long as you also have windows in the house, or ready access to a Windows machine, there is no fundamental objection to use ntfs.

As long as you mainly use linux, and use your data drives with linux, the use of a native linux file system is the superior option. You have a robust, modern, well performing file system that integrates perfectly in the file system. You can arrange permissions and ownerships per directory/file, you can create backups that preserve all file attributes of the originals. Admittedly, ownerships and file permissions are mostly of importance in a multi-user environment. They are less important with your personal user data (docs, pictures, ...), but remain important even in a single user environment if you also want to backup user configuration data, e.g. an email account. 

vfat should never be recommended for hard drives. It is a primitive file system that is very fragile (i.e. easily corrupted) and highly unreliable for large volumes. The main asset of vfat is wide compatibility, which is why it is the file system of preference for small mobile volumes such as USB sticks.

---

### Post by fabricator4 on 2011-03-23
> **Ghost_Mazal said:**
> And the upside is in case of disaster I have immediate access to my files on another pc that might be running Windoze.

If you put the open source driver Ext2 on your Windows machine it will be able to access ext partitions.  This includes ext4 and ext3, since they are backwards compatible with ext2 albeit without journaling.

Using ext4 on your backup drive will help to protect you from FS corruption caused by a power problem or someone unplugging the cable before the data has been written out.

Having said all that, I made the exact same mistake on my own external backup drive.](*,)

Chris.

---

### Post by barbedsaber on 2011-03-23
I use NTFS for my music partition.
It's not a great file system, but I haven't had any actual problems with it so far.
Support from linux has been flawless.

Being able to access your backups from a windows machine may not be a bad thing either (as someone already mentioned)

---

### Post by barbedsaber on 2011-03-23
wow, this thread is older than I thought

---

### Post by vanadium on 2011-03-23
Indeed, you noticed. It was not only bad advice, but also old advice I was bashing at. You see how these things are being picked up again, though.

---

