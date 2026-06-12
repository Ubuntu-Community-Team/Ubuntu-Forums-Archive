---
title: "Changing write permissions for jailed SFTP denies login"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by onggie on 2013-04-12
I have scouted over many websites and forums on how to setup an SFTP user that is jailed to a certain directory using CHROOT.  Here are the steps I have followed but I can't seem to get write permissions to work.

Setup

**sshd_config**
```

#Subsystem sftp /usr/lib/openssh/sftp-server
Subsystem sftp internal-sftp


Match group webmaster
        X11Forwarding no
        ChrootDirectory %h
        AllowTcpForwarding no
        ForceCommand internal-sftp

```

**Create Folder**
```

mkdir /var/www/sites

```
[B]
Create User and Group[/B]
```

useradd uploader
passwd uploader
usermod -d /var/www/sites uploader
groupadd webmaster uploader
groupadd www-data uploader

```

**Permissions and Ownership**
```

chown root:root /var/www
chmod 755 /var/www/sites

```

Now with these settings the user uploader is able to SFTP into the home directory but is unable to write to the directory.

There are 2 typical errors that occur, I either can't login or I don't have write permissions.  

**Login Error**
```

Error:    Network error: Software caused connection abort
Error:    Could not connect to server

```


[LIST]
[*]Changing permissions of /var/www/sites to 775 or 777 causes login error. 
[*]chown /var/www/sites to uploader:root causes login error. 
[*]chwon root:webmaster or root:www-data I have no write permissions 
[/LIST]

I am at odds end trying to figure this out and if anyone could point me into the right direction I would be greatly appreciate it.

Thank you.

---

### Post by onggie on 2013-04-13
Ok found out the solution to this, I hope it helps some people out.

The user is jailed to /var/www/sites. I then created another folder /var/www/sites/site1.  I chown root:webmaster /var/www/sites/site1 as well as chmod 775 /var/www/sites/site1 .  This enabled the home directory to have the correct permissions to login and then be able to write to the next folder up.

If the user needs write access to /var/www/sites, then you must jail the user at /var/www which has root:root ownership and permissions of 755.  You then need to give /var/www/sites ownership of root: (your group) and permissions of 775.

---

