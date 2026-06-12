---
title: "[SOLVED] synaptic package manager"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by JaJaBinks on 2008-11-06
A newbiew to Linux and ubuntu I am learning fast, but am a little out of my depth with a problem affecting Update manager, synaptic package manager and software sources.

1. Synaptic package manager will not start from GUI, but will start from terminal using exec synaptic package manager
2. Software sources will not start from GUI, and I have no idea how to get it to run from terminal
3. Update manager will start from GUI, but just hangs when either Check or update are selected. I am able to update using terminal and apt-get update and apt-get upgrade.

I have looked at several threads relating to problems with update manager but have not been able to resolve the issue.

Any suggestions would be appreciated

---

### Post by billgoldberg on 2008-11-06
Start all of those program from the terminal using,

gksudo synaptic

or gksudo application 

I'm not on Ubuntu right now so I can't check how those applications are called.

Try asking on irc (if you don't know how to use it, see:

[http://linuxowns.wordpress.com/2008/04/23/ubuntu-irc-channel/](http://linuxowns.wordpress.com/2008/04/23/ubuntu-irc-channel/))

If you start them, what errors does the terminal give?

Post those here for each of those three applications.

---

### Post by digitalvectorz on 2008-11-06
Hey JaJaBinks,

> 
2. Software sources will not start from GUI, and I have no idea how to get it to run from terminal

To edit the software sources (for synaptic) from the terminals, type this:
```

gksudo gedit /etc/apt/sources.list

```
That will open up a gui text editor for you to manually edit the sources.


As for the GUI problems, honestly I'm not too sure.  I only use the terminal to install/upgrade/etc.  Rarely do I use the GUI, sorry :|

---

### Post by nothingspecial on 2008-11-06
Don`t know whats wrong but you can modify your software sources by typing ```
gksudo gedit /etc/apt/sources.list
```
Add lines to the bottom to add sources
Comment out lines you no longer want (put a # infront)
Save close then
```
sudo apt-get update
``` as you already know.

You can search your software sources from the terminal using 
```
apt-cache search word
``` where word is the app you are seaching for.

Hope that helps a little untill you get your main problem sorted.

---

### Post by JaJaBinks on 2008-11-06
Thanks for the tips. I suspect the problem lies with sources.list. Now that i know how to edit it, i will give it a go.
I tried to upload sources.list to my thread earlier but did not happen
Thanks again

---

### Post by nothingspecial on 2008-11-06
The way to post your sources.list is
```

cat /etc/apt/sources.list
```

Then just copy and paste.

cat prints text files in a terminal so you would use it when you just want to view something rather than edit it.

---

### Post by fvds on 2008-11-06
Are you logged in to Ubuntu with a user that has sufficient rights? If the user is not allowed to manage the system Synaptic will not run from the GUI.

---

### Post by JaJaBinks on 2008-11-06
This gets worse. just tried gksudo gedit /etc/apt/sources.list
Administration GUI started then just bombed out.

I tried editing sources.list directly with gedit, but was unable to save changes due to a permission error

---

### Post by JaJaBinks on 2008-11-06
Thanks. User priveleges checked and OK

---

### Post by nothingspecial on 2008-11-06
You can`t gedit your sources.list without gksudoing it.
Are you logged in as an administrator? Can you sudo stuff?
Try to edit it in the terminal with ```
sudo nano /etc/apt/sources.list
```
nano is a command line text editor
Ctrl + O will save your changes
Ctrl + X will exit

---

### Post by JaJaBinks on 2008-11-06
# 
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080701)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by JaJaBinks on 2008-11-06
Thanks. That one worked.

---

### Post by nothingspecial on 2008-11-06
Editing your sources list will not solve your problem of synaptic package manager not working. I don`t have the answer for that.
What we`ve been showing you is how to get along without it. Synaptic package manager and software sources are the guis for the commands we`ve been showing you.
So when you click search and type googleearth in the box and hit enter in software sources, you are just telling ubuntu to ```
apt-cache search googleearth
```
The result is the same.
Somebody who knows far more than me will have to fix synaptic and software sources.

---

### Post by JaJaBinks on 2008-11-07
Thank you for your assistance. With the help you have given me I have been able to edit the sources.list, which has now solved the problem with the GUI.

This has been a valuable learning experience for me

Thanks again

---

### Post by JaJaBinks on 2008-11-07
Thanks to all who responded to my thread. with your help and suggestions I have been able to locate the cause of the problem, and edit the sources.list, which has now solved the problem with the GUI.

This has been a valuable learning experience, encouraging me to do more from terminal and rely less on GUI

---

