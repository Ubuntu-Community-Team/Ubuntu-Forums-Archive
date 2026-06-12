---
title: "I can't install updates?"
date: 2015-06-03
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-06-03
Hello guys
When I open the update manager I get the following message: 
```
Not all updates can be installed
Run a partial upgrade to install as many updates as possible.
This can be caused by: 
* A previous upgrade which didn't complete
* Problem with some of the installed software
* Unofficial software packages not provided by Ubuntu
* Normal changes of pre-release version of Ubuntu
When I run "sudo apt-get -f install" here is what I get: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer
0 upgraded, 0 newly installed, 1 to remove and 21 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
```
And then when I press Y here is what I get: 
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:i386
Thank you for any help.

---

### Post by dino99 on 2015-06-03
so start cleaning the sources and system:

- comment out the third party sources if any
from a terminal:
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update

---

### Post by deadflowr on 2015-06-03
It's rare to get a partial upgrade request in a stable release.
(Very common in the development release)
Typically, it means an older package is to be replaced, but the older package also needs to be removed in order for the new package to work.

When you get a partial upgrade you can select it.
You can select it because it won't actually begin the upgrade/remove/install quite yet as the system will start a procedure.
It goes through several pages first and then it'll show one last page.
The last page is key.
In this last page should be an arrow toggle marked with the word Details.
Click on that and it'll show exactly what is to be done.
You can usually see which package is to be installed, upgraded, and removed.
Most of the time you should be able to match up a new package that coincides with a package that is to be removed.

If you feel that proceeding with the upgrade might be trouble, you can still cancel it on the Last Page.

Hope that makes sense.

---

### Post by remmas-sido on 2015-06-03
> **dino99 said:**
> so start cleaning the sources and system:

- comment out the third party sources if any
from a terminal:
I have done everything you write, but after refreshing package here is what comes: 
W: GPG error: [http://dz.archive.ubuntu.com](http://dz.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

