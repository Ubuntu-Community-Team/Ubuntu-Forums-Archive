---
title: "Best practices on EXT4 and SAMBA"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by Will_Moonen on 2014-09-30
Hi Everyone,

I'm in the process of switching from Windows 2003 to Ubuntu 14.04 LTS.

At this time, I have build a VM with Ubuntu server 14.04.1 and Webmin for testing purposes.
 
This Windows server is currently used as a file- and application server.
The application server runs partially on Apache and partially on Tomcat and is currently being tested on the VM.

So now I'm looking for some best practices on how to replace Windows 2003 filesharing with SAMBA on Ubuntu.
I have enough disks available for backup purposes in case there is a need for replacing NTFS with EXT4.

The server contains 4 NTFS volumes (drive F, L, M and N). Each of these volumes contain one or more shares.
One of these volumes is based on a Dell PERC/5i with a RAID5 config based on 5 SATA discs.
Another volume is based on 2 PATA discs configured in RAID0 @ OS level.
The other 2 volumes are single discs.

The things I'm struggling with is replacing NTFS and its file shares with EXT4 and SAMBA.
Anyone out there that can help by sharing some best practices on replacing Windows 2003 with Ubuntu 14.04 LTS?

Ideally, I would like to configure Ubuntu and SAMBA in such a way that it behaves in the same way as Windows and its workgroup approach.
Meaning that I'm *not* using a domain controller.


Thanks - Will

---

### Post by Michael_McKenney on 2014-09-30
I do SAMBA at home on my workgroup.   Setup same workgroup in SAMBA.  I use the same user name and password on Windows 7 x64 and Ubuntu.  Setup the shares and give my user rights to it.  I would consider getting external drives for backup.  Cryptolocker virus can jump and encrypt any files it hits.   I would pull the WIndows 2003 drives out and replace them with new drives for Ubuntu.  Once you are comfortable with Ubuntu working.  You can wipe the 2003 drives and add them.  Are you using domain services in Windows?  How many 2003 servers do you have?  You have to be careful with domain services running.  You don't want to break the SIDs and AD.

---

### Post by Will_Moonen on 2014-10-01
Well - I'm not sure if it is all that easy.

Users should be able to read and write in all public shares.
However, files and folders created by a certain user should only be visible for that particular user (unless these files and folders are accessed by somebody with root access). In addition, a home folder for each user is not needed and should not be created (ideally).

Currently, users can browse all shares and files. However, they can not create files and folders in any of these public shares.
In addition, while all users are created through the System section of Webmin, none of them show up under SAMBA section.

---

### Post by bab1 on 2014-10-01
> **Will_Moonen said:**
> Well - I'm not sure if it is all that easy.

Users should be able to read and write in all public shares.
However, files and folders created by a certain user should only be visible for that particular user (unless these files and folders are accessed by somebody with root access). In addition, a home folder for each user is not needed and should not be created (ideally).

This is not possible on a public share.  If objects in a directory are visable then it because the eXecute bit is set on the entire directory not on individual objects.  All attributes are set at the Linux level (Ext4)and then at the Samba level.  Samba won't allow something that Ext4 doesn't allow first.

If you want private shares then you should set up the [homes] share.  This single share will allow you to provide restrict access to only the logged in user private directory.  Yes this will mean each user has a directory, but it does absolutly have to be the users Linux /home directory. 
> 

Currently, users can browse all shares and files. However, they can not create files and folders in any of these public shares.
In addition, while all users are created through the System section of Webmin, none of them show up under SAMBA section.
I wouldn't use Webmin at all.  Learn the Linux and Samba systems commands and edit the simple text file to configure Samba (smb.conf).

---

### Post by Will_Moonen on 2014-10-02
Thanks Bab1!

I followed your recommendation and removed Webmin => stick to system commands.
Second, to make sure I start with a clean SAMBA config, I removed and re-installed SAMBA.

Based on your feedback, I would like to accomplish the following:
(1) - Create a share that is the home folder for all users. To keep things simple lets call it "Thuus"... ;-)
(2) - Create 2 public shares where all known users have read & write access. Let's call these "Data-1" and "Data-2".
(3) - Create 1 share where only admins have access to. Let's call this one "Admins".

Can you (or anybody else) guide me to this process?


Thanks - Will

---

### Post by JKyleOKC on 2014-10-02
> **Will_Moonen said:**
> (1) - Create a share that is the home folder for all users.
This can be done; that is, it's possible. However it's also possible to totally destroy a system with a single command less than a dozen bytes in length.

Similarly, having a single home folder for all users is a recipe for total disaster. Since all the personalized configuration settings that Windows would put into "user.dat" registry hives gets stored as hidden files in the user's home directory, any change by one user would affect all other users as well. Also, all files available to any user would be equally available to all, since personal data is stored in the user's home folder. And finally, the system would be unusably slow, since any user's attempt to write to a file would lock that file for the duration of the attempt, making it unavailable to everyone else -- and some of the hidden files get updated with just about every action the user takes!

So while it's possible, it's certainly not practical.

---

### Post by bab1 on 2014-10-02
> **Will_Moonen said:**
> Thanks Bab1!

I followed your recommendation and removed Webmin => stick to system commands.
Second, to make sure I start with a clean SAMBA config, I removed and re-installed SAMBA.

Based on your feedback, I would like to accomplish the following:
(1) - Create a share that is the home folder for all users. To keep things simple lets call it "Thuus"... ;-)
(2) - Create 2 public shares where all known users have read & write access. Let's call these "Data-1" and "Data-2".
(3) - Create 1 share where only admins have access to. Let's call this one "Admins".

Can you (or anybody else) guide me to this process?


Thanks - Will
With a new install you should be able to see the Samba server without doing anything.  If not then we will need to deal with that.

Assuming that you can see the server when browsing for it, we can start with making a copy of the default smb.conf file.  Use this command to make the copy ```
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.original
```  To see that you have been successful you can use this command ```
ls -l /etc/samba
```

I assume that you have an administrative account on this host (computer).  We should be able to see this account using this command```
grep -i <user-name>  /etc/passwd
```...where <user-name> is your login name.

You also need to be part of the Samba users database.  You can add yourself to the Samba user database with this command```
sudo smbpasswd -a  <user-name>
```...to see if you were successful you can view the Samba users database with this command```
sudo pdbedit -L
```

