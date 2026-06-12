---
title: "can't do anything with broken packages"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Matt26 on 2008-06-10
i have 2 packages on ubuntu 8.04 that are broken- firefox 3.0 and xulrunner-1.9-gnome-support.

when i try to uninstall either from synaptic they fail (error messages related to files that couldn't be deleted/removed if i remember correctly) and i have tried fixing them using the 'sudo apt-get install -f' command, which gives the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dpatch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9-gnome-support
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 3842kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151584 files and directories currently installed.)
Removing firefox-3.0-gnome-support ...
dpkg: error processing firefox-3.0-gnome-support (--remove):
 cannot remove file `/usr/share/doc/firefox-3.0-gnome-support/changelog.Debian.gz': Not a directory
Removing firefox-3.0 ...
dpkg: error processing firefox-3.0 (--remove):
 cannot remove file `/usr/lib/firefox-3.0b5/defaults/profile': Not a directory
Removing xulrunner-1.9-gnome-support ...
dpkg: error processing xulrunner-1.9-gnome-support (--remove):
 cannot remove file `/usr/share/doc/xulrunner-1.9-gnome-support/changelog.Debian.gz': Not a directory
Errors were encountered while processing:
 firefox-3.0-gnome-support
 firefox-3.0
 xulrunner-1.9-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

trying to apply updates when they are available yeilds the same error messages as in synaptic (2 of the upgrades are for the same apps in question- strangely i only had v3 beta 5 of FF before this messs started but now i have v3 after numerous trials/errors with synaptic and the update manager?)

i have also been prompted to do a partial upgrade when updates are available to be installed but they fail as well.

what can i do to get these fixed?

thanks.

---

### Post by JoshuaRL on 2008-06-10
Try the following commands first:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

```
If that doesn't work, you may need to remove and reinstall FF:
```

sudo apt-get remove firefox-3.0
sudo apt-get install firefox-3.0

```
If that doesn't work, try removing it with a --purge option to make the removal more intense.

---

### Post by RomeReactor on 2008-06-10
Hi. Is this the Firefox package that comes with Ubuntu, or a version downloaded from the Mozilla site?

If it is the Ubuntu version, try:
```
sudo dpkg --configure -a
```
If that doesn't help:
```
sudo dpkg --remove --force-remove-reinstreq firefox-3.0 firefox-3.0-gnome-support xulrunner-1.9-gnome-support
```

Then try installing Firefox 3 again.

---

### Post by Matt26 on 2008-06-10
thanks for the suggestions- i have tried the commands in both responses but i am still receiving the same error messages that i had posted when i try any of those commands (the commands for sudo apt-get update and upgrade did seem to execute successfully though) 

this is the ubuntu version of FF, not from the website.

---

### Post by RomeReactor on 2008-06-10
Are you sure the directories/files dpkg complains about are really there?

**/usr/share/doc/firefox-3.0-gnome-support/changelog.Debian.gz**

**/usr/lib/firefox-3.0b5/defaults/profile**

**/usr/share/doc/xulrunner-1.9-gnome-support/changelog.Debian.gz**

If not, you could try making the folders/files and then try to reinstall Firefox.

---

### Post by gr4nf on 2008-06-10
You could try changing your sources.list file.

Make a backup:
```

sudo mv /etc/apt/sources.list /etc/apt/sourcesback.list

```
and now replace your old sources.list with this (assuming you have the 32 bit version of hardy):
```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse

```

---

### Post by Matt26 on 2008-06-10
i discovered that the directories do not exist as they should be so i am trying to create the proper files/folders but (of course) i am running into problems- i am trying to copy a file out of the /usr/share/doc directory using 'sudo cp firefox-3.0-gnome-support /home/matthew/Documents' (while i am in the directory that contains the file) to backup the file before deleting it but it isn't working- telling me there is an invalid argument with the filename.. i have even tried using 'sudo nautilus' to open a window and do a copy of the file but that ends up reporting a permissions error- what am i doing wrong here?

---

### Post by cariboo on 2008-06-11
You can't copy the directroy, but you can copy the files and you don't need to be root to do it. In a terminal

```
user@intrepid:/usr/share/doc/firefox-3.0$ cp * /home/user/Documents
```

That will copy all the files to your documents directory. Substitute your user name for user.

Use the broken packages filter in synaptic to repair your problem.

Jim

---

### Post by Matt26 on 2008-06-11
i am trying to copy a single file, not the entire contents of a directory- the file is located under the doc directory, not in the firefox-3.0 directory.  thanks.

---

### Post by RomeReactor on 2008-06-11
try making the directories first, then add the files:
```
sudo mkdir /usr/share/doc/firefox-3.0-gnome-support
```
```
sudo mkdir /usr/lib/firefox-3.0b5/defaults
```
```
sudo mkdir /usr/share/doc/xulrunner-1.9-gnome-support
```

Then:

```
sudo touch /usr/share/doc/firefox-3.0-gnome-support/changelog.Debian.gz
```
```
sudo touch /usr/lib/firefox-3.0b5/defaults/profile
```
```
sudo touch /usr/share/doc/xulrunner-1.9-gnome-support/changelog.Debian.gz
```

And try removing/reinstalling Firefox.

---

### Post by tinny on 2008-06-11
Have you tried to clean apt and start again?

```

sudo apt-get clean
sudo apt-get update
...etc

```

---

### Post by Matt26 on 2008-06-12
ok i have tried everything that i can think of to get rid of this file firefox-3.0-gnome-support that is in the /usr/share/doc/ directory- i have even logged into ubuntu as root and i still can't do anything with it- i get errors whether i try copying it (invalid argument) or deleting it (operation not permitted).

this is also the name of one of the packages that is marked for removal in synaptic- however i can't get synaptic to undo the marking of this or the other packages that are currently marked for deletion- but i can't remove them either because everytime i try i run into errors related to the missing directories i mentioned in my fist post (it's looking for directories to remove with these packages that are not there).

could this file be the prorgam itself that synaptic is referring to?  maybe that's why i can't do anything with the file?  this is getting really crazy now and i don't know what else i can do to remedy this issue.

any help would be greatly appreciated.

---

### Post by Matt26 on 2008-06-16
i finally found a fix for this issue (see link below). it turns out that the problem was with the packages themselves, since they were being shown as only "half/partially installed".. and all my settings in firefox were saved as well!

[https://answers.launchpad.net/ubuntu/+question/4838](https://answers.launchpad.net/ubuntu/+question/4838)
(details are in the grey section)

---

