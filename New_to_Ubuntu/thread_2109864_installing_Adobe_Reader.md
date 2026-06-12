---
title: "installing Adobe Reader"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by miscellanyous on 2013-01-28
Hi, I am trying to install Adobe Reader but have some dependency problems. Installing via synaptic fails because of broken packages. Here's more info from the command line:

```
$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 acroread : Depends: nspluginwrapper but it is not installable
E: Unable to correct problems, you have held broken packages.
```

```
sudo apt-get install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nspluginwrapper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'nspluginwrapper' has no installation candidate
```

I also tried down loading AdbeRdr9.5.3-1_i386linux_enu.deb and installing via the software centre --> also fails. My system
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```

---

### Post by omeomi on 2013-01-28
Did you enable all the repositories in Software Sources? (I think this package is in the Multiverse repo)

Otherwise, you can find the package here: [https://launchpad.net/ubuntu/+source/nspluginwrapper](https://launchpad.net/ubuntu/+source/nspluginwrapper)

---

### Post by miscellanyous on 2013-01-28
> **omeomi said:**
> Did you enable all the repositories in Software Sources? (I think this package is in the Multiverse repo)

Otherwise, you can find the package here: [https://launchpad.net/ubuntu/+source/nspluginwrapper](https://launchpad.net/ubuntu/+source/nspluginwrapper)

Thanks, yes multiverse is enabled but oddly synaptic doesn't show the nspluginwrapper package. Here's what I found when I tried to manually download & install:
```
$ sudo dpkg -i nspluginwrapper_1.4.4-0ubuntu3_amd64.deb 
[sudo] password for cs: 
Selecting previously deselected package nspluginwrapper.
(Reading database ... 588937 files and directories currently installed.)
Unpacking nspluginwrapper (from nspluginwrapper_1.4.4-0ubuntu3_amd64.deb) ...
dpkg: dependency problems prevent configuration of nspluginwrapper:
 nspluginwrapper depends on nspluginviewer (= 1.4.4-0ubuntu3); however:
  Package nspluginviewer is not installed.
dpkg: error processing nspluginwrapper (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 nspluginwrapper

```

But oddly nspluginviewer is supposed to be contained in nspluginwrapper ?!? I am confused

---

### Post by omeomi on 2013-01-29
You could run this to see if it gives you any hints about broken packages:
```
sudo apt-get install -f
```

and/or boot into recovery mode and choose "Fix broken packages"

This guy seems to have the same problem and apparantly was only able to solve it by reinstalling Ubuntu (which should not be a big deal as long as you have a separate /home partition):
[http://askubuntu.com/questions/76766/how-do-i-overcome-these-package-dependency-problems](http://askubuntu.com/questions/76766/how-do-i-overcome-these-package-dependency-problems)

---

### Post by miscellanyous on 2013-01-29
Good news! After enabling the multiverse repo I ran an update. This installed a few new packages from multiverse. Then tried to install acroread again and it works :)

---

