---
title: "Setup permissions for SMB and Transmission"
date: 2021-01-21
forum: New to Ubuntu
---

### Post by hikariws on 2021-01-21
I'm having a very odd situation :/


I had built a server and now added 4 HDs to it on RAID 5. Among other stuff I'm installing Transmission and migrating torrents from old server to it.


As we know, transmission-daemon runs under debian-transmission user. So, I need both my user and debian-transmission to be able to create new folders and files, write on existing ones and read them.


I also have SMB set on this RAID and only my user is able to login. I need files accessed from SMB to be created, written and read as if I was logged from SSH.


I wanna avoid adding debian-transmission to my group and vice-versa, so I had created a group naswrite and added both users to it, but this got even worse. `chmod g+s` doesn't work, when a new file is created it gets its user and group. IDK why, when I from SMB or Transmission create a folder, we're unable to rename it or create files inside it. From SSH it works fine.


I'm having to run `chgrp -R naswrite downloads && chmod -R g+rw downloads` to fix it, but then when a new folder is created inside it the same issue happens. When Transmission creates a folder and fails to create files inside it, it stops trying and I have to restart it.


What's the best practice to handle this? Should I just give up and set it to run on my user?

---

### Post by TheFu on 2021-01-21
Which file system?

[https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) explains the details for working together in the same directory. Of course, native linux file systems are required.

---

### Post by hikariws on 2021-01-21
ext4

Gonna read it, tnx

---

### Post by hikariws on 2021-01-21
Unfortunately it didn't work :/

Here's the script I made to set permissions:

```
#!/bin/bash


find /nas/raid -type d -exec chmod 775 {} \;
find /nas/raid -type f -exec chmod 664 {} \;
chown -R hikari:naswrite /nas/raid
chmod -R g=rwxs /nas/raid
find /nas/raid -type f -exec chmod -x {} \;

```

I know it has redudancy, I'm still trying to make it work.

The improvement is that now when transmission creates a folder is has proper group:

```
drw-rwsr-x+ 2 debian-transmission naswrite        4096 jan 21 23:09
```

But the torrent is still stopping with Permission denied error, and inside the folder there's no file.