At this point we can create the directory that will be the first share we will make.  We will start with a public share.  All public shares should be created at /srv.  The is the proper directory for this type of data.  See [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") for a complete guideline for the Linux file system.  To give us some flexibility for future development (adding NFS in the future?) you should create a structure like this (/srv/samba/data1) with this command```
sudo mkdir -p /srv/samba/data1
```...the -p switch makes both the samba and the data1 directory.  You can read about the command *mkdir* here ```
man mkdir
```

Since you will be having multiple users creating file files and directories you need to have a common group for the directory *data1 *and all subdirectories.  To achieve this we need to create a group and provide inheritance.  Good practice for this is to create these groups with a distinct group ID (away from the normal user/group numbering.  I suggest you use the range starting with 2000 for these groups.  To create a group you can do this  ```
sudo groupadd -g 2000 <group-name>
```... where group name of your choice.  To see if the command worked you can do this```
getent group <group-name>
```

Now we need to change the group ownership to the directory we are going to share.  Use this command ```
sudo chgrp <group-name> /srv/samba/data1 
```... to check the work you can do this```
ls -l /srv/samba
```.  We now need to add the inheritance of group ownership for the directory /srv/samba/data1 and its subdirectories.  We do that using this command```
sudo chmod 2775 /srv/samba/data1
```...this sets the SGID bit on all data created in /srv/samba/data1 and its subdirectories.

Let me know if all of this was successful.  Then we can continue with creating the share.

---

### Post by Will_Moonen on 2014-10-02
> **JKyleOKC said:**
>  Similarly, having a single home folder for all users is a recipe for total disaster. Since all the personalized configuration settings that Windows would put into "user.dat" registry hives gets stored as hidden files in the user's home directory, any change by one user would affect all other users as well. Also, all files available to any user would be equally available to all, since personal data is stored in the user's home folder. And finally, the system would be unusably slow, since any user's attempt to write to a file would lock that file for the duration of the attempt, making it unavailable to everyone else -- and some of the hidden files get updated with just about every action the user takes! 

Thanks "JKyleOKC".

Perhaps I'm missing something here. But why would Windows want to store its settings on this SAMBA share as there is no domain involved?
The goal is to have file shares only based on workgroups.

---

### Post by bab1 on 2014-10-02
> **JKyleOKC said:**
> This can be done; that is, it's possible. However it's also possible to totally destroy a system with a single command less than a dozen bytes in length.

FUD Jim.  You can destroy a system regardless of whether you are creating a single share for home directories or not.
> 
Similarly, having a single home folder for all users is a recipe for total disaster. Since all the personalized configuration settings that Windows would put into "user.dat" registry hives gets stored as hidden files in the user's home directory

This is a Samba share for each users private data.  It's not a *Windows* home directory data at all. 
> 
, any change by one user would affect all other users as well. Also, all files available to any user would be equally available to all, since personal data is stored in the user's home folder. And finally, the system would be unusably slow, since any user's attempt to write to a file would lock that file for the duration of the attempt, making it unavailable to everyone else -- and some of the hidden files get updated with just about every action the user takes!

So while it's possible, it's certainly not practical.
It's a [homes] share in Samba.  Each user has their own directory for data.  Traditionally the Linux system admin uses the* /home *directories to store this data, but that is not always the case.  You can configure the [homes] share to any path you like.  Maybe /srv/samba/homes/<user-name>.  Remember the user only sees this: //SERVER-NAME/<user-name>

---

### Post by Will_Moonen on 2014-10-02
> **bab1 said:**
> With a new install you should be able to see the Samba server without doing anything.  If not then we will need to deal with that.

.....

Let me know if all of this was successful.  Then we can continue with creating the share.

Thank you for the detailed instructions - great! :D
Everything was successful. 

One remark when creating shares. I have reserved a single disk (/dev/sdb) for Data1 and created /dev/md0 being a soft-raid0 volume for Data2.
For the soft-raid volume, I have used the steps outlined here: [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm).
Both disks are formatted as ext4 and adjusted to 0% reserved blocks.
Let me know if this suites the things you have in mind for the next step.

---

### Post by bab1 on 2014-10-02
> **Will_Moonen said:**
> Thank you for the detailed instructions - great! :D
Everything was successful. 

One remark when creating shares. I have reserved a single disk (/dev/sdb) for Data1 and created /dev/md0 being a soft-raid0 volume for Data2.
For the soft-raid volume, I have used the steps outlined here: [http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm](http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm).
Both disks are formatted as ext4 and adjusted to 0% reserved blocks.
Let me know if this suites the things you have in mind for the next step.
It should be fine.  We will only be interested in mounting partitions to mount points.

I don't see the need for the RAID at all.  RAID is for high availability situations.  I use 0% reserved blocks myself and backup all the data..  It's up to you (unless we want to discuss this).  Both a single disk or a RAID set up will work for what we are doing.

---

### Post by Will_Moonen on 2014-10-02
No particular reason - this was just an exercise when creating volumes.
Just continue as planned.

---

### Post by JKyleOKC on 2014-10-03
> **bab1 said:**
> FUD Jim.  You can destroy a system regardless of whether you are creating a single share for home directories or not.

This is a Samba share for each users private data.  It's not a *Windows* home directory data at all. 

It's a [homes] share in Samba.  Each user has their own directory for data.  Traditionally the Linux system admin uses the* /home *directories to store this data, but that is not always the case.  You can configure the [homes] share to any path you like.  Maybe /srv/samba/homes/<user-name>.  Remember the user only sees this: //SERVER-NAME/<user-name>Sorry! I was misinterpreting his desire as wanting a common /home/everyone for multiple *buntu users, all sharing a common home directory.

I know many ways of destroying a system -- I've even managed it by attempting to defrag a WinXP box! But since I was addressing a pitfall that didn't exist, I'll bow out of the thread. Glad to know that Will achieved his goal!

---

### Post by Will_Moonen on 2014-10-03
Allright - so after some struggles with mounting volumes I have a Data1 and Data2 both mounted under /mnt. The result sofar:

=====

will@tank:~$ sudo blkid
[sudo] password for will:
```
/dev/sda1: UUID="18b8df6b-e60f-4a50-b329-0fb2f8f117c2" TYPE="ext4"
/dev/sda5: UUID="747d7b10-686d-45b5-b6f8-c6203f409c9d" TYPE="swap"
/dev/sdb: UUID="8d5270a8-3fc6-4fda-8f15-f8f20d41968b" TYPE="ext4"
/dev/sdc:  UUID="0bbe8671-7ab4-2639-9dcf-f81b645edb06"  UUID_SUB="4ac5e840-4a5c-8ab8-e4cc-53ccbd84a40a" LABEL="Tank:0"  TYPE="linux_raid_member"
/dev/md0: UUID="10b4a112-0cbb-4ab2-83cd-a500392b7348" TYPE="ext4"
/dev/sdd:  UUID="0bbe8671-7ab4-2639-9dcf-f81b645edb06"  UUID_SUB="2f43396b-c728-c425-f55d-8e0e5251403b" LABEL="Tank:0"  TYPE="linux_raid_member"

```
=====

will@tank:~$ df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        16G  2.1G   13G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  8.0K  2.0G   1% /dev
tmpfs           396M  1.2M  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdb         50G   52M   50G   1% /mnt/Data1
/dev/md0         99G   60M   99G   1% /mnt/Data2

```
=====

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=18b8df6b-e60f-4a50-b329-0fb2f8f117c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=747d7b10-686d-45b5-b6f8-c6203f409c9d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
# Mount Data1 and Data2.
# Originally /dev/sdb => Data1
UUID=8d5270a8-3fc6-4fda-8f15-f8f20d41968b /mnt/Data1 ext4 defaults 0 0
# Orginally /dev/md0 => Data2
UUID=10b4a112-0cbb-4ab2-83cd-a500392b7348 /mnt/Data2 ext4 defaults 0 0
```

=====

So what's next? :-)

---

### Post by bab1 on 2014-10-03
> **Will_Moonen said:**
> Allright - so after some struggles with mounting volumes I have a Data1 and Data2 both mounted under /mnt. The result sofar:

=====

will@tank:~$ sudo blkid
[sudo] password for will:
```
/dev/sda1: UUID="18b8df6b-e60f-4a50-b329-0fb2f8f117c2" TYPE="ext4"
/dev/sda5: UUID="747d7b10-686d-45b5-b6f8-c6203f409c9d" TYPE="swap"
/dev/sdb: UUID="8d5270a8-3fc6-4fda-8f15-f8f20d41968b" TYPE="ext4"
/dev/sdc:  UUID="0bbe8671-7ab4-2639-9dcf-f81b645edb06"  UUID_SUB="4ac5e840-4a5c-8ab8-e4cc-53ccbd84a40a" LABEL="Tank:0"  TYPE="linux_raid_member"
/dev/md0: UUID="10b4a112-0cbb-4ab2-83cd-a500392b7348" TYPE="ext4"
/dev/sdd:  UUID="0bbe8671-7ab4-2639-9dcf-f81b645edb06"  UUID_SUB="2f43396b-c728-c425-f55d-8e0e5251403b" LABEL="Tank:0"  TYPE="linux_raid_member"

```
=====

will@tank:~$ df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        16G  2.1G   13G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  8.0K  2.0G   1% /dev
tmpfs           396M  1.2M  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdb         50G   52M   50G   1% /mnt/Data1
/dev/md0         99G   60M   99G   1% /mnt/Data2

```
=====

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=18b8df6b-e60f-4a50-b329-0fb2f8f117c2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=747d7b10-686d-45b5-b6f8-c6203f409c9d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
# Mount Data1 and Data2.
# Originally /dev/sdb => Data1
UUID=8d5270a8-3fc6-4fda-8f15-f8f20d41968 /mnt/Data1 ext4 defaults 0 0
# Orginally /dev/md0 => Data2
UUID=10b4a112-0cbb-4ab2-83cd-a500392b7348 /mnt/Data2 ext4 defaults 0 0
```

=====

So what's next? :-)

Since we are creating the shares at: */srv/samba/data1* and */srv/samba/data2 * you need to mount the new partitions at those mount points.  The entries in *fstab* should look like this```

# Mount Data1 and Data2.
# Originally /dev/sdb => Data1
UUID=8d5270a8-3fc6-4fda-8f15-f8f20d41968 [COLOR="#FF0000"]/srv/samba/Data1[/COLOR] ext4 defaults 0 0
# Orginally /dev/md0 => Data2
UUID=10b4a112-0cbb-4ab2-83cd-a500392b7348 [COLOR="#FF0000"]/srv/samba/Data2[/COLOR] ext4 defaults 0 0

```...FYI:  Linux admins don't use Capital Letters.  The tradition is for lower case only (no shift key needed).  I would use data1 and data2 rather than Data1 and Data2, but both ways will work.  As a command line person, I hate the shift key.

If you need to create the mountpoint for Data2 (/srv/samba/data2) then create that before you modify the fstab file.

the directory /mnt is traditionally used for temporarily mounting partitions.  See the listings of the various filesystem hierarchies [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard").

---

### Post by Will_Moonen on 2014-10-03
Done - see below.


will@tank:~$ df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        16G  2.1G   13G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           396M  1.2M  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdb         50G   52M   50G   1% /srv/samba/data1
/dev/md0         99G   60M   99G   1% /srv/samba/data2

```

=====

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=18b8df6b-e60f-4a50-b329-0fb2f8f117c2 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=747d7b10-686d-45b5-b6f8-c6203f409c9d none            swap    sw           $
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
#
# Mount data1 and data2.
# Originally /dev/sdb => data1
UUID=8d5270a8-3fc6-4fda-8f15-f8f20d41968b /srv/samba/data1 ext4 defaults 0 0
# Orginally /dev/md0 => data2
UUID=10b4a112-0cbb-4ab2-83cd-a500392b7348 /srv/samba/data2 ext4 defaults 0 0

```

Next! :-) :-)

---

### Post by bab1 on 2014-10-03
> **Will_Moonen said:**
> Done - see below.

```

will@tank:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        16G  2.1G   13G  14% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           396M  1.2M  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M     0  100M   0% /run/user
/dev/sdb         50G   52M   50G   1% /srv/samba/data1
/dev/md0         99G   60M   99G   1% /srv/samba/data2

```

Next! :-) :-)

Great!  Now we need to recheck the ownership and permissions on both directories.  What do you get from this```

ls -l /srv/samba

```
Do we need to make a separate common user group for the share named?```
data2
``` ... if so, then we can do that now.  Look back at my instructions for creating a group.  I assume that since we created a specific group named *data1 *for the share named **data1** that we should create a group named* data2 *for the share named** data2**.  Of course you could use the same user group with either share, but this will show you how to separate user data by user groups.  Think executives vs sales vs engineering types.  ;-)

---

### Post by Will_Moonen on 2014-10-03
I have created a group in the beginning of this process - see below the results:

```
will@tank:~$ ls -l /srv/samba
total 8
drwxr-xr-x 3 root root 4096 Oct  2 19:50 data1
drwxr-xr-x 3 root root 4096 Oct  2 19:45 data2
will@tank:~$
```

However, as this group contains capitals, I would like to reverse that process.
How do I do that?

Seperating groups is a good thing as I would need that later on... :-)
So yes, l will make one group for data1 and another for data 2 - good suggestion! :-)

---

### Post by bab1 on 2014-10-03
> **Will_Moonen said:**
> I have created a group in the beginning of this process - see below the results:

```
will@tank:~$ ls -l /srv/samba
total 8
drwxr-xr-x 3 root root 4096 Oct  2 19:50 data1
drwxr-xr-x 3 root root 4096 Oct  2 19:45 data2
will@tank:~$
```
Note that the permissions and group ownership seemed to have disappeared from the directory /srv/samba/data1.  This is because you are now using that directory as a mount point so all the directory formatting is obscured by the new mounted partition.  Questions about that?

We will need to set the permissions and group inheritance now.  For group ownership of the partition do this```
sudo chgrp <user-group>  /srv/samba/<directory>
```...substitute the correct variables in each incantation.  You will need to do this for each directory (data1 and data2)

Then you need to shet the inheritance on each directory with this command```
sudo shmod 2775 /srv/samba/<directory>
```...for each directory.  After all of that post again the output of ```
sl -l /srv/samba
```
 > 

However, as this group contains capitals, I would like to reverse that process.
How do I do that?
you can delete the group and replace it with the new one.  Use this command ```
delgroup <group-name>
```...look back at my instructions for the way to add a group to add the 2 new groups.  FYI:  keep extensive notes on what you are doing so you can refer to them later.  I have kept journals on all of my installs and modifications.  BE VERBOSE, you will not remember what simple terse notes mean 6 moths from now.> 

Separating groups is a good thing as I would need that later on... :-)
So yes, l will make one group for data1 and another for data 2 - good suggestion! :-)
That's the engineering magic that separates the good admins from the average.  Thinking ahead and realizing the subtleties.  It also provides granularity.  You can have some users in one group while you have others in the second group and still others in both groups.

---

### Post by Will_Moonen on 2014-10-03
Thanks man - you are great. I hope I can return the favor one day.

What I have done sofar:

```
will@tank:~$
will@tank:~$ sudo groupadd -g 2000 regular
will@tank:~$ sudo groupadd -g 2100 admins
will@tank:~$ getent group regular
regular:x:2000:
will@tank:~$ getent group admins
admins:x:2100:
will@tank:~$ sudo chgrp admins /srv/samba/data1
will@tank:~$ sudo chgrp regular /srv/samba/data2
will@tank:~$ ls -l /srv/samba
total 8
drwxr-xr-x 3 root admins  4096 Oct  2 19:50 data1
drwxr-xr-x 3 root regular 4096 Oct  2 19:45 data2
will@tank:~$ sudo chmod 2775 /srv/samba/data1
will@tank:~$ sudo chmod 2775 /srv/samba/data2
will@tank:~$ ls -l /srv/samba
total 8
drwxrwsr-x 3 root admins  4096 Oct  2 19:50 data1
drwxrwsr-x 3 root regular 4096 Oct  2 19:45 data2
will@tank:~$

```

Any comment(s) on this?

---

### Post by bab1 on 2014-10-03
> **Will_Moonen said:**
> Thanks man - you are great. I hope I can return the favor one day.

What I have done sofar:

```
will@tank:~$
will@tank:~$ sudo groupadd -g 2000 regular
will@tank:~$ sudo groupadd -g 2100 admins
will@tank:~$ getent group regular
regular:x:2000:
will@tank:~$ getent group admins
admins:x:2100:
will@tank:~$ sudo chgrp admins /srv/samba/data1
will@tank:~$ sudo chgrp regular /srv/samba/data2
will@tank:~$ ls -l /srv/samba
total 8
drwxr-xr-x 3 root admins  4096 Oct  2 19:50 data1
drwxr-xr-x 3 root regular 4096 Oct  2 19:45 data2
will@tank:~$ sudo chmod 2775 /srv/samba/data1
will@tank:~$ sudo chmod 2775 /srv/samba/data2
will@tank:~$ ls -l /srv/samba
total 8
drwxrwsr-x 3 root admins  4096 Oct  2 19:50 data1
drwxrwsr-x 3 root regular 4096 Oct  2 19:45 data2
will@tank:~$

```

Any comment(s) on this?

Perfect.  Now we have the structure we need to create the different shares.  

You need to add the various users to the groups as you like.  There are no "admins"  (the noun) so to speak in Linux.  Only the root user.  All others are mortal users or system users.  Sudo causes root to execute a command and you either do or do not have sudo rights.  If you have  sudo rights you can admin (the verb) the system. 

But "a rose by any other name is still a rose"...  The actual group names do not need to be perfectly meaningful to work.  The system administrators just need to know what they are when diagnosing a problem.

Here is how you add user to the group of your choice```
sudo adduser <user-name> <group-name> 
```...check it with this command```
getent group <group-name>
```
 I think you should add at least to test users.  Put one in the data1 group and one in the data2 group.

Once you have at least yourself in both of these groups we can do a final test and setup the actual shares.

---

### Post by Will_Moonen on 2014-10-03
Done.
Besides myself there are 2 users in each group.

---

### Post by bab1 on 2014-10-03
> **Will_Moonen said:**
> Done.
Besides myself there are 2 users in each group.

Let's turn our attention to configuring the Samba server now.  I use vim as a text based editor but you can use nano if you like.  Nano is installed by default while the full vim package is not.

First we need to make a copy of the default smb.conf file.  Use this command to make the copy```
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.original
```

Now we can edit the file```
sudo nano /etc/samba/smb.conf
```

The first thing is to assign the server to a specific workgroup.  Find the line that starts with ```
workgroup =
```...assign the  workgroup name of your choice.  This is so users can browse to the appropriate workgroup if you multiple workgroups.

Next we can add a share at the bottom of the smb.conf file  like this ```

[Share1]
        comment = Shared Data1  
        path = /srv/samba/data1
        browseable = yes

        valid users = @admins
        force group = admins
        writeable = yes

        create mask = 0664
        force directory mode = 0775

```
Now we need to save the file (hint: cntl+x) and restart Samba with this command```
sudo service smbd restart
```

Wait about 10 minutes for the configuration changes to be made.  Then try and browse for the Samba share with this command ```
smbtree -d3
```  It should be shown as //SERVER_NAME/Share1.  You will also get a lot of debug info.  Post the output for me to see.  

Why the the force group, the create mask and the force directory mode?  Because without those things Samba will attempt to maintain the original Windows permissions.  Only the creation of files and directories via Samba will use the native ownership and permissions we set up.  In the beginning most data will be either moved or copied rather that created.  We want to keep the permission and ownership consistent..

Now we need to save

---

### Post by Will_Moonen on 2014-10-04
I have made some changes to the SMB conf file. The results are attached in a ZIP file and includes the output of "smbtree -d3".
So now I can see (and access) the shares data1 and data2.

However, the behavior is not entirely what was expected.

First, is there a specific need for the folder "lost+found" to be visible?
If not, is there a way to hide it?
Background: it may trigger questions that are not very meaningful unless there is a specific need for this folder.

Second the use of WINS.
As mentioned in the start of topic, I would like to copy the behavior of Windows file sharing as much as possible.
This includes the use of WINS and its interaction with DNS as part of the NetBIOS protocol stack.
So what I would like to accomplish is:
(1) - a consistent use of the domain name local.net 
(2) - make sure the content of DHCP, DNS and WINS are alligned with this domain name
(3) - make the server a caching DNS & WINS server => force tank.local.net to be the master browser for NetBIOS

The idea is to have all IP devices registered @ the DNS server in order to use DNS names like tank.local.net, morpheus.local.net, trinity.local.net, neo.local.net, etc. Either by creating manual DNS entries or by assuring that whenever DHCP is assigning an IP address, it gets registered in the DNS service as well.
In parellel (and where relevant), the WINS part should look for DNS entries.

Are you in a position to assist with this as well?

---

### Post by bab1 on 2014-10-04
> **Will_Moonen said:**
> I have made some changes to the SMB conf file. The results are attached in a ZIP file and includes the output of "smbtree -d3".
So now I can see (and access) the shares data1 and data2.

Glad to hear that.  Now we should configure a homes share.  I suggest you at least try this share out so you can see how it works.  The homes share is already configured in the smb.conf file.  You just need to un-comment the parameters.  Once set the individual user can either browse to the share or call it directly if you choose to make this share un-browseable.  If you insist on not implementing the [homes] share that's fine by me also.
> 

However, the behavior is not entirely what was expected.

First, is there a specific need for the folder "lost+found" to be visible?
If not, is there a way to hide it?
Background: it may trigger questions that are not very meaningful unless there is a specific need for this folder.

There are two thoughts on this.  One is to never share the top level directory of the mounted partition and thus avoiding the user seeing the Lost+Found directory.  The other method is to use a .hidden file the directory that holds the Lost + Found directory.  In the .hidden file list the directories that you do not want to show.
> 

Second the use of WINS.
As mentioned in the start of topic, I would like to copy the behavior of Windows file sharing as much as possible.
This includes the use of WINS and its interaction with DNS as part of the NetBIOS protocol stack.
So what I would like to accomplish is:
(1) - a consistent use of the domain name local.net 
(2) - make sure the content of DHCP, DNS and WINS are alligned with this domain name
(3) - make the server a caching DNS & WINS server => force tank.local.net to be the master browser for NetBIOS

The idea is to have all IP devices registered @ the DNS server in order to use DNS names like tank.local.net, morpheus.local.net, trinity.local.net, neo.local.net, etc. Either by creating manual DNS entries or by assuring that whenever DHCP is assigning an IP address, it gets registered in the DNS service as well.
In parellel (and where relevant), the WINS part should look for DNS entries.

The short answer: The above will never happen.  First, because that is not how Windows server actually works (MS may state that it works one way, but in reality it does not) and second: because some of what you want is not how Samba implements SMB resource location (SMB/CIFS share browsing). 

Let's break this down using your points. 

WINS (in reality NETBIOS Naming) is not related to DNS resolution at all.  WINS (Windows Internet Naming Service) is just the server that caches the NETBIOS information used to build the Master Browse List (MBL) in a NETBIOS naming environment (i.e. Network Neighborhood).  The DNS to NETBIOS relationship in Samba (and I would guess Windows too) is that the DNS name is used a reference to the NETBIOS name.  In other words, the Samba nmbd daemon looks to the hosts file for the name and converts that to a NETBIOS name.  All further name resolution uses NETBIOS names and suffixes.

Samba has these methods for locating the COMPUTER NAME (the NETBIOS NAME): lmhosts (depricated Lan Man), hosts (locate hostname via host file or DNS), WINS (NETBIOS NAME) or bcast (broadcasting for the NETBIOS NAME directly).  Putting aside LMhosts, the following are the pros and cons of the other methods.  

Hosts: In a traditional Samba environment (Samba v3) "hosts" requires a static IP address and hostname mapping in either the /etc/hosts file or a DNS server. The FQDN is not needed and DNS is the most complicated method to use if you are using DHCP to assign IP adddresses.  At this time you would need to fully impliment Samba's version of Active Directory (AD) to get the benifits of integrated DHCP and DNS.  Since this renders the DNS name down to the NETBIOS name anyway it's not really needed in a simple workgroup environment.

WINS: This is a direct NETBIOS only way to locate SMB resources.  It is needed if you have a multi-segment LAN.  That and the fact that you reduct the ammount of broadcast traffic is the only reason to impliment a WINS server.

Bcast:  This is the simplest way to locate SMB resources.  It is limited to use on a single segment LAN as The broadcast domain is limited to the single segment.

As you can see all roads lead to the NETBIOS name.  So how does NETBIOS naming really work?  Nothing like DNS at all.  In traditional static DNS the dns name (hostname.domain.tld) is mapped to an address.  Later DNS fuctionalality now allows for DHCP servered IP addresses to change and be mapped to the FQDN.  This is something that NETBIOS has had for 25 years or so, but slightly different.

When the NETBIOS host appears on the network (boots up) the NETBIOS NAME (COMPUTER NAME) is annouced ant the IP address is matched at that time.  This information is stored at the MASTER BROWSER (MB) if there is no WINS server or retrived by the MB if a WINS server is employed.

In my opinion you should provide the NETBIOS NAME for the Samba server.  This eliminates the need to convert the hostname to the NETBIOS NAME from the its hosts file.  This turns off that aspect in the nbmd daemon (the naming daemon for Samba).  This can be added to the smb.conf file in the [globla] section with this```
netbios name = <your-hosts-name>
```

When the user is searching for a Windows/Samba share (SMB reasource) this is always what they see:
//NETBIOS_NAME/share-name.  In your case it is //TANK/data1 or //TANK/data2.  TANK is not the dns name 
at all.


At this point I'll bet you have a ton of questions so fire away!
> 

Are you in a position to assist with this as well?
Sure thing.  Let me point out one thing and make some comments from the smbtree file.  This might help with what I've said above.  You do not want to try and replicate all that the WIN2003 server is doing.  Samba has its own way to achive what Windows does.  The outcome is more important that the specific process.

The comments will be in red below the instance.```
will@tank:~$ smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
[COLOR="#FF0000"]# Samba reads the smb.conf file[/COLOR]
added interface eth0 ip=192.168.0.150 bcast=192.168.0.255 netmask=255.255.255.0
added interface virbr0 ip=192.168.122.1 bcast=192.168.122.255 netmask=255.255.255.0
[COLOR="#FF0000"]# Samba reads the announcement of the Samba server to the network[/COLOR]
Enter will's password:
tdb(/var/cache/samba/gencache.tdb): tdb_open_ex: could not open file /var/cache/samba/gencache.tdb: Permission denied
resolve_lmhosts: Attempting lmhosts lookup for name NEBUCHADNEZZAR<0x1d>
resolve_lmhosts: Attempting lmhosts lookup for name NEBUCHADNEZZAR<0x1d>
[COLOR="#FF0000"]# Samba  attempts to use the lmhosts file to find the workgroup -- note the <0x1d> suffix
# NETBIOS uses a 15 character name and 1 character suffix to determine the type of resource[/COLOR]
name_resolve_bcast: Attempting broadcast lookup for name NEBUCHADNEZZAR<0x1d>
[COLOR="#FF0000"]# Samba ends up using  bcast to find the workgroup.  No WINS and NO hosts[/COLOR]
Got a positive name query response from 192.168.122.1 ( 192.168.122.1 )
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7eff72343e10] mpx_fde[(nil)] fd[9] - disabling
Connecting to 192.168.122.1 at port 445
[COLOR="#FF0000"]# via NetBIOS over TCP (NBT)[/COLOR]
...
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\TANK                          tank server (Samba, Ubuntu)
[COLOR="#FF0000"]# Found the NETBIOS name TANK[/COLOR]

