---
title: "Synaptic Package Reload Failure"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by edwardLS on 2008-08-08
I am just about to switch to Ubuntu Hardy and drop that other OS.  I have Hardy running and doing just about everything that I need/want.  However, I have a minor annoyance that I would like to resolve and/or understand.

When I start Synaptic Package Manager and then click Reload to download the package information there is several "Failed" downloads where the "Package" is always listed as 'Translation-en_US'. This had always failed since I have installed Hardy.

My system seems to suffer no ill effect.  So what is this, and is there a way that I can delete the attempt to download it, or is that not a good idea.

---

### Post by iaculallad on 2008-08-08
Post whatever message/error message is displayed when you issue the command below on your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by edwardLS on 2008-08-08
Here is the output:

```
edward@ed-laptop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for edward: 
Hit http://security.ubuntu.com hardy-security Release.gpg                   
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
edward@ed-laptop:~$ 

```

---

### Post by iaculallad on 2008-08-08
No problem so far. Navigate to System->Administration->Software Sources, Try changing the "Download From:" to "Main Server". Click on Close, click on Reload on the next window that pops up.

---

### Post by edwardLS on 2008-08-08
I did as you suggested, and I still get the same problem in Synaptic Package Manager as originally described.

---