(When the torrent has only 1 file and no folder, it's able to create the file and write on it and download goes on with no error)

The odd thing is that from SSH I'm able to create a file inside the folder, and the file is created with my user:

```
-rw-rw-r--+ 1 hikari              naswrite    0 jan 21 23:11 test.txt
```

I don't really understand why transmission which created the folder is unable to create files inside it and I am.

And SMB issue remains. I'm able to create a folder with its default name "New folder", then Windows shows error dialog for being unable to *rename* the folder it just created! I'm also unable to delete it from SMB, even thou I am from SSH. Its permissions are also odd:

```
drw-r-sr-x+ 2 hikari              naswrite        4096 jan 21 23:13 'New folder'/
```

It must have write permission on group.

Any suggestion?

---

### Post by TheFu on 2021-01-21
u+w is needed on the directories or the owner will be prevented access. There is a hierarchy for permissions. Owner permissions override group permissions which override "other" permissions.

Probably don't want whatever is causing the + is that from xattrs? ACLs are a '.' in that place.

Samba permissions really shouldn't matter, since smbd runs as root. Someone else will need to help with that. Last time I used samba for multiple users was in the 1990s. We used the same group for people with write access. It all worked. 

```
drwxrwsr-x 2 hikari              naswrite
```
is probably what you want for the top directories. Any newly created files or subdirs will inherit that unless an odd umask setting.
Provided the owner is in the naswrite grp, the owner doesn't matter.  You don't need a script to fix things.  Or at least you shouldn't.

"Other" may not need any permissions. Depends on the access goals.

---

### Post by hikariws on 2021-01-21
> **TheFu said:**
> Samba permissions really shouldn't matter, since smbd runs as root. Someone else will need to help with that. Last time I used samba for multiple users was in the 1990s. We used the same group for people with write access. It all worked.

It's not even for multiple users, it's only for me :p

As I understood from what I've been reading, smbd runs as root and sets permission on what it messes based on its settings. I added the following commands and surprisely it seems to be working now!

```
create mask = 0664
directory mask = 0775
force user = hikari
force group = naswrite

```

These commands were on their defaults before. I guess smbd was setting g=rx and that was messing with SMB part. Now it works:

```
drwxrwsr-x+ 2 hikari naswrite 4096 jan 22 00:50 test/
```

Windows provides the folder to be renamed after creation and I'm able to delete it. I didn't do many tests but there was no error msg so far.

> **TheFu said:**
> u+w is needed on the directories or the owner will be prevented access. There is a hierarchy for permissions. Owner permissions override group permissions which override "other" permissions.

Probably don't want whatever is causing the + is that from xattrs? ACLs are a '.' in that place.

Sorry I didn't understand anything u said :/

u+w is being attributed when folder is created:

```
drwxrwsr-x+ 2 debian-transmission naswrite        4096 jan 22 00:58   torrent folder
```

Oddly enought, I went to make another test and it seems to be working now. At least the torrent haven't stopped with error yet.

I was reading [https://www.thegeekdiary.com/how-to-force-user-group-ownership-of-files-on-a-samba-share/](https://www.thegeekdiary.com/how-to-force-user-group-ownership-of-files-on-a-samba-share/). ACL is enabled, but anyway I added it to fstab and remounted it. Then executed this command:

```
setfacl -R -d -m u::rwx,g:naswrite:rwx,o::r-x /nas/raid
```

Maybe it's what made it work.

This is how ACL is now:


```
$ getfacl /nas/raid/
getfacl: Removing leading '/' from absolute path names
# file: nas/raid/
# owner: hikari
# group: naswrite
# flags: -s-
user::rwx
group::r-x
group:naswrite:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:naswrite:rwx
default:mask::rwx
default:other::r-x

```

> **TheFu said:**
> 
```
drwxrwsr-x 2 hikari              naswrite
```
is probably what you want for the top directories. Any newly created files or subdirs will inherit that unless an odd umask setting.
Provided the owner is in the naswrite grp, the owner doesn't matter. You don't need a script to fix things. Or at least you shouldn't.

"Other" may not need any permissions. Depends on the access goals.

Exactly. If group works and user doesn't step on the way, I can ignore user. That's what I was thinking when I first got issues from permission conflicts.

I don't believe all of a sudden all the issues are gone, but I haven't seen any error so far. I'm gonna get back into migrating torrents and make some other migrations too and see if anything goes wrong.

---

### Post by TheFu on 2021-01-22
I've never needed "force user" and have been burned by ACLs a few times over the decades. Avoid both.  ACLs are not needed and the setfacl above is mission the g+s. In one command fr directories:
```
chmod u+rwx,g+rwxs,o+rx  directory-name
```
For data files, **chmod 664** fine, but if a file needs eXecute, it will be removed. The solution is the **chmod +X**. It leaves all existing x perm bits alone., but doesn't add any.

The directory permissions in samba need to include the g+s part. I don't remember the octal for that: 2775 or 4775.

The only reason to force a specific owner is if you need to modify the permissions later and don't want to use sudo. Correct permissions negates that need.

But *perfect* is the enemy of *done*, so stop when you feel done.

If you don't have Windows, this all gets much easier via NFS or just use sftp (winscp or any Linux file manager). I've heard win10 includes NFS support.

---

### Post by hikariws on 2021-01-22
tnx for the tips!

Indeed, I've been migrating some torrents and had no errors yet. It's a very specific procedure, so I still need more use cases to be sure there's nothing wrong. The thing is I have 39TB free and don't wanna rush and mess with it, so first I'm migrating most torrents to then move to other stuff.

The script with find commands wasn't needed anymore too.

Before now I was using BusyBox based commercial NAS, so they use to hide some details and make other stuff troubling. I had tried NFS years ago and was unable to make it work, ever since I'm using SMB even on lix. Maybe now it could work, even more if I could get it working on Win10, but SMB is doing the trick.

Until last year I used Acronis True Image to make partition backups and FTP worked better on it than SMB which used to fail to authenticate. Now I'm using Macrium and only way it has to remote connect is SMB, so I need to keep it anyway. I hope to not need to use FTP ever again.

---

### Post by TheFu on 2021-01-22
Hope you have backups.  That's a bunch of data loss.  I have about 32T of storage, but use only half that so backups can be done. I'd hate to re-rip all that content. I don't torrent.  My NAS/media server doesn't do CIFS/Samba at all, only DLNA and NFS. Standard Unix permissions "just work."

---