resolve_lmhosts: Attempting lmhosts lookup for name TANK<0x20>
resolve_lmhosts: Attempting lmhosts lookup for name TANK<0x20>
[COLOR="#FF0000"]# Note the different suffix used for the NETBIOS NAME vs the workgroup name[/COLOR]
resolve_wins: using WINS server 69.172.201.208 and tag '*'
[COLOR="#FF0000"]# Attempts to use an Internet host as a WINS server.  This means that your ISP is
# using DNS redirects (not a standard protocol) and your DNS is not set up correctly
# you should not forward unresolved local DNS requests.[/COLOR]
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7eff72357a90] mpx_fde[(nil)] fd[12] - disabling
resolve_hosts: Attempting host lookup for name TANK<0x20>
Connecting to 127.0.1.1 at port 445
[COLOR="#FF0000"]# This is from your /etc/hosts file and it should not be 127.0.1.1 (the looback)[/COLOR]
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\TANK\IPC$             IPC Service (tank server (Samba, Ubuntu))
                \\TANK\Data2            Shared data2
                \\TANK\Data1            Shared data1
                \\TANK\print$           Printer Drivers
...
will@tank:~$ 
```

So we need to add additional configuration to the smb.conf file and the /etc/hosts file.

Post the output of these commands```
cat /etc/hosts

