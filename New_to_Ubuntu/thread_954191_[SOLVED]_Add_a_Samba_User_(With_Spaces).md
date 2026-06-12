---
title: "[SOLVED] Add a Samba User (With Spaces)"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-20
How can I add a samba user with spaces?

i.e. "John Smith"

When I try and add a user with spaces I get:
```
$ sudo adduser "John Smith"
adduser: To avoid problems, the username should consist only of
letters, digits, underscores, periods, at signs and dashes, and not start with
a dash (as defined by IEEE Std 1003.1-2001). For compatibility with Samba
machine accounts $ is also supported at the end of the username

```
or
```
$ sudo useradd "John Smith"
useradd: invalid user name 'John Smith'
```
or
```
$ sudo smbpasswd -a "John Smith"
New SMB password:
Retype new SMB password:
Failed to modify password entry for user John Smith
```
:(

So if I have a winXP machine that I am trying to share with that has a username with a space, I can't ???

---

### Post by spiderbatdad on 2008-10-20
i believe this is configured in your /smbusers file, where the user's name is quoted...it will get mapped to the linux account as John.```
John = "John Smith"
```
Check:```
man smb.conf
```

---

### Post by BassKozz on 2008-10-20
Thanks...
For others see: 
[http://www.sysop.ca/?p=54](http://www.sysop.ca/?p=54)
[http://lists.samba.org/archive/samba/2003-February/062602.html](http://lists.samba.org/archive/samba/2003-February/062602.html)

---

