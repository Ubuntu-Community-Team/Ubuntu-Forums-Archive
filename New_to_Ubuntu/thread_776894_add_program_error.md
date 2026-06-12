---
title: "add program error"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by IncadudeF on 2008-05-01
first time ubuntu user

I get this error when trying to install programs:

```
incadude@incadude-laptop:~$ sudo apt-get update
[sudo] password for incadude: 
Err http://us.archive.ubuntu.com hardy Release.gpg                             
  Could not connect to us.archive.ubuntu.com:80 (91.189.92.3), connection timed out
Err http://security.ubuntu.com hardy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out
Err http://security.ubuntu.com hardy-security/main Translation-en_US           
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US     
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/universe Translation-en_US       
  Unable to connect to security.ubuntu.com http:
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
  Unable to connect to security.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy/main Translation-en_US                  
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Unable to connect to us.archive.ubuntu.com http:
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Unable to connect to us.archive.ubuntu.com http:
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (91.189.92.3), connection timed out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to us.archive.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (91.189.88.37), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to security.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

I cant install anything!!!

---

### Post by IncadudeF on 2008-05-01
*bump*

---

### Post by Aelfric5578 on 2008-05-01
Stupid question, but are you sure you have a working internet connection?  Alternatively are you behind an improperly configured firewall?  It doesn't seem like you can't install anything as much as you can't download anything to install.

---

### Post by IncadudeF on 2008-05-01
im able to connect to the internet using firefox. But i cant download any packages using the Synaptic Package manager. Im trying to download the virtualbox and an irc chat client.

---

### Post by TeoBigusGeekus on 2008-05-01
Perhaps the servers are jammed. Try again later...
The whole (Ubuntu) world is downloading, installing and fixing Hardy Heron these days. Maybe patience is all you need...

---

### Post by IncadudeF on 2008-05-01
ok i did the select best server and it gave me a new zealand one. lol

Everything works fine now.

---