cat /etc/network/interfaces
```

---

### Post by Will_Moonen on 2014-10-04
Going backwards...

The requested output:
```
will@tank:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       tank

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

=====

will@tank:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.150
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.244
dns-nameservers 62.179.104.210 213.46.228.210 8.8.8.8 8.8.4.4
```

As for Netbios and DNS:
Indeed - I have a some questions here. However, this has to wait as I'm about to hit the sack - it is around 11 PM here.
I have the catch a plane to Milan-Italy tomorrow morning for a 3-day tech event.
So the questions, while a limited amount, will have to wait a little. 

Apart from the questions: to a certain extend I agree to the principle - it is not so much the process that counts - it's the results.

Have a nice evening and I will try to find some time tomorrow to line up some questions.

Again, thanks sofar and perhaps till tomorrow!

---

### Post by bab1 on 2014-10-04
> **Will_Moonen said:**
> 
As for Netbios and DNS:
Indeed - I have a some questions here. However, this has to wait as I'm about to hit the sack - it is around 11 PM here.
I have the catch a plane to Milan-Italy tomorrow morning for a 3-day tech event.
So the questions, while a limited amount, will have to wait a little. 

Apart from the questions: to a certain extend I agree to the principle - it is not so much the process that counts - it's the results.

Have a nice evening and I will try to find some time tomorrow to line up some questions.

Again, thanks sofar and perhaps till tomorrow!

I'm surprised.  Your Ubuntu host is slightly broken.  Particularly your Samba Server WINS usage and the Ubuntu hostname configuration.  Are you interested it fixing those items?

Re read the last post when you aren't so tiered and reply tomorrow or Monday.  I'll only be available in the evenings the rest of the weekend.

---

### Post by JKyleOKC on 2014-10-04
> **bab1 said:**
> I'm surprised.  **Your Ubuntu host is slightly broken.**  Particularly your Samba Server WINS usage and the **Ubuntu hostname configuration**.  Are you interested it fixing those items?Every copy of Xubuntu I've seen, for the past seven years, has included the defined hostname in the /etc/hosts file and associated it with 127.0.1.1. This appears to be a *buntu extension to the "standard" usage of the hosts file and the loopback IP address space -- I hesitate to call it "*slightly broken*" although I might describe it as "*broken by design*."

---

### Post by bab1 on 2014-10-04
> **JKyleOKC said:**
> Every copy of Xubuntu I've seen, for the past seven years, has included the defined hostname in the /etc/hosts file and associated it with 127.0.1.1. This appears to be a *buntu extension to the "standard" usage of the hosts file and the loopback IP address space -- I hesitate to call it "*slightly broken*" although I might describe it as "*broken by design*."

Yes indeed.  This was originally done to accommodate lazy developers of applications that needed the host to have a hostname mapped to an IP address.  They just *assumed *that every machine had a hostname mapped to some network interface.  I think this is more a Debian fix handed down to Ubuntu but it may be in other distro lines also.  Most of the time users don't even notice as they don't call their own desktop from another machine across a network.  As soon as you  involve running a server daemon that needs to be found by a static address or hostname then it becomes broken.  So I guess we should call this "slightly broken by design".

FYI -- A Samba server does not need to have a static IP address as it announces its NETBIOS name (COMPUTER NAME) and what ever its current IP address is.  The Master Browser or a WINS server holds that mapping.

---

### Post by Will_Moonen on 2014-10-05
> **bab1 said:**
> I'm surprised.  Your Ubuntu host is slightly broken.  Particularly your Samba Server WINS usage and the Ubuntu hostname configuration.  Are you interested it fixing those items?

Re read the last post when you aren't so tiered and reply tomorrow or Monday.  I'll only be available in the evenings the rest of the weekend.

What exactly seems to be broken and why?
And of course I'm interested in fixing things.

I'm not experiencing any issues - connectivity or otherwise.

Keep in mind that I have forced a Windows 2003 server to be master browser and DNS forwarder.
I have manually entered tank.local.net in that DNS database.
Most likely, this is why it doesn't affect me?

---

### Post by bab1 on 2014-10-05
> **Will_Moonen said:**
> What exactly seems to be broken and why?
And of course I'm interested in fixing things.
The short answer is as I previously stated; the hosts file and WINS broken. @JKyleOKC has also commented on the hosts problem. The WINS problem is a configuration problem in the smb.conf file.

First the DNS problem. When a Linux host checks for a dns hostname it first checks its own /etc/hosts file. Then it checks the local dns server for LAN resolution. You appear to have not configured a local DNS server to the host TANK. In no instance should a Samba server's local hostname (e.g tank) be forwarded to the Internet to attempt resolution. The FQDN is not relevant to the issue except to gain the hostname only. The local hosts file is dependent on static IP address use. With proper entries in the /etc/hosts file your server will resolve it's hostname without needing a DNS lookup. This is the proper way of configuring hosts/DNS. Your /etc/hosts should have an entry like this  
```
will@tank:~$ cat /etc/hosts
# Loopback address available to this host only
127.0.0.1       localhost
# The eth0 network interface for LAN connectivity (calling this host by it's hostname)
192.168.0.150       tank

