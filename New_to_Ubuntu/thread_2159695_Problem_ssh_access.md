---
title: "Problem ssh access"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by musaka on 2013-07-04
I have a problem with ssh access and I have not idea how fix it.


Long time ago I changed in my external server the ssh option PasswordAuthentication to value no (in the file ssh_confg).
Just three days ago I have lost all data from my local machine and now there aren't no options to access to the server, I can't access with the key because I lost it and with the password I can't because the option in the server say no.


How can I restore the ssh option to no?


Thank in advance.

---

### Post by hamishmb on 2013-07-04
Do you mean to ask how to allow password login again? Do you have physical access to the server? Do you have another computer with the key backed up? 

Thanks,
Hamish

---

### Post by Lars Noodén on 2013-07-04
You'll either need the old key from your backup disks, or another account with an active key and the ability to gain root privileges, or out of band (e.g. physical) access to the server.

For the last two, make a new key pair and use the privileges to copy to your user accounts *authorized_keys* file.

---

