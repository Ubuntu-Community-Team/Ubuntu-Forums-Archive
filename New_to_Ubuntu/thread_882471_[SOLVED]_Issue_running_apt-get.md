---
title: "[SOLVED] Issue running apt-get"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Mauler5858 on 2008-08-07
When i run apt-get when trying to install sarg i get:

:~$ sudo apt-get install sarg
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libfreetype6 libgd2-noxpm libjpeg62 libpng12-0
Suggested packages:
  libfreetype6-dev libgd-tools httpd apache2 libapache2-mod-php5 squidguard
The following NEW packages will be installed:
  libfreetype6 libgd2-noxpm libjpeg62 libpng12-0 sarg
0 upgraded, 5 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
:~$

---

### Post by cdtech on 2008-08-07
Try running "sudo apt-get autoremove && sudo apt-get clean" then do an "update"

**P.S.**
Make sure you don't have another instance of Synaptic running.
And you may want to try running "dpkg --configure -a"

---

### Post by iaculallad on 2008-08-07
On your terminal:

```
sudo rm /var/cache/apt/archives/lock
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by prshah on 2008-08-07
> **Mauler5858 said:**
> 
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
:~$

This message comes when you open a second (or more) instance of any package manager; all package managers work on the same backend; you can have only one package-manager running on your system at any given time; you cannot run multiple package managers simulatenously.

Package managers include: apt-get and derivatives, aptitude (GUI for apt-get), Synaptic, update-manager etc.

If you have no other active package managers running, you may have set auto-updates to update in the background, and at the moment of trying to install using apt-get, that update-manager would have probably been running.

---

### Post by Mauler5858 on 2008-08-07
Thanks that worked

---