```...assuming that the host TANK is 192.168.0.150.  What host uses 192.168.122.1?  Is that the host NAS?

Here is what my /etc/hosts file looks like for my workstation
```
# loopback Interface
127.0.0.1       localhost
# Infrastructure Devices
192.168.1.1     bb-gw1
192.168.1.200   bb-hp1
192.168.1.245   bb-ap1
# hosts on Network
192.168.1.3     malibu
192.168.1.4     manila
192.168.1.2     rincon
192.168.1.5     ventura
```

Now to the WINS problem.  It's not working at all.  This debug entry shows that```
resolve_wins: using WINS server 69.172.201.208 and tag '*'
samba_tevent: EPOLL_CTL_DEL EBADF for fde[0x7eff72359340] mpx_fde[(nil)] fd[14] - disabling
```...This is because the resolve_wins routine is looking for a WINS server at ```
69.172.201.208
``` This is a public Internet address and should never have a WINS server configured on it.  Samba is for private local LAN's only. In fact checking that address reveals this is public IP address for [http://69.172.201.208.ipaddress.com/"]Peer 1 Network (USA)](")  Not a WINS server at all.

Your configuration of WINS in the smb.conf file is incorrect also.  This could be part of the problem.  I have colored the orighinal to the smb.conf comments to [COLOR="#008000"]**green**[/COLOR].  See my comments in [COLOR="#FF0000"]red[/COLOR] below.  The section of the smb.conf file that configures WINS

```

