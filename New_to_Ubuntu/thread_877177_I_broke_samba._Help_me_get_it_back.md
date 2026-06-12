---
title: "I broke samba. Help me get it back"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by geokok1981 on 2008-08-01
I noticed that my shares were not shared anymore, for some reason. 
So i decided to install samba again. I did this:

sudo apt-get remove samba
sudo rm -rf /etc/samba
sudo apt-get install samba

On step 3 however I get an error message that says more or less (translated):

```
Decompressing samba (&#945;&#960;&#972; .../samba_3.0.28a-1ubuntu4.4_i386.deb) ...
Installing samba-common (3.0.28a-1ubuntu4.4) ...
Not replacing deleted config file /etc/samba/smb.conf
chmod: cannot access `/etc/samba/smb.conf': No such file or directory
dpkg: error editing samba-common (--configure):
 sub-proccess post-installation script returned error state 1
dpkg: dependency problems dont allow adjusting libpam-smbpass:
 libpam-smbpass depends on samba-common (= 3.0.28a-1ubuntu4.4). However:
  Package samba-common is not configured yet.
dpkg: error in proccessing libpam-smbpass (--configure):
 dependency problems - left unconfigured
dpkg: dependency problems dont allow adjusting samba:
 samba depends on samba-common (= 3.0.28a-1ubuntu4.4). However:
  Package samba-common is not configured yet.
dpkg: error proccessing samba (--configure):
 dependency problems - left unconfigured
Errors while processing:
 samba-common
 libpam-smbpass
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I also tried dpkg --remove --purge samba but no luck

PLease, help......

---

### Post by geokok1981 on 2008-08-01
Sorry to ask again but u really want to avoid formatting...
Anyone?

---

### Post by dca on 2008-08-01
Rename your /etc/samba/smb.conf as something else for now
 
issue */etc/init.d/samba stop*  
command at CLI to make sure service is stopped prior to removal.

---

### Post by dca on 2008-08-01
Is this similar to your issue?
 
[http://ubuntuforums.org/showthread.php?p=5387695](http://ubuntuforums.org/showthread.php?p=5387695)

---

### Post by geokok1981 on 2008-08-01
Awesome! Thanks. The link u provided did just the thing!!

However smb.conf is completely blank!!!I thought than when I shared a folder using nautilus 
sharing options it would add that share there. But nothing appears on the smb.conf file....hmmm

---

### Post by dca on 2008-08-01
The only thing I can tell you is when using Samba I only used it on Ubuntu's server version where all the shares were added manually to the smb.conf file using [sharename] and then its context below.  If you need a spare smb.conf file you should be able to google and find a generic one you can add the shares to.
 
Just remember the smbpasswd -a username
then smbpasswd -e username
 
for adding different user access to your shares -a = add, -e = enable
 
For most changes share adds, users, you have to restart the samba service for those changes to take affect so that way Samba has to re-read the smb.conf file again...

---

