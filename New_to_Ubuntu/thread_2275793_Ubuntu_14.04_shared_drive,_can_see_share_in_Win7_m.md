---
title: "Ubuntu 14.04 shared drive, can see share in Win7 machine but can't access"
date: 2015-04-28
forum: New to Ubuntu
---

### Post by kkc on 2015-04-28
We have a local network of Win7 computers and one Ubuntu 14.04 with 4 drives 2-2tb, 2-4tb. I've shared these drives with samba and from a win7 computer I can see the shares but when I try to access I get a "You do not have permission to access" error. I have samba (from gui) set to "allow access to everyone" and under Samba Users I have none listed. I also try to share them with "local network sharing" same error. I want to be able to share them without a password to everyone on our local network. Any help would be appreciated. I'm new to Ubuntu and terminal commands.

---

### Post by bab1 on 2015-04-29
> **kkc said:**
> We have a local network of Win7 computers and one Ubuntu 14.04 with 4 drives 2-2tb, 2-4tb. I've shared these drives with samba and from a win7 computer I can see the shares but when I try to access I get a "You do not have permission to access" error. I have samba (from gui) set to "allow access to everyone" and under Samba Users I have none listed. I also try to share them with "local network sharing" same error. I want to be able to share them without a password to everyone on our local network. Any help would be appreciated. I'm new to Ubuntu and terminal commands.
With Samba (also Windows sharing), you share folders not drives.  Windows calls these shares "drives" but they really are just a folder and all below it.  Where are these folders located in your Ubuntu file system?  Are these shared folders inside of your users /home directory?  How did you do this: "shared these drives ... from a win7 computer"?

---

### Post by Bucky Ball on 2015-04-29
Are the folders you are trying to share on an NTFS partition or a Ubuntu EXT* partition? If the latter, that would probably cause an issue as Win can not natively read/write EXT* filesystem.

---

### Post by bab1 on 2015-04-29
> **Bucky Ball said:**
> Are the folders you are trying to share on an NTFS partition or a Ubuntu EXT* partition? If the latter, that would probably cause an issue as Win can not natively read/write EXT* filesystem.

Maybe, but then again, maybe not.  Let's see what the OP has to say about the shares they have.

Widows machines that are using remotely mounted file systems don't really care it what the "native" file system is on the file server (in this case Samba).  Samba and Windows sharing take care of the translation between EXT and NTFS.  Sometimes imperfectly, but always using SMB.

---

### Post by Bucky Ball on 2015-04-29
> **bab1 said:**
> Maybe, but then again, maybe not.  Let's see what the OP has to say about the shares they have.

That's the intention. ;)

> **bab1 said:**
> Widows machines that are using remotely mounted file systems don't really care it what the "native" file system is on the file server (in this case Samba).  Samba and Windows sharing take care of the translation between EXT and NTFS.  Sometimes imperfectly, but always using SMB.