# Windows Internet Name Serving Support Section:

**[COLOR="#008000"]# WINS Support - Tells the NMBD component of Samba to enable its WINS Server [/COLOR]**
   wins support = yes

[COLOR="#FF0000"]The boolean above controls whether the nmbd daemon in Samba on this host (TANK) will act as a WINS server. 
#You should not set this to yes unless you have a* multi-subnetted* network and you wish a particular nmbd to be your WINS server. 
# Note that you should *NEVER* set this to yes on *more than one machine* in your network.[/COLOR]

[COLOR="#008000"][B]# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both[/B][/COLOR]
   wins server = morpheus.local.net  <--What is the IP address of this host?

[COLOR="#FF0000"]# This specifies the IP address (or DNS name ( the IP address is preferred)) of the WINS server that nmbd daemon should register with. 
# If you have a WINS server on your network then you should set this to the WINS server's IP.   
# Tank is now asking to be a client of some other WINS server.  See the comments in green just above the parameter.  
#   FYI: Since this is never seen by a human after it is configured you should keep this as simple as possible -- use the IP address instead of 
#   having the DNS name resolved.  If the DNS server errors you have no access to the WINS server if you use a FQDN.[/COLOR]

[COLOR="#008000"]# This will prevent nmbd to search for NetBIOS names through DNS.[/COLOR]
   dns proxy = yes


