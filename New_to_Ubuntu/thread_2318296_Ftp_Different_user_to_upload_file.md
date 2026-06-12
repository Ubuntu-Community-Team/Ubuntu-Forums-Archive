---
title: "Ftp Different user to upload file"
date: 2016-03-24
forum: New to Ubuntu
---

### Post by abaki on 2016-03-24
hi guys;

i installed vsftpd and configured SFTP. 
i have a standart user who is name lets say user1 with all perms. i dont want to give the password to my friend.i only want him to access a spesific directory to upload file so server can run those files. file place is : /home/user1/upload
i create a user w/o a no shell login named user1ftp. Changed the user home location to /home/user1/upload so when he log in he directly to log in the upload file. he can upload and delete files in it. problem is that when he upload a file server cannot run it. his files permisson is : rw-r--r-- so i need that when he upload a file perms should be rwxrwxr-x

how can i do that

---

### Post by TheFu on 2016-03-24
Use the sftp that is part of openssh-server package, not vsftp.  Then the userid's umask will control it. 
BTW, I consider this very dangerous to allow a userid you don't trust enough to give full ssh access, but want to allow execute?
The short answer is that sftp supports the chmod command, just like plain FTP. sftp was designed to be backwards compatible with plain FTP (which NOBODY should be using since 2002, IMHO).
You could also write a script that changes the permissions on the files placed in the upload directory owned by user1.

[https://serverfault.com/questions/639042/does-openssh-sftp-server-use-umask-or-preserve-client-side-permissions-after-put](https://serverfault.com/questions/639042/does-openssh-sftp-server-use-umask-or-preserve-client-side-permissions-after-put) has the setting for the /etc/ssh/ssh_config file. 

I never understood why people still use vsftp for this stuff. Perhaps someone could explain it?

---

### Post by abaki on 2016-03-24
> **TheFu said:**
> Use the sftp that is part of openssh-server package, not vsftp.  Then the userid's umask will control it. 
BTW, I consider this very dangerous to allow a userid you don't trust enough to give full ssh access, but want to allow execute?
The short answer is that sftp supports the chmod command, just like plain FTP. sftp was designed to be backwards compatible with plain FTP (which NOBODY should be using since 2002, IMHO).
You could also write a script that changes the permissions on the files placed in the upload directory owned by user1.

[https://serverfault.com/questions/639042/does-openssh-sftp-server-use-umask-or-preserve-client-side-permissions-after-put](https://serverfault.com/questions/639042/does-openssh-sftp-server-use-umask-or-preserve-client-side-permissions-after-put) has the setting for the /etc/ssh/ssh_config file. 

I never understood why people still use vsftp for this stuff. Perhaps someone could explain it?

i first installed vsftp later sftp on the server. when i login ftp with user1 and upload file umask control its perms but situation is different with user1ftp. i couldnt find any way to change files perms which uploaded by user1ftp.

i am really new to linux so try different things to learn the system. 

i dont want to give full ssh access to user but i want to give its files to be executed by main user not root. i might revoke main user sudo privilege too.

i will try these things and learn. most of them will be wrong but i need to find right. so bare me and help me guys. appreciated your helps. thanks.

---

### Post by TheFu on 2016-03-24
We were all new at some point.  The learning curve is much less these days than when I started, but it is still steep.
My best advice for people wanting to learn linux: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)

Remove vsftp. You don't want that left on the box.

Be certain that you fully understand file and directory permissions. This is the corner-stone for all Linux security - that is different than other OSes you've probably used.

Also, know that there are 500 solutions for what you are asking. Each with good and bad aspects.  The way that I'd do it is 
* load openssh-server
* enable on sftp access for the userid
* set the umask as needed - I wouldn't make it executable permissions for security reasons (too many to list).
* setup a cron task daily or hourly or every 15 minutes to move any uploaded files to a place that the upload userid cannot see, chmod +x the files in the new directory.  Don't leave executable files anywhere that untrusted FTP/sftp users can see or access.

If nobody as mentioned this, there is a help system on your linux machine already - man pages or manpages.  Almost every program and config file has a manpage which describes the settings and options for control.  man ssh_config will show the options to control the umask, if you insist on doing it that way.  Again, I wouldn't, but it is your box.

BTW, there is also a manpage for the sftp-server ... which says something about chmod. [http://linuxcommand.org/man_pages/sftp1.html](http://linuxcommand.org/man_pages/sftp1.html) or just look on your box.

---

### Post by bab1 on 2016-03-24
> **abaki said:**
> i first installed vsftp later sftp on the server. when i login ftp with user1 and upload file umask control its perms but situation is different with user1ftp. i couldnt find any way to change files perms which uploaded by user1ftp.

i am really new to linux so try different things to learn the system. 

i dont want to give full ssh access to user but i want to give its files to be executed by main user not root. i might revoke main user sudo privilege too.

i will try these things and learn. most of them will be wrong but i need to find right. so bare me and help me guys. appreciated your helps. thanks.
As @The Fu says; you should not keep files that need to be accessible by multiple users in your home directory.  You can create a directory that is accessible by both users (e.g. /data).  

The proper way to set the access for both users to be able to use each others files is to use a user group the both users are added to.  If you set the SGID (set group ID) bit on that directory, all files and directories will be created with that user group and all users will have rw access.

A word about this: *"i am really new to linux so try different things to learn the system."*.  Not all things are obvious.  The system is flexible enough that you can create serious security issues or render the system inoperable.  All of this without any warning to you.  Just because you can do something doesn't mean you should do it.  I recommend you read about how the system works before modifying it.  Of course you can always ask questions on this forum too.  ;-)

---

### Post by abaki on 2016-03-24
@[B]bab1 ;
[/B]
my both users user1 and user1ftp are member of the ftpaccess group. directory home/user1/upload owner is user1 and gorup is ftpaccess. user1ftp uploads a file inside the upload directory and new file gets the rw-r--r--
how can i set SGID and make user1ftp files get the group write perms. 

i will delete vsftp and follow the guide that @TheFu gave. thanks.

---

### Post by bab1 on 2016-03-24
> **abaki said:**
> @**bab1 ;**
my both users user1 and user1ftp are member of the ftpaccess group. directory home/user1/upload owner is user1 and gorup is ftpaccess. 

I'm sure you mean the directory /home/suer1/upload.  The directory already has the group ownership by ftpaccess.
> 
user1ftp uploads a file inside the upload directory and new file gets the rw-r--r--

This is not the default umask for Ubuntu.  Are you using Ubuntu as the OS?  I don't use vsftp for the same reasons ad @TheFu.  Maybe vsftp changes the umask.
> 
how can i set SGID and make user1ftp files get the group write perms. 

The SGID bit does nothing for file and directory permissions.  It insures that any file of directory created always has the intended user group ownership.  The permissions are always set by umask.
> 
I will delete vsftp and follow the guide that @TheFu gave. thanks.
Okay.

---

### Post by abaki on 2016-03-25
thanks.

i learn a lot about linux gropus and permission system. 

i have another question is there any way to give a executable x  permission to a new file when a user upload the file with SFTP?

---