Hmm, interesting. Learn something everyday. Didn't know that as I don't use and actively avoid using samba (unless I'm attempting to dance or play one). ;)

---

### Post by newb85 on 2015-04-29
What security policy are you using in samba?

---

### Post by kkc on 2015-04-29
The 4 drives I want to share are installed in the Ubuntu 14.04 machine. They are mounted and from the media folder there is a network share option, I tried that and also from Samba at the media folder. Thanks for the help, it is appreciated.

---

### Post by kkc on 2015-04-29
The folders have a Ubuntu EXT partition. We had a file server a few years ago with Ubuntu 10.04 and it seemed to work sharing with Win XP,7 computers and it had a EXT partition. Thanks

---

### Post by kkc on 2015-04-29
> **newb85 said:**
> What security policy are you using in samba?

Whatever the default is, from the GUI under the security tab Auth mode:User, Guest Account: No Guest Account, Samba Users: None are listed. For the share, the Allow access to everyone is checked. Thanks

---

### Post by bab1 on 2015-04-29
> **kkc said:**
> The 4 drives I want to share are installed in the Ubuntu 14.04 machine. They are mounted and from the media folder there is a network share option, I tried that and also from Samba at the media folder. Thanks for the help, it is appreciated.
Post the output of this terminal command```
ls -l /media/
```...my guess is the disks are mounted without the proper permissions set because they are formatted NTFS.  This means that the user ***nobody*** has no access rights and you can't give that user access because NTFS does not allow you to change the permissions.  

You have to remount the drive using the permissions appropriate for the user ***nobody*** for Samba sharing to work properly.

---

### Post by bab1 on 2015-04-29
> **kkc said:**
> Whatever the default is, from the GUI under the security tab Auth mode:User, Guest Account: No Guest Account, Samba Users: None are listed. For the share, the Allow access to everyone is checked. Thanks
If the partitions are formatted NTFS then you can't change the permissions this way.

---

### Post by bab1 on 2015-04-29
> **kkc said:**
> The folders have a Ubuntu EXT partition. We had a file server a few years ago with Ubuntu 10.04 and it seemed to work sharing with Win XP,7 computers and it had a EXT partition. Thanks
Are you sure?  The symptoms sure appear to be that or NTFS formatted partitions. Post the output of this```
sudo blkid -c /dev/null -o list
```

---

### Post by kkc on 2015-04-29
> **bab1 said:**
> Post the output of this terminal command```
ls -l /media/
```...my guess is the disks are mounted without the proper permissions set because they are formatted NTFS.  This means that the user ***nobody*** has no access rights and you can't give that user access because NTFS does not allow you to change the permissions.  

You have to remount the drive using the permissions appropriate for the user ***nobody*** for Samba sharing to work properly.

Here is the listing:

kevin@coolermaster:~$ ls -l /media/
total 4
drwxr-x---+ 6 root root 4096 Apr 29 08:24 kevin
kevin@coolermaster:~$ 

How do I remount with the correct permissions? Preferably I'd like these the mount automatically during the boot process. Thanks

---

### Post by kkc on 2015-04-29
> **bab1 said:**
> Are you sure?  The symptoms sure appear to be that or NTFS formatted partitions. Post the output of this```
sudo blkid -c /dev/null -o list
```

Here is the listing:

device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              27e9ae28-e863-402c-9273-62f86bd29b41
/dev/sda5  swap             <swap>         c4fbb983-0e98-4870-9755-4722e7b18944
/dev/sdb1  ext4             /media/kevin/87879cc4-cc77-46b4-9842-a4cc62cb035a 87879cc4-cc77-46b4-9842-a4cc62cb035a
/dev/sdc1  ext4             /media/kevin/21ac2a6b-8bce-4add-8b77-f1880b05f660 21ac2a6b-8bce-4add-8b77-f1880b05f660
/dev/sdd1  ext4             /media/kevin/8b428e8e-4a8e-4f05-93ca-2237d735bf90 8b428e8e-4a8e-4f05-93ca-2237d735bf90
/dev/sde1  ext4             /media/kevin/507e413e-da56-4301-8455-f83e93855f2d 507e413e-da56-4301-8455-f83e93855f2d
kevin@coolermaster:~$

---

### Post by bab1 on 2015-04-29
> **kkc said:**
> Here is the listing:

```
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              27e9ae28-e863-402c-9273-62f86bd29b41
/dev/sda5  swap             <swap>         c4fbb983-0e98-4870-9755-4722e7b18944
/dev/sdb1  ext4             /media/kevin/87879cc4-cc77-46b4-9842-a4cc62cb035a 87879cc4-cc77-46b4-9842-a4cc62cb035a
/dev/sdc1  ext4             /media/kevin/21ac2a6b-8bce-4add-8b77-f1880b05f660 21ac2a6b-8bce-4add-8b77-f1880b05f660
/dev/sdd1  ext4             /media/kevin/8b428e8e-4a8e-4f05-93ca-2237d735bf90 8b428e8e-4a8e-4f05-93ca-2237d735bf90
/dev/sde1  ext4             /media/kevin/507e413e-da56-4301-8455-f83e93855f2d 507e413e-da56-4301-8455-f83e93855f2d
kevin@coolermaster:~$
```
They are indeed ext partitions.  So what is the output of this command```
ls -l /media/kevin
```

At this point you are NOT allowing an world (others) permissions at all on /media.  We need to what is set on the subdirectories below that point.

[COLOR="#0000FF"]EDIT:  I wonder what acl's you are using.  What do you get from this command[/COLOR]```

getfacl /media

```

---

### Post by kkc on 2015-04-29
> **bab1 said:**
> They are indeed ext partitions.  So what is the output of this command```
ls -l /media/kevin
```

At this point you are NOT allowing an world (others) permissions at all on /media.  We need to what is set on the subdirectories below that point.

Here is the listing:
kevin@coolermaster:~$ ls -l /media/kevin
total 16
drwxrwxrwx 3 root  root  4096 Apr 27 16:20 21ac2a6b-8bce-4add-8b77-f1880b05f660
drwxrwxrwx 4 kevin kevin 4096 Apr 28 14:01 507e413e-da56-4301-8455-f83e93855f2d
drwxrwxrwx 3 root  root  4096 Apr 27 16:19 87879cc4-cc77-46b4-9842-a4cc62cb035a
drwxrwxrwx 3 kevin kevin 4096 Apr 28 08:22 8b428e8e-4a8e-4f05-93ca-2237d735bf90
kevin@coolermaster:~$ 

I think the 8b428...drive is the one I shared with Samba supposedly for all users. The 507e... is the one I tried to share with the Ubuntu network share feature.

---

### Post by kkc on 2015-04-29
> **bab1 said:**
> They are indeed ext partitions.  So what is the output of this command```
ls -l /media/kevin
```

At this point you are NOT allowing an world (others) permissions at all on /media.  We need to what is set on the subdirectories below that point.

[COLOR=#0000FF]EDIT:  I wonder what acl's you are using.  What do you get from this command[/COLOR]```

getfacl /media

```

Listing:

kevin@coolermaster:~$ getfacl /media
getfacl: Removing leading '/' from absolute path names
# file: media
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

kevin@coolermaster:~$

---

### Post by bab1 on 2015-04-29
> **kkc said:**
> Here is the listing:
kevin@coolermaster:~$```
 ls -l /media/kevin
total 16
drwxrwxrwx 3 root  root  4096 Apr 27 16:20 21ac2a6b-8bce-4add-8b77-f1880b05f660
drwxrwxrwx 4 kevin kevin 4096 Apr 28 14:01 507e413e-da56-4301-8455-f83e93855f2d
drwxrwxrwx 3 root  root  4096 Apr 27 16:19 87879cc4-cc77-46b4-9842-a4cc62cb035a
drwxrwxrwx 3 kevin kevin 4096 Apr 28 08:22 8b428e8e-4a8e-4f05-93ca-2237d735bf90
kevin@coolermaster:~$ 
```

I think the 8b428...drive is the one I shared with Samba supposedly for all users. The 507e... is the one I tried to share with the Ubuntu network share feature.

It appears that the problem might be only with the /media/kevin directory.  On the one hand the permissions show that no user other than root has access tot the /media/kevin directory.  See below (in red) ```
drwxr-x**[COLOR="#FF0000"]---[/COLOR]**[COLOR="#0000FF"]**+**[/COLOR] 6 root root 4096 Apr 29 08:24 kevin
```...but, the little plus sign (in blue) says Linux acl's are set on that directory and that shows read and traverse rights.  See here (again in blue) ```
getfacl /media
getfacl: Removing leading '/' from absolute path names
# file: media
# owner: root
# group: root
user::rwx
group::r-x
[COLOR="#0000FF"]**other::r-x**[/COLOR]
```

I would just set the permissions to read (r) write (w) and execute (x) for all (chmod 777) since that is what you have on the 4 partitions under /media/kevin.  See below (in green)```
 ls -l /media/kevin
total 16
[COLOR="#008000"]**drwxrwxrwx**[/COLOR] 3 root root 4096 Apr 27 16:20 21ac2a6b-8bce-4add-8b77-f1880b05f660
**[COLOR="#008000"]drwxrwxrwx[/COLOR]** 4 kevin kevin 4096 Apr 28 14:01 507e413e-da56-4301-8455-f83e93855f2d
[COLOR="#008000"]**drwxrwxrwx**[/COLOR] 3 root root 4096 Apr 27 16:19 87879cc4-cc77-46b4-9842-a4cc62cb035a
[COLOR="#008000"]**drwxrwxrwx**[/COLOR] 3 kevin kevin 4096 Apr 28 08:22 8b428e8e-4a8e-4f05-93ca-2237d735bf90
kevin@coolermaster:~$ 
```

Here is the command to set the permissions of rwx for all (777) on the /media/kevin directory```
sudo chmod 777 /media/kevin
```...We do not need to use recursive (-R) on the chmod command.  As I said before the permissions look correct in the subdirectories below /media/kevin.  Try that and let us know how it goes.

---

### Post by Morbius1 on 2015-04-30
The only problem with adjusting the permissions of the /media/$USER directory is that it will work until it possibly doesn't.

The system creates the /media/$USER directory at first use and sets permissions via an ACL that should in this case look something like this:
> getfacl /media/kevin
getfacl: Removing leading '/' from absolute path names
# file: media/kevin
# owner: root
# group: root
user::rwx
user:kevin:r-x
group::---
mask::r-x
other::---
Only root and kevin can traverse the /media/kevin directory and the remote samba client guest user isn't kevin.

You can override the permissions of /media/kevin but at some point in the future there may be an update that resets it back to the default.

SO the options are:

*** Reset the permissions anyway and assume that it's remote a future update will reset it.
*** OR, Since this set up allows guest access anyway add a "force user" either globally or to the share definition in /etc/samba/smb.conf so that the guest user looks like kevin to Linux:
```
force user = kevin
```
This will get you past the /media/kevein folder but at this point the guest user for that share appears to be kevin which may or may not be consistent with the permissions already present on that partition so you may need to adjust things.

*** OR, Mount these partitions one level up from where they are so as to bypass the whole /media/kevin issue. For example to have it auto mount to /media/Data1 add or change the line in /etc/fstab to look something like this:
```
UUID=8b428e8e-4a8e-4f05-93ca-2237d735bf90 /media/Data1 ext4 defaults,noatime 0 2
```
Just make sure to create the mount point:
```
sudo mkdir /media/Data1
```
Then /media/Data1 will have whatever normal linux permissions you have already set on that partition and /media/kevin will not be a gate.

[COLOR=#0000cd]EDIT: The reason this wasn't an issue in Ubuntu 10.04 is that this /media/$USER directory happened somewhere around the Ubuntu 12.10 time frame. Ubuntu 10.04 mounted things to /media/XXX not /media/$USER/XXX since there was no /media/$USER in 10.04.[/COLOR]

---

### Post by kkc on 2015-04-30
bab1 and Morbius1,

Thanks for the great advice. I mounted the one drive to /media/Data1, changed the premissions for Data 1, shared it in samba and it worked great from a win7 computer. Then I mounted (fstab) the 4 drives to the  /media/Data1 but in samba when I add a share I see 4 Data1 directories but I can only pick the first one. Should each drive be mounted in a separate sub-directory under the Data 1 directory?

---

### Post by Morbius1 on 2015-04-30
Each partition should have a different mount point:
> drwxrwxrwx 3 root root 4096 Apr 27 16:20 21ac2a6b-8bce-4add-8b77-f1880b05f660
drwxrwxrwx 4 kevin kevin 4096 Apr 28 14:01 507e413e-da56-4301-8455-f83e93855f2d
drwxrwxrwx 3 root root 4096 Apr 27 16:19 87879cc4-cc77-46b4-9842-a4cc62cb035a
drwxrwxrwx 3 kevin kevin 4096 Apr 28 08:22 8b428e8e-4a8e-4f05-93ca-2237d735bf90

So:
Data1 = UUID=8b428e8e-4a8e-4f05-93ca-2237d735bf90
Data2 = UUID=21ac2a6b-8bce-4add-8b77-f1880b05f660
Data3 = UUID=87879cc4-cc77-46b4-9842-a4cc62cb035a
Data4 = UUID=507e413e-da56-4301-8455-f83e93855f2d

Use the method you used to mount Data1 as a template for the rest of them. For Data2:

```
sudo mkdir /media/Data2
```
Then add or change the fstab line to read:
```
UUID=21ac2a6b-8bce-4add-8b77-f1880b05f660 /media/Data2 ext4 defaults,noatime 0 2
```

One line per each partition in fstab. 4 partitions = 4 separate lines with 4 different UUID's and 4 different mount points.

---

### Post by kkc on 2015-04-30
Morbuis1,

That did it, all seems to be working now. I appreciate all the help from you, bab1 and others on this forum.

---

### Post by Bucky Ball on 2015-04-30
Great work. You got there in the end. :)

---