```   
> 
I'm not experiencing any issues - connectivity or otherwise.
Ahhh, but you are.  You just don't know it.  Windows sharing and Samba have plenty of security holes so it should never be used over the Internet (no public addressing at all).  If you want this to work using the hosts files (dns) then you need to set that up correctly.  If you want WINS to work you need to set that up correctly.  If you want to close the possible security breach casued by the attempts to resolve a WINS server name via the public Internet, you need to set that up correctly also. > 

Keep in mind that I have forced a Windows 2003 server to be master browser and DNS forwarder.
I have manually entered tank.local.net in that DNS database.
Most likely, this is why it doesn't affect me?

You are affected.  I don't see any reason for the Windows 2003 server to always win the MB election or for it to forward any local.net inquries.  In fact DNS is only needed on a very limited basis andyou haven't set that up correctly anyway.

The reason it all works is because Samba continues its attemps to connect using this list of methods```
name resolve order = lmhosts wins host bcast
```...they all fail until you get to bcast (the original Windows way) and then it works.

The bottom line is you need to either set up the hosts file and WINS correctly, or, set up the system to only use bcast and close the potential security breach with WINS that you have .  Either way will work on a small to moderately sized single segment LAN.

Which way do you want to proceed?  Or do you just want to leave it as it is?

---

### Post by Will_Moonen on 2014-10-06
The server indicated by morpheus.local.net has IP address 192.168.0.250.
This server is configured as a DNS forwarder and WINS server (i.e. MB) - or at least that is how it's supposed to work.

The general idea is that the DNS forwarder caches DNS client requests including the translation from their <something>.local.net to IP address being 192.168.0.<something> and v.v. Therefor preventing the use of the hosts file as much as possible.

I don't know where 69.172.201.208 and 192.168.122.1 are coming from.

This morpheus server is supposed to be replaced by thank. Or better, I'm using tank to learn Ubuntu to the extend that I can apply this knowledge to transform morpheus from a Windows 2003 server into an Ubuntu server.

So the way I want to proceed is change things to whatever is needed to support this initiative.

Do I make myself clear? And perhaps more important, does it make sense?

---

### Post by bab1 on 2014-10-06
> **Will_Moonen said:**
> The server indicated by morpheus.local.net has IP address 192.168.0.250.
This server is configured as a DNS forwarder and WINS server (i.e. MB) - or at least that is how it's supposed to work.

The only way I know to configure  a Windows 2003 server to act as a DNS server is to use "DCPromo"  Did you do that? 

A Samba WINS client should not be configured as the WINS server.  These are two different things.  The way you have Samba configured is as both a WINS server and a WINS client.  This is NOT CORRECT.  You need to fix that.  WINS is not working for Samba right now.

What did you do to insure that the Windows server was always the MB?
> 

The general idea is that the DNS forwarder caches DNS client requests including the translation from their <something>.local.net to IP address being 192.168.0.<something> and v.v. Therefor preventing the use of the hosts file as much as possible.

Configuring Windows DNS does not prevent the Linux host from checking the /etc/hosts file first.  In fact Linux always checks the hosts file before DNS.  Since Samba is not finding the correct hostname anywhere it is failing to successfully use the "hosts" method.
> 

I don't know where 69.172.201.208 and 192.168.122.1 are coming from.

I told you.  It's because the "hosts" method of name resolution is not working correctly.
> 

This morpheus server is supposed to be replaced by thank. Or better, I'm using tank to learn Ubuntu to the extend that I can apply this knowledge to transform morpheus from a Windows 2003 server into an Ubuntu server.

Your original post was " how to replace Windows 2003 filesharing with SAMBA"  This is not the same as replacing the entire Active Directory (AD) Domain Controller (DC) itself.

By your description the host *morpheus* is as an Active Directory (AD) Domain Controller (DC) server. Not just a file server.  If you want TANK to be an DC you have a lot more to do than just setting up shares.  Are you aware of that?  Samba v4 is capable of providing that functionality but is not a trivial thing.  The learning curve is huge. 
> 
So the way I want to proceed is change things to whatever is needed to support this initiative.

Do I make myself clear? And perhaps more important, does it make sense?
Not in my mind.  I doesn't make much sense if you can't even get the Samba server to perform correctly as a standalone file server.  There are two aspects to both of these servers.  Whether you are speaking of Windows2003 or Samba v4 you have a "file server" component and a "centralized user and networking" (DC) component.

If using Samba as a DC is what you want then you need to read and understand these documents:
[https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO]("https://wiki.samba.org/index.php/Samba_AD_DC_HOWTO")

[https://wiki.samba.org/index.php/User_Documentation]("https://wiki.samba.org/index.php/User_Documentation")

[http://www.samba.org/samba/GUI/]("http://www.samba.org/samba/GUI/")

[http://ubuntuforums.org/showthread.php?t=2146198]("http://ubuntuforums.org/showthread.php?t=2146198")

You should have a working knowledge of TCP/IP networking, DNS, DHCP, Kerberos and LDAP for this project to be successful well as NETBIOS and Windows sharing for the basic file sharing.

I still suggest you fix the Samba server errors you have now before you update it to a DC replacement.  If you don't do that you will have more problems as you go along.

Good Luck.  This is going to be a long complex project.

---

### Post by Will_Moonen on 2014-10-07
In principle, I know how DHCP, DNS and WINS works. This includes when the hosts file is used.

As far as DNS and the hosts file goes, I prefer adding DNS entries as opposed to adding entries in the hosts file.
This way I have a single instance for the translation between name and IP address as the stations asking for an IP address through DHCP can not interact with the hosts file. While these stations are able to interact with a DNS service.

There is *no* AD and *no* DC involved - the Windows 2003 server indicated as morpheus or morpheus.local.net (IP is 192.168.0.250) is acting as a basic, single fileserver - no authorization against an AD on a DC.

As far as installing the DNS service goes: it can be installed as a standalone network service - see also: [http://support2.microsoft.com/kb/814591](http://support2.microsoft.com/kb/814591).
Years ago, around the Matrix-1 movie release timeframe, I installed and configured this basic Windows file server. Some time after, I added the network service WINS and DNS. Never was I asked for a DCpromo to make things happen - it only wanted to know a (DNS) domain name - which is where local.net comes from.

So all and all, in terms of the post title, I would say it is still valid. Because again, there is *no* AD and *no* DC and I have *no* intention in adding these.

What I meant with "I don't know where 69.172.201.208 and 192.168.122.1 are coming from." is that I don't know where these requests are coming from - as in: who is the initiator. I'm planning for some packet capturing to figure out where it comes from (i.e. initiates this). 

Assuming that we are still on the same page with this: below are the latest versions of hosts, smb.conf and the output of smbtree -d3.

```
127.0.0.1    localhost

