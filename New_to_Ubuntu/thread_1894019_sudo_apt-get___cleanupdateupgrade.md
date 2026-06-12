---
title: "sudo apt-get   clean/update/upgrade"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by swordsintoplowshares on 2011-12-11
In the Installation & Upgrades forum, in the Sticky post: "I  upgraded, and now I have this error..."  it suggests running these 3 commands:

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

Newbie question: what does each command do? 
Thanks in advance.

---

### Post by Cookieh on 2011-12-11
[U]
apt-get clean[/U]

apt-get clean will not harm your system. The .deb packages in  /var/cache/apt/archives are used by the system to install software. But  once the software is installed, these .deb packages are no longer  needed. You will need these .deb files only while re-installing the  software. In case you do not need to re-install, remove these .deb files  using apt-get clean.

_apt-get update_

apt-get update is use for updating all your current catalog for the latest update

_apt-get upgrade_ 

apt-get upgrade is use to upgrade apps that u have install on your Computer or Laptop

---

### Post by Cookieh on 2011-12-11
BTW i am running as root so i dont use sudo anymore but if you are an administrator you need to use sudo

---

### Post by oldos2er on 2011-12-11
You have access to documentation for any program or command using **man**
For example, ```
man apt-get
``` will show you info on the commands you posted: 

clean
           clean clears out the local repository of retrieved package files. It removes
           everything but the lock file from /var/cache/apt/archives/ and
           /var/cache/apt/archives/partial/. When APT is used as a dselect(1) method,
           clean is run automatically. Those who do not use dselect will likely want to
           run apt-get clean from time to time to free up disk space.


 update
           update is used to resynchronize the package index files from their sources.
           The indexes of available packages are fetched from the location(s) specified
           in /etc/apt/sources.list. For example, when using a Debian archive, this
           command retrieves and scans the Packages.gz files, so that information about
           new and updated packages is available. An update should always be performed
           before an upgrade or dist-upgrade. Please be aware that the overall progress
           meter will be incorrect as the size of the package files cannot be known in
           advance.

upgrade
           upgrade is used to install the newest versions of all packages currently
           installed on the system from the sources enumerated in /etc/apt/sources.list.
           Packages currently installed with new versions available are retrieved and
           upgraded; under no circumstances are currently installed packages removed, or
           packages not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without changing the
           install status of another package will be left at their current version. An
           update must be performed first so that apt-get knows that new versions of
           packages are available.

---

### Post by bluexrider on 2011-12-11
sudo apt-get clean = Clears out the local repository of retrieved package files. It removes everything but the lock file from */var/cache/apt/archives/* and */var/cache/apt/archives/partial/*

sudo apt-get update = Used to re-synchronize the package index files from their sources. The indexes of available packages are fetched from the **location**(s) specified in */etc/apt/***[sources.list]("http://linux.die.net/man/5/sources.list")**

sudo apt-get upgrade = Used to install the newest versions of all packages currently installed on the system from the sources enumerated in */etc/apt/***[sources.list]("http://linux.die.net/man/5/sources.list")**(5). Packages  currently installed with new versions available are retrieved and  upgraded; under no circumstances are currently installed packages  removed, nor are packages that are not already installed retrieved and installed. New  versions of currently installed packages that cannot be upgraded without  changing the install status of another package will be left at their current version.  An update must be performed first so that **apt-get** knows that new versions of packages are available.

---

### Post by Cookieh on 2011-12-11
Couldnt have said it any better... Thanks oldos2er and bluexrider

---

### Post by swordsintoplowshares on 2011-12-11
To everyone who responded: thank you very much, I appreciate the quick answers. :D

---

### Post by bluexrider on 2011-12-11
need any more help let us know


mark this 

(SOLVED)

---

