---
title: "problem with the update manager"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by CrossS on 2008-06-23
Hi

When I try to update i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Then when I use terminal to run
dpkg --configure -a

I get this massage: dpkg: requested operation requires superuser privilege

But I don't remember my superuser password :S

What can I do?

---

### Post by Duck2006 on 2008-06-23
Try,

sudo dpkg --configure -a

then,

sudo update
sudo upgrade

---

### Post by forestpixie on 2008-06-23
Use sudo with your password

sudo dpkg --configure -a

---

### Post by CrossS on 2008-06-23
> **Duck2006 said:**
> Try,

sudo dpkg --configure -a

then,

sudo update
sudo upgrade

It worked but now I got this massage:

dpkg: error processing gnome-applets-data (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 gnome-applets-data

I'm on deep water now :S

---

### Post by aheckler on 2008-06-23
Try this:

```
sudo apt-get purge gnome-applets-data
sudo apt-get install gnome-applets-data
```

---

### Post by CrossS on 2008-06-23
> **aheckler said:**
> Try this:

```
sudo apt-get purge gnome-applets-data
sudo apt-get install gnome-applets-data
```

when I use: 

sudo apt-get purge gnome-applets data

I get this massage:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package data

---

### Post by RiceMonster on 2008-06-23
Be careful, removing gnome-applets data removes the ubuntu-desktop. if that gets removed, run

```
sudo apt-get install ubuntu-desktop
```

---

### Post by aheckler on 2008-06-23
There's a hyphen there, it's "gnome-applets-data".

---

### Post by forestpixie on 2008-06-23
it's a typo

---

### Post by aheckler on 2008-06-23
> **RiceMonster said:**
> Be careful, removing gnome-applets data removes the ubuntu-desktop. if that gets removed, run

```
sudo apt-get install ubuntu-desktop
```

Shoot, that was a bad typo for me to make.... :-\

---

### Post by Duck2006 on 2008-06-23
or you can do it from Synaptic Package Manager.

---

### Post by CrossS on 2008-06-23
Typed: 

sudo apt-get purge gnome-applets-data

Got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-applets* gnome-applets-data* ubuntu-desktop*
0 upgraded, 0 newly installed, 3 to remove and 75 not upgraded.
1 not fully installed or removed.
After this operation, 28.2MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 153599 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing gnome-applets ...
Purging configuration files for gnome-applets ...
dpkg: error processing gnome-applets-data (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
E: Sub-process /usr/bin/dpkg returned an error code (1)

There is an error there :S

When I still tried to install I got an error (not in terminal)

"Sorry, the package "gnome-applets-data 2.22.2-0ubuntu2" failed to install or upgrade"

---

### Post by CrossS on 2008-06-23
nm, tried to do it again and this time it worked :) 
trying to update now.. will let you know how it goes

---

### Post by CrossS on 2008-06-23
It worked :D

You guys are great!

---

