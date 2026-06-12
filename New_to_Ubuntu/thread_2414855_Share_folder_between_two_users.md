---
title: "Share folder between two users"
date: 2019-03-16
forum: New to Ubuntu
---

### Post by weirdygeekpsych on 2019-03-16
So I tried the steps explained first answer in this [link]("https://askubuntu.com/questions/291501/share-a-folder-between-two-local-users") to share some folders from Primary user home[admin] folder to my second user[std].

Unfortunately, when I change and close the group permission it reset to how it was. my changes doesn't take place. 

How to actually change it?

---

### Post by TheFu on 2019-03-16
Trying to share a HOME with all the settings is a bad idea.  Sharing data and programming directories is relatively safe.

Please provide some facts with command output. **ls -al **on the directory and files you'd like to share.  Also need proof that both userids are in the same group - **id** on both uids will prove that. Please post using _code tags_.

Only the "owner" can change permissions on files or directories.
The setgid flag (chmod g+s) is very important on the empty directory BEFORE any files are copied in/created by either userid.
The permissions you want are:
```
$ \ls -al
total 156
drwxrwsr-x   10 thefu   group    4096 Feb  1 08:29 .
drwxr-xr-x   30 root    root     4096 Feb 23 13:28 ..
drwxrwsr-x  123 thefu   group    4096 Feb 11 13:42 T
drwxrwsr-x    4 thefu   group    4096 Aug 23  2017 V
```
"group" has a few userids in it.  See the 's' on the group execute permission?  That is the setgid flag. The eXecture flag is also set on the directories, just cannot be shown at the same time.  Group membership matters greatly but the setguid flag with the correct group set are critical.

---

### Post by weirdygeekpsych on 2019-03-16
I have added my secondary user(group) to primary group.

I am not sharing my primary Home folder. the folder I am willing to share is not from OS partition. 

Although I have another doubt, why there is a creation of group is same name as when I create a standard user?

---

### Post by TheFu on 2019-03-16
So no **ls -al**?
No output from **id**?
Cannot help. Sorry.

---

### Post by weirdygeekpsych on 2019-03-17
1000 -primary and 1001 -secondary

May I know why you are asking for information of ls -al? as it is showing important information on my directory permission things and all?

---

### Post by yancek on 2019-03-17
You are posting what appears to be conflicting information.  In your initial post, you indicate that "to share some folders from Primary user home[admin] folder to my second user[std]."  THis would seem to indicate you are sharing or trying to share a sub-directory in your /home/user directory.   In a subsequent post your state "I am not sharing my primary Home folder. the folder I am willing to share is not from OS partition."  So where on the system is it?  Is it on a secondary partition/hard drive?  Is it a Linux filesystem or some other type?  If it is a windows filesystem, windows doesn't understand Linux permissions.

> Unfortunately, when I change and close the group permission it reset to how it was. my changes doesn't take place.

That doesn't tell us much.  How exactly did you try to make this change?  Were you using your filemanager (nautilus?) logged in as the user who has ownership of the directory?  Logged in as another user?  Logged in and using a terminal as root/sudo?  The inability to make the changes should result in an error being output giving the reason or it would be expected behavior on a 'live' system on which changes cannot be made.  Since you appear to have an installed system, did you get any response when you attempted to make the changes however your tried to make them?

> May I know why you are asking for information of ls -al? as it is showing important information on my directory permission things and all?

The owner/group and permissions on the directory in question are needed to see if they are correct.  There is nothing 'secret' about them as they are standard with the exception of your user name.

---

### Post by TheFu on 2019-03-17
> **jegan2 said:**
> 1000 -primary and 1001 -secondary

May I know why you are asking for information of ls -al? as it is showing important information on my directory permission things and all?

You are trying to have 2 userids on the same system be able to access and read-write to the same files.  That is a permissions question.
When we ask for facts and for commands, it isn't because we are nosey.  The directory permissions impact the file and directory access for anything contained inside. The file permissions impact the files.

That's why I asked.  Also, the specific commands show the required data. It isn't dumbed down like most GUIs do it. The subtle things shown are critical to getting this working.

We've already many hundreds of assumptions, but the most likely issue is the permissions are incorrect.

The other main condition is that a Linux file system be used, not NTFS, FAT-whatever, as yancek says.  Unix permissions for foreign file systems are controlled by mount options. They cannot be modified post-mount 99.999% of the time. Only enterprises with full-time admins are likely to make foreign file system permissions work in a native way. It is a big hassle.

"Sharing" is vague. Network sharing via CIFS/NFS is different from making directories where all the users are on the same computer.

---

### Post by oldfred on 2019-03-17
The users trying to help you know more than me.
But if you search forum you would find these threads on similar topics, but all those have required user to post info so specific suggestions to help can be made.

Threads are now older, but ownership & permissions have not changed.

       Group Permissions - Morbius1
[http://ubuntuforums.org/showthread.php?t=2138476](http://ubuntuforums.org/showthread.php?t=2138476) 
            Share folder among two users of same PC.- morbius1
[http://ubuntuforums.org/showthread.php?t=2033060](http://ubuntuforums.org/showthread.php?t=2033060)
[http://ubuntuforums.org/showthread.php?t=1998114](http://ubuntuforums.org/showthread.php?t=1998114)
[http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)
Two users to share music folder - group & permissions -BoneKracker:
[http://ubuntuforums.org/showthread.php?t=1484221](http://ubuntuforums.org/showthread.php?t=1484221)
[http://ubuntuforums.org/showthread.php?t=1488065](http://ubuntuforums.org/showthread.php?t=1488065)
All users read/write shared folder - morbius1
[http://ubuntuforums.org/showthread.php?t=1727396](http://ubuntuforums.org/showthread.php?t=1727396)

---

### Post by weirdygeekpsych on 2019-03-24
@yancek , yes the folder is in another hard drive that shares as NTFS partition with windows, FYI , Two hard disks 

1) one harddisk for OS alone(Ubuntu, Windows 10)

2) second hard disk for files which is a dedicated one in NTFS format.

I am planning to share some specific folder from my secondary hard disk in between two ubuntu users


And here's what I did?

I added the secondary(standard user) to my first group(Administrator)

and opened nautilus in root mode to change the permissions of that specific folder, unluckily once I close that dialog box default permission of group is being set.

Hope I answered all your questions.

---

### Post by yancek on 2019-03-24
If I'm understanding your last post, you are trying to share a specific folder on a partition with an ntfs filesystem, is that correct?  Windows (ntfs) filesystems do not understand the standard Linux permissions.  If you are wanting to share data in a folder between two Ubuntu users, why on an ntfs filesystem?  You might be able to accomplish what you want by using dmask, umask.

---