127.0.1.1    tank
127.0.1.1    tank.local.net

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

=====

```
will@tank:~$ sudo smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.150 bcast=192.168.0.255 netmask=255.255.255.0
added interface virbr0 ip=192.168.122.1 bcast=192.168.122.255 netmask=255.255.255.0
Enter root's password:
Connecting to 192.168.122.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
NEBUCHADNEZZAR
Connecting to 192.168.122.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\TANK                          tank server (Samba, Ubuntu)
Connecting to 192.168.0.150 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\TANK\IPC$             IPC Service (tank server (Samba, Ubuntu))
                \\TANK\Data2            Shared data2
                \\TANK\Data1            Shared data1
                \\TANK\print$           Printer Drivers
        \\NAS                           LG-NAS server
Connecting to 192.168.0.251 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\NAS\IPC$              IPC Service (LG-NAS server)
                \\NAS\cdrom             CD-ROM device
                \\NAS\Data              Data @ volume 1
                \\NAS\FTP               FTP folder @ volume1
                \\NAS\service$          Default Service Folder
will@tank:~$

```

=====

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = nebuchadnezzar

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
   wins server = 192.168.0.250

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = yes

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam
   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Data1]
   comment = Shared data1
   path = /srv/samba/data1
   browseable = yes

   valid users = @admins
   force group = admins
   writeable = yes

   create mask = 0664
   force directory mode = 0755

[Data2]
   comment = Shared data2
   path = /srv/samba/data2
   browseable = yes

   valid users = @regular
   force group = regular
   writeable = yes

  create mask = 0664
  force directory mode = 0755

```

Any comment on this? Anything you would like me to change?

---

### Post by bab1 on 2014-10-07
> **Will_Moonen said:**
> In principle, I know how DHCP, DNS and WINS works. This includes when the hosts file is used.

As far as DNS and the hosts file goes, I prefer adding DNS entries as opposed to adding entries in the hosts file.
This way I have a single instance for the translation between name and IP address as the stations asking for an IP address through DHCP can not interact with the hosts file. While these stations are able to interact with a DNS service.

There is *no* AD and *no* DC involved - the Windows 2003 server indicated as morpheus or morpheus.local.net (IP is 192.168.0.250) is acting as a basic, single fileserver - no authorization against an AD on a DC.

As far as installing the DNS service goes: it can be installed as a standalone network service - see also: [http://support2.microsoft.com/kb/814591](http://support2.microsoft.com/kb/814591).
Years ago, around the Matrix-1 movie release timeframe, I installed and configured this basic Windows file server. Some time after, I added the network service WINS and DNS. Never was I asked for a DCpromo to make things happen - it only wanted to know a (DNS) domain name - which is where local.net comes from.

So all and all, in terms of the post title, I would say it is still valid. Because again, there is *no* AD and *no* DC and I have *no* intention in adding these.


You sound like a lawyer advocating your position or a salesman making a pitch.

Samba **file services** do not include the installation of DHCP or DNS,  If you want to install these Ubuntu packages (ISC DHCP server and BIND9)  outside of the integrated Samba packages for these services in a DC environment you certainly can.  It is outside the scope of " filesharing with SAMBA" in this thread.  I would create 2 new threads.  One asking how to install and configure the ISC DHCP server package (isc-dhcp-server) and all the appropriate utilities and another separate thread on installing BIND9 and all of its utilities.   
> 
What I meant with "I don't know where 69.172.201.208 and 192.168.122.1 are coming from." is that I don't know where these requests are coming from - as in: who is the initiator. I'm planning for some packet capturing to figure out where it comes from (i.e. initiates this). 

I already know the answer to this.  You have fixed it with the proper WINS configuration.
> 

Assuming that we are still on the same page with this ... 
  I don't think we are.  So let me be blunt about my position.  I won't help you in this forum thread with DHCP or DNS package install or configuration.  You need to open 2 new threads.  One for each subject.

> 
below are the latest versions of hosts, smb.conf and the output of smbtree -d3.
```
127.0.0.1    localhost

127.0.1.1    tank
127.0.1.1    tank.local.net

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

=====

```
will@tank:~$ sudo smbtree -d3
lp_load_ex: refreshing parameters
Initialising global parameters
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=192.168.0.150 bcast=192.168.0.255 netmask=255.255.255.0
added interface virbr0 ip=192.168.122.1 bcast=192.168.122.255 netmask=255.255.255.0
Enter root's password:
Connecting to 192.168.122.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
NEBUCHADNEZZAR
Connecting to 192.168.122.1 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
        \\TANK                          tank server (Samba, Ubuntu)
Connecting to 192.168.0.150 at port 445
Doing spnego session setup (blob length=74)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=not_defined_in_RFC4178@please_ignore
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\TANK\IPC$             IPC Service (tank server (Samba, Ubuntu))
                \\TANK\Data2            Shared data2
                \\TANK\Data1            Shared data1
                \\TANK\print$           Printer Drivers
        \\NAS                           LG-NAS server
Connecting to 192.168.0.251 at port 445
Doing spnego session setup (blob length=42)
got OID=1.3.6.1.4.1.311.2.2.10
got principal=NONE
Got challenge flags:
Got NTLMSSP neg_flags=0x608a8215
NTLMSSP: Set final flags:
Got NTLMSSP neg_flags=0x60088215
NTLMSSP Sign/Seal - Initialising with flags:
Got NTLMSSP neg_flags=0x60088215
                \\NAS\IPC$              IPC Service (LG-NAS server)
                \\NAS\cdrom             CD-ROM device
                \\NAS\Data              Data @ volume 1
                \\NAS\FTP               FTP folder @ volume1
                \\NAS\service$          Default Service Folder
will@tank:~$

```

=====

```

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = nebuchadnezzar

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
   wins server = 192.168.0.250

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = yes

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam
   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[Data1]
   comment = Shared data1
   path = /srv/samba/data1
   browseable = yes

   valid users = @admins
   force group = admins
   writeable = yes

   create mask = 0664
   force directory mode = 0755

[Data2]
   comment = Shared data2
   path = /srv/samba/data2
   browseable = yes

   valid users = @regular
   force group = regular
   writeable = yes

  create mask = 0664
  force directory mode = 0755

```

Any comment on this? Anything you would like me to change?
The above looks fine to me.  The smbtree -d3 output has no errors now.

If you want to allow TANK to become the WINS server you may do so.  Just set TANK to be the WINS server and stop pointing to 192.168.0.250 as a WINS client.

Other than that we have accomplished all that we can regarding Samba file sharing.  Good luck with integrating DHCP and DNS on the host TANK.

---

### Post by Will_Moonen on 2014-10-08
Thanks for the help.

I agree to creating 2 new threads. So after doing some homework on these topics as how it is supposed to work within Ubuntu/Linux, I will create these 2 topics. Hope to hear from you there! :-)

---

