---
title: "Can't create samba users with smbpasswd"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by wardjame on 2008-06-24
Hi all,
I'm trying to get my ubuntu machine working as a simple file server.  I was able to add one samba user, the same one that I was logged into the machine as but I can not seem to add any additional users.  If I am understanding the forum threads I have read here it should be possible for me to create samba users that are not system users with the smbpasswd command.

Here is what happens when I try to add a user called test:
smbpasswd -a test
New SMB password:
Retype new SMB password:
Failed to modify password entry for user test

The error here is a little vague.  Do I have to modify the smb.conf to get this to work?  Do I have to create a system user for every samba user?  Any help would be much appreciated.

---

### Post by PinkFloyd102489 on 2008-06-24
Use sudo.

---

### Post by wardjame on 2008-06-24
I was logged in as root when I issued the smbpasswd command.  Any other possibilities?

---

### Post by wardjame on 2008-07-01
Is there no solution to this?  I guess I will have to create system users in order to create samba users?

---

### Post by sisco311 on 2008-07-01
Yes, you need to create a system user first.
```
sudo useradd *USERNAME* --shell /bin/false
```
will create a new user with a disabled account and without home directory.

---

### Post by superprash2003 on 2008-07-01
right..you can add a samba user only if he is a system user..

---

### Post by Krupski on 2008-07-01
> **wardjame said:**
> Hi all,
I'm trying to get my ubuntu machine working as a simple file server.  I was able to add one samba user, the same one that I was logged into the machine as but I can not seem to add any additional users.  If I am understanding the forum threads I have read here it should be possible for me to create samba users that are not system users with the smbpasswd command.

Here is what happens when I try to add a user called test:
smbpasswd -a test
New SMB password:
Retype new SMB password:
Failed to modify password entry for user test

The error here is a little vague.  Do I have to modify the smb.conf to get this to work?  Do I have to create a system user for every samba user?  Any help would be much appreciated.

I'm using Ubuntu 8.04 64 bit server and SAMBA as a file server.

Here's what I do to create and authorize each user of the SAMBA shares:

In, for example, the /home directory... to add a user called "mikek":

(1) mkdir mikek
(2) useradd -d /home/mikek -s /bin/false -r mikek
(3) passwd mikek (then enter new UNIX password twice)
(4) smbpasswd -a mikek (then enter new SMB password twice)
(5) chown mikek mikek
(6) chgrp users mikek

Repeat for each user you wish to add to SAMBA.

Good luck!

-- Roger

(edit to add):

Whoops! Forgot to mention that you have to be root to do the above, so either use "sudo" or log in as root. Sorry.

-- Roger

---

