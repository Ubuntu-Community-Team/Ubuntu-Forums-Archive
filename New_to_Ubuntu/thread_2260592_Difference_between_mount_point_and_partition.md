---
title: "Difference between mount point and partition ?"
date: 2015-01-13
forum: New to Ubuntu
---

### Post by gardenair on 2015-01-13
Any one guide me the difference between mount point and partition ? I know that partition is a chunk in a Hard Disk where as mount point is a directory ?
Suppose I create a folder i.e"Music" and share it so.If i mount it in fstab what will be its advantage  ?
please guide me.

---

### Post by nerdtron on 2015-01-13
Mounting is different from sharing.
Mounting simply means that you mount/insert/attaches a disk partition onto the filesystem hierarchy. It's a folder you make and you attach the partition to that folder so that the file/folders on that partition will be accessible by the user/operating system.

Sharing a folder to other is a different story. But of course, you need to mount a partition into a folder so that you can access it.

---

### Post by gardenair on 2015-01-13
thanks for the reply. Well it means a folder can not mount only a partition will be mount ? In a simple words we can say that physical media can only be mount like hard disk and USB but a folder can not be mount.Is it correct ?

---

### Post by The Cog on 2015-01-13
You are right that a partition is a "chunk" of a hard disk. 
Each partition can have its own filesystem containing its own set of files.

In windows, each partition would be allocated a different "drive letter", C:, D: etc, despite the fact that they are all different areas of the same physical drive.

In *nix, partitions and remote shares are not shown as separate drives with separate drive letters. Instead, when they are "mounted", they are represented as the contents of a pre-existing directory. Mounting a filesystem into a directory hides its real contents and replaces it with a view of the contents of the newly mounted filesystem. If you have a directory that is expressly intended to be used for showing the contents of a partition or share, then it probably makes sense to leave it empty until the mount is performed. 

These days, using a file manager to open a removable drive will create an empty folder in /media/username and mount the drive into it. The mount point directory will generally be deleted immediately after the drive is unmounted again. 

One thing to watch out for - people sometimes copy files to a folder where they **think **a partition or share is mounted to (but it isn't) and end up copying the files to the wrong place. Even more confusing is that then mounting the intended destination makes the local copies apparently disappear as the real directory contents are replaced with a view of the (empty) removable drive or share.

---

### Post by gardenair on 2015-01-13
thanks  well my objective is to build a samba server where windows users will keep there all files. It will be a common share folder .In this case i can create a folder like "Public" and them mount it ? Definitely there will be a need to add it in fstab as well. what you say about it.
thanks.

---

### Post by The Cog on 2015-01-13
It seems that a folder (or even a single file) can be mounted elsewhere, so that the same content appears in two places in the directory tree. See the bind and rbind options here:
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

I have never felt any need to mount folders elsewhere, but there must be a use or people would not have written the capability into the OS.

---

### Post by nerdtron on 2015-01-13
You can mount another folder of course, especially if it is a samba share or a nfs share.
To imagine it, say you have a hard drive partition and you mount it on your server, then that partition becomes a normal folder on the server, (ex: /mnt/samba)
Now you can create a samba share, by configuring this folder (/mnt/samba) as a samba share, other people on the network can mount it.
If you successfully created a samba share for this folder, other people on the network will "mount" this folder on their computer for them to access it. Once they mount this shared folder, it becomes a normal folder on their computer. (although data of course will be sent on the server when they save anything on that folder.)

---

### Post by The Cog on 2015-01-13
I can't help you with samba shares. But mounting is done when you want to view a remote share. In windows, the client would "map a drive" - making the share appear as a "drive". In linux, the client would "mount" the share into a folder (the mount point) making the share appear as folder contents.

---

### Post by Morbius1 on 2015-01-13
>  					thanks  well my objective is to build a samba server where windows  users will keep there all files. It will be a common share folder .In  this case i can create a folder like "Public" and them mount it ?  Definitely there will be a need to add it in fstab as well. what you say  about it.
Now I'm confused.

Does this Public folder reside on a partition you are already mounting in fstab?

If so then the samba server simply defines the share parameter of the Public folder.
If not it would be best to mount the partition then define the share parameters of the Public folder within that mounted partition.

---

