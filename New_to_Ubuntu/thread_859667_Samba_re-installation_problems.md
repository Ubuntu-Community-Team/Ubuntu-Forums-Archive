---
title: "Samba re-installation problems"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Cr85bro13 on 2008-07-14
I had Samba installed on a server box I put in the basement. It is a headless machine running Ubuntu 8.04 Server Edition with no GUI. I manage it through SSH. Samba was installed, and I tried using SWAT to configure it, but after a while I decided I wanted a clean install because I would rather edit the configuration file directly without SWAT. The uninstall went fine. When I tried to reinstall, it throws this error: 
```
kenny@bserver:~$ sudo apt-get install samba
[sudo] password for kenny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  samba-common
Suggested packages:
  openbsd-inetd inet-superserver smbldap-tools
The following NEW packages will be installed:
  samba samba-common
0 upgraded, 2 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B/6678kB of archives.
After this operation, 16.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package samba-common.
(Reading database ... 29443 files and directories currently installed.)
Unpacking samba-common (from .../samba-common_3.0.28a-1ubuntu4.4_i386.deb) ...
Selecting previously deselected package samba.
Unpacking samba (from .../samba_3.0.28a-1ubuntu4.4_i386.deb) ...
Setting up samba-common (3.0.28a-1ubuntu4.4) ...
Not replacing deleted config file /etc/samba/smb.conf
chmod: cannot access `/etc/samba/smb.conf': No such file or directory
dpkg: error processing samba-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 3.0.28a-1ubuntu4.4); however:
  Package samba-common is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba-common
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Can anybody please help me? Thank you.

---

### Post by ChameleonDave on 2008-07-14
It seems to be complaining that "/etc/samba/smb.conf" does not exist.  It is expecting it to be there, and is choking on that.  Silly, I know.

Here is a hack that might work.

Go to the terminal and do this:

```

sudo touch /etc/samba/smb.conf

```

Then try again.

---

### Post by Cr85bro13 on 2008-07-15
Seemed to work. Thanks alot for the help. Would you happen to know why smb.conf was not being created? If I was doing a complete reinstall of Samba, shouldn't it just recreate everything?

---

### Post by phpcitizen on 2008-08-28
It worked. Thanks a lot.

---

