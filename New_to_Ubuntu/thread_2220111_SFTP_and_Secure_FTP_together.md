---
title: "SFTP and Secure FTP together"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by antony7 on 2014-04-26
Hi Folks,

I've finally got SFTP and FTP (with forced SSL) working (pretty much) except although I can FTP to the folder I cannot actually upload or delete any files.

I have done quite a bit of playing around with permissions having used [http://www.sigerr.org/linux/setup-vsftpd-custom-multiple-directories-users-accounts-ubuntu-step-by-step/](http://www.sigerr.org/linux/setup-vsftpd-custom-multiple-directories-users-accounts-ubuntu-step-by-step/) to set the FTP up.

User permissions:

/var/www = 755 root:root
/var/www/user = 555 root:remotefileaccess
/var/www/user/www = 755 user(SFTP user **not** FTP user):remotefileaccess (contains vsftpd user as member)

Remotefileaccess contains a user called vsftp who is then configured in the vsftpd settings and as far as I can see this should all work. **I have tried** to change permissions to 770 for /var/www/user/www because I can see that group permissions would need execute but that didn't seem to work.

Any ideas?

Thanks

Antony

---

