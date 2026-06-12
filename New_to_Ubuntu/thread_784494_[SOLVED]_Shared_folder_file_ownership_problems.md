---
title: "[SOLVED] Shared folder file ownership problems"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by movrshakr on 2008-05-06
Let me describe as succinctly as I can...

Folder on ubuntu Gutsy machine is shared.  Windows XP and Vista machines on the local network create, read and write files to/in that folder.  All works well.

What doesn't work well is if I go to that Gutsy machine and log on there, it is difficult to work with files stored there by the Windows machine.  I can open them (say, in gedit), but cannot save changes back into the same file name.

The reason is that the group/owner of the files created by other machines are set to "nogroup nobody."  Does anybody know a way to set this up so I can work with the files AT the Gutsy machine without having to do chown commands on the files.

---

### Post by JudasReanimated on 2008-05-06
```
sudo chgrp "your user's group here"
```

```
sudo chown "Your username here"
```

---

### Post by bodhi.zazen on 2008-05-06
You can look at configuring samba, may be as easy as adding your Gutsy user to samba, and logging in as the user.

You can also set the new folder / directory permissions with a mask

(put this in the share)

create mask = 0664
directory mask = 0775


Or you can try adding your Gutsy user to the nobody group.

---

### Post by movrshakr on 2008-05-06
I like the idea of adding my Gutsy login username to the group, but wouldn't it be the 'nogroup' group ('nobody' is a username)?  Will try that.

Don't understand (not advanced enough) the: 
--------------
You can also set the new folder / directory permissions with a mask (put this in the share)

create mask = 0664
directory mask = 0775
-------------------------
Nor understand what I would change in samba to solve it.

---

### Post by bodhi.zazen on 2008-05-06
Sorry, I was referring to manually editing your samba config file. /etc/samba/smb.config

See this link : 

[SettingUpSamba - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SettingUpSamba") 

First try adding your user to samba on the server.

```
sudo groupadd samba
sudo adduser user samba
```

Where "user" = your user name on the samba server.

Next, try adding your nogroup

Last further edit /etc/samba/smb.conf as needed.

---

### Post by movrshakr on 2008-05-19
SOLVED
OK, I have it working now.

Putting the user name into the 'nogroup' group did not work.

Putting
```
create mask = 0664
directory mask = 0775
```
into the share definition section of /etc/samba/smb.conf did work.

---

