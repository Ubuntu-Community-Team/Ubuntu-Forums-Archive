---
title: "Failed to add new user"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by penasjr on 2012-06-28
I am setting a samba server for the first time.

I could not create a user because I am getting this message :

sudo smbpasswd -a netadd
password for mrp      ,------- ok i enter my password here
New SMB password    ------- i assign a password
retyrpe new SMB password ----- ok i retype
Failed to add entry for user netadd

Any body can help me pls...

---

### Post by penasjr on 2012-06-28
"failed to add new user"

This is the message I get when I attempted to add a new samba user with
the command line:

sudo smbpasswd -a  netadd

where 'netadd'  is supposed to be the new user i would like to add.

Pls help ..... I am just starting to setup samba on a newly installed ubuntu 12.4

---

### Post by bab1 on 2012-06-28
> **penasjr said:**
> "failed to add new user"

This is the message I get when I attempted to add a new samba user with
the command line:

sudo smbpasswd -a  netadd

where 'netadd'  is supposed to be the new user i would like to add.

Pls help ..... I am just starting to setup samba on a newly installed ubuntu 12.4

Does this user have an Ubuntu login account?  What does this show ```
getent passwd|grep <Ubuntu_user> 
```

Does a Samba user database exist?  What do you get with this```
sudo pdbedit -L
```

---

### Post by cariboo on 2012-06-29
Please don't create multiple threads on the same subject, I've merged your two threads.

---

