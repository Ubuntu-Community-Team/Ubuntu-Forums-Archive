---
title: "FTP Permisions"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by hawk007 on 2012-09-14
Hi, i installed ubuntu, installed LAMP, i can view the IT WORKS page ok using 192.168.1.7 (internal static).

I changed the ftp /home/ftp default vsftpd directory to:
/var/www which is where i want to upload a site to via ftp.

I can logon to the ftp server using a username specified in vsftpd.chroot_list (ive allowed local users)using the system password.

This still opens the original user directory but i can back out of that directory and see root, var etc.

I can then navigate to the var/www folder that i want to upload to via filezilla

The problem is what i cant do:

I cant upload or write to that folder even if i change permissions from 755 to 777, they just revert back to the 755 permissions.

What do i need to do to upload a site to that directory?

Thanks for listening

UUBUNTU 10.04.4

---

