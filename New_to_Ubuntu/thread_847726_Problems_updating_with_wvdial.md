---
title: "Problems updating with wvdial"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Natsuko640 on 2008-07-02
I'm stuck with dial-up for the time being and just got a connection with wvdial. My problem is that when I use Add/Remove, Upgrade Manager, Synaptic and apt-get the connection always fails. I can get on FireFox with the connection, but I can't download anything via Ubuntu's system tools. Any help is appreciated.

---

### Post by spiderbatdad on 2008-07-02
have you tried launching wvdial from a terminal as root?
```
sudo wvdial
```

---

### Post by Natsuko640 on 2008-07-02
Oh, no, I'm connected. My problem is trying to update or download a program from Add/Remove. Sorry if I was confusing.

---

### Post by spiderbatdad on 2008-07-02
if you run update from a terminal, you should be able to copy/paste the errors here.

```
sudo apt-get update
```

---

### Post by Natsuko640 on 2008-07-02
```
Err http://apt.wicd.net hardy Release.gpg                                                                                                                         
  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out
Err http://apt.wicd.net hardy/extras Translation-en_US                                                                                                            
  Unable to connect to 172.16.0.9 80:
Err http://archive.canonical.com hardy Release.gpg                                                                                                                
  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out
Err http://archive.canonical.com hardy/partner Translation-en_US                                                          
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy Release.gpg                                                                        
  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out
Err http://us.archive.ubuntu.com hardy/main Translation-en_US                     
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US               
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US                 
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US               
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy-updates Release.gpg                        
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US             
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US       
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US         
  Unable to connect to 172.16.0.9 80:
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
  Unable to connect to 172.16.0.9 80:
Err http://security.ubuntu.com hardy-security Release.gpg                         
  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Unable to connect to 172.16.0.9 80:
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Unable to connect to 172.16.0.9 80:
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Unable to connect to 172.16.0.9 80:
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US
  Unable to connect to 172.16.0.9 80:
Reading package lists... Done             
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Failed to fetch http://apt.wicd.net/dists/hardy/Release.gpg  Could not connect to 172.16.0.9:80 (172.16.0.9), connection timed out

W: Failed to fetch http://apt.wicd.net/dists/hardy/extras/i18n/Translation-en_US.bz2  Unable to connect to 172.16.0.9 80:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```


What confuses me is the IP that's listed. I know that it's my school's proxy, but I never brought my laptop to my school.

---

