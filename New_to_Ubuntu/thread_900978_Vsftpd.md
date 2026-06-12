---
title: "Vsftpd"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Drezard on 2008-08-25
I have 2 users on my computer, one which was installed by default: main_account and one which was created using the command (useradd -d /var/public -s /bin/false ftp_user). I have uncommented 'local_enable=YES' in vsftpd.conf. 

Now, heres where my problem is. main_account can login but ftp_user cannot. 

What have I done wrong?

Daniel

---

### Post by aloshbennett on 2008-08-26
The basic check:
Does /var/public exist and does the ftp_user has access on it?

---

### Post by Drezard on 2008-08-26
All users have rwx permissions to that directory.

---

### Post by aloshbennett on 2008-08-26
Two other things:
1. ftp_user is not a valid name because of the underscore.
2. reset the password for the user

---

