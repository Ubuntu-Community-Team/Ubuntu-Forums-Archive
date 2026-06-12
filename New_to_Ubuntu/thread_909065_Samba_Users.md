---
title: "Samba Users"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by fixit on 2008-09-03
Hello. I'm trying to install and configure Samba server on an Ubuntu 8.04 machine and want to allow some Ubuntu and some Vista computers to log in.
I've read a lot of posts and tutorials how to add users and to manage users authentication but I still can't understand some things.
The following line is very frustrating "Samba will expect both the client and the server user to have the same password.". What does this mean?
I've added Linux user called user1 with password user1pass and then added Samba user (sudo smbpasswd -L -a user1) with the same password.
A friend of mine tried to connect from a Vista machine where he is logged as user1 but with different password. When he was prompted for a password (from the Samba server) he entered user1pass but he wasn't allowed to login. When he changed his local(Vista) password to user1pass he entered in the Samba server without being prompted for a password.
Does this mean that I have to know his password in order to allow him to view my shares?!?

How I have to configure my Samba server so everybody who knows the user and the password to log in and to have access to my shares?

Thanks!

---

### Post by Nepherte on 2008-09-03
I think that samba by default tries to use the user name & password of the local computer. You shouldn't have to know the password of that local computer though. You probably forgot to restart the samba service or the -L option gives an unwanted effect. This is how I always add users:

1. Make a user on the samba server (without a shell, so he won't be able to login to the samba server itself) and give him a password:
```
sudo useradd -s /bin/false user1
sudo passwd user1
```

2. I always add the user to a samba group:
```
sudo groupadd smbshares
sudo usermod -a -G smbshares user1
```

3. Add the user to the smb authentication file and enable the user:
```
sudo smbpasswd -a user1
sudo passwd -e user1
```


4. Restart the samba service:
```
sudo /etc/init.d/samba restart
```

---

### Post by fixit on 2008-09-03
Thanks Nepherte!

I think I found my problem. It was because I've used username map file. I removed the mappings from this file and then it was possible to log in as whom user you want.

---

