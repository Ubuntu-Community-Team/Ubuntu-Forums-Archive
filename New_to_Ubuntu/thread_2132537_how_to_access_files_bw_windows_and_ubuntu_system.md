---
title: "how to access files b/w windows and ubuntu system"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by manjusun on 2013-04-05
Hi All,
I have my ubuntu laptop and windows xp desktop over wifi, I want to access complete file system of one machine from another. Basically need to copy few files b/w system and keep them sync.

I have done this b/w 2 machines which were windows just by typing ip address in windows explorer and did access the files in them. 

Ubuntu is new to me and need some help to achieve the same.

-Thanks & regards,
Manju

---

### Post by slickymaster on 2013-04-05
An easy solution is to use Samba and set up a CIFS (Common Internet File System) server on your Linux machine.

---

### Post by manjusun on 2013-04-05
Hi,
Thanks for your reply, can you provide me some pointers how to install samba in detail
I did tried,
[https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html](https://help.ubuntu.com/10.04/serverguide/samba-ad-integration.html)

but couldnot access complete file system from windows,
when connected from windows explorer for my unbuntu system with its local ip, I could see only one folder  "Printers and Faxes"

but the other way is not even possible to connect from ubuntu to windows from file explorer

-regards,
Manju

---

### Post by nerdtron on 2013-04-05
Try this one [http://compnetworking.about.com/od/softwareapplicationstools/l/aa062499.htm](http://compnetworking.about.com/od/softwareapplicationstools/l/aa062499.htm)
and this one [http://archive09.linux.com/whatislinux/118625](http://archive09.linux.com/whatislinux/118625)

---

### Post by slickymaster on 2013-04-05
The two links nerdtron provided you seem to be a good place to start.

Basically you install a recent copy of [Samba]("http://www.samba.org"), find the Samba configuration file, usually **/etc/samba/smb.conf**. The configuration file is split in two: global settings and share definitions. The global settings control how the CIFS server works and can be used to control anything - from what interface the server listens on, to Windows Active Directory domain controller settings. The out-of-the-box global settings will be sufficient. Set up a share for your files. Let's say that the files exist on the filesystem as /export/share. You will need a CIFS share name and description, which you can call myshare' and 'all my files', for example.
Suppose you want other users on your wireless network to also access the share, you'll want to lock down this share so that only them, besides you, can access the share, giving them read and write access.
Add the following to the smb.conf:
```
[myshare]
comment = all my files
path = /export/share
valid users = user1 user2
public = no
writable = yes
printable = no
create mask = 0765
```
Finally add authentication credentials for user1 and user1. To do this, use smbpasswd as root:
```
smbpasswd -a user1 New SMB password:
smbpasswd -a user2 New SMB password:
```

---

