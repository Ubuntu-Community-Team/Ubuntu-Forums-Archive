---
title: "[SOLVED] File and Folder permissions"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by colskinet on 2008-11-28
Hi

I have an Ubuntu 8.10 server that I have setup (Server so no GUI) and have a few users connecting to it.

I have some mount points such as /CPdata, /NBBdata and /Engmisc.

I have setup Samba permissions fine so that only certain people can access certain files/folders, but when using Filezilla to transfer files a user that shouldn't have access to /CPdata for example can perfectly view the contents inside the folder.

How do I go about locking this down?

Thanks in advance.

Colin

---

### Post by bhadotia on 2008-11-28
> **colskinet said:**
> Hi

I have an Ubuntu 8.10 server that I have setup (Server so no GUI) and have a few users connecting to it.

I have some mount points such as /CPdata, /NBBdata and /Engmisc.

I have setup Samba permissions fine so that only certain people can access certain files/folders, but when using Filezilla to transfer files a user that shouldn't have access to /CPdata for example can perfectly view the contents inside the folder.

How do I go about locking this down?

Thanks in advance.

Colin

Use the chmod command. Type:
```
man chmod
```
for a manual on chmod. [Here]("http://linuxcommand.org/lts0070.php") is some more clear explanation regarding permissions and chmod.

---

### Post by eder.apt-get on 2008-11-28
Chmod will affect all users in your network. If I got i right, you could use smb.conf in order to say who can and who can´t access a samba share, using parameters such as valid users, invalid users, read list, etc. You can find more informations here:
[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

---

### Post by bhadotia on 2008-11-28
> **eder.apt-get said:**
> Chmod will affect all users in your network. If I got i right, you could use smb.conf in order to say who can and who can´t access a samba share, using parameters such as valid users, invalid users, read list, etc. You can find more informations here:
[http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html](http://www.cyberciti.biz/tips/how-do-i-set-permissions-to-samba-shares.html)

Oh yes,chmod will effect all the users on your system. 
Follow eder.apt-get's solution if that suites you more.

---

### Post by colskinet on 2008-11-28
Thanks guys, got it sorted now with the help of your links.

:guitar::popcorn:

---

### Post by ||Z0di4C|| on 2008-12-02
ironically i had the same problem so thanks to everyone that helped cause u helped me too

---

