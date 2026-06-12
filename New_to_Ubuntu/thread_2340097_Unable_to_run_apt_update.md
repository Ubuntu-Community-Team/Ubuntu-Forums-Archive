---
title: "Unable to run apt update"
date: 2016-10-15
forum: New to Ubuntu
---

### Post by MadleSs on 2016-10-15
Hey guys, 
When I run apt update I'm getting following error 
```
sudo apt update
Hit:1 http://sk.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://sk.archive.ubuntu.com/ubuntu xenial-updates InRelease                       
Hit:3 http://sk.archive.ubuntu.com/ubuntu xenial-backports InRelease                     
Ign:4 http://download.opensuse.org/repositories/home:/jgeboski/xUbuntu_16.04  InRelease  
Ign:5 http://dl.google.com/linux/chrome/deb stable InRelease                             
Hit:6 http://download.opensuse.org/repositories/home:/jgeboski/xUbuntu_16.04  Release    
Ign:7 http://ppa.launchpad.net/attente/modifier-only-input-switch/ubuntu xenial InRelease
Hit:8 http://ppa.launchpad.net/noobslab/themes/ubuntu xenial InRelease                   
Hit:9 http://dl.google.com/linux/chrome/deb stable Release                               
Hit:10 http://ppa.launchpad.net/ricotz/testing/ubuntu xenial InRelease                   
Get:11 http://security.ubuntu.com/ubuntu xenial-security InRelease [94,5 kB]             
Err:12 http://ppa.launchpad.net/attente/modifier-only-input-switch/ubuntu xenial Release 
  404  Not Found
Hit:13 http://us.archive.ubuntu.com/ubuntu xenial InRelease                              
Reading package lists... Done                                                       
E: The repository 'http://ppa.launchpad.net/attente/modifier-only-input-switch/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

anyone knows how to fix this? 
Thank you

---

### Post by howefield on 2016-10-15
What is it that you use the attente/modifier-only-input-switch ppa for ?

It is non existent for Xenial in other words, you are querying a repository that isn't there, so it is bound to error.

What is the output of..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by MadleSs on 2016-10-15
Here's the output of the command:
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ xenial main restricted
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ xenial universe
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ xenial-updates universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu xenial main universe
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ xenial multiverse
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
/etc/apt/sources.list.d/attente-ubuntu-modifier-only-input-switch-xenial.list:deb http://ppa.launchpad.net/attente/modifier-only-input-switch/ubuntu xenial main
/etc/apt/sources.list.d/attente-ubuntu-modifier-only-input-switch-xenial.list.save:deb http://ppa.launchpad.net/attente/modifier-only-input-switch/ubuntu xenial main
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/jgeboski.list:deb http://download.opensuse.org/repositories/home:/jgeboski/xUbuntu_16.04/ /
/etc/apt/sources.list.d/jgeboski.list.save:deb http://download.opensuse.org/repositories/home:/jgeboski/xUbuntu_16.04/ /
/etc/apt/sources.list.d/noobslab-ubuntu-themes-xenial.list:deb http://ppa.launchpad.net/noobslab/themes/ubuntu xenial main
/etc/apt/sources.list.d/noobslab-ubuntu-themes-xenial.list.save:deb http://ppa.launchpad.net/noobslab/themes/ubuntu xenial main
/etc/apt/sources.list.d/ricotz-ubuntu-testing-xenial.list:deb http://ppa.launchpad.net/ricotz/testing/ubuntu xenial main

```

---

### Post by howefield on 2016-10-15
Try removing the dead repository..

```
sudo mv /etc/apt/sources.list.d/attente-ubuntu-modifier-only-input-switch-xenial.* ~/Documents
```

This will move the attente ppa files to your Documents folder for later deletion or re-use.

Then try again with the

```
sudo apt update
```

---

### Post by MadleSs on 2016-10-15
This solved the problem :) Thank you very much!

---

### Post by howefield on 2016-10-15
Cool, you're welcome.

You can delete the files copied to your Documents folder now if you like.

---

