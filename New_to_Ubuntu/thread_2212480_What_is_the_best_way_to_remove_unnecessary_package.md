---
title: "What is the best way to remove unnecessary packages?"
date: 2014-03-21
forum: New to Ubuntu
---

### Post by arroy_0209 on 2014-03-21
I got the following message while trying to install ("sudo apt-get install ...") a new package:
> 
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-56 libubuntuoneui-3.0-1 linux-headers-3.2.0-56-generic-pae
  linux-headers-3.2.0-56-generic
Use 'apt-get autoremove' to remove them.

I do not understand why suggestion to remove unnecessary packages comes while trying to install a new package. How do I know these are the only package which are no longer required? may be when I try to install some other package, I will get names of some more packages which are not required as well. Is the command "autoremove" the best for this purpose?

---

### Post by philinux on 2014-03-21
The package manager is merely informing a user that some packages are redundant as part of the normal operation of it.

sudo apt-get autoremove

will do the job.

Also see this.

man apt-get

---

### Post by grahammechanical on 2014-03-21
The suggestion to remove unnecessary packages is not coming because we are installing a new package but because we are in effect running the apt-get update and the apt-get upgrade combination.
 
Installing/upgrading can make some libraries obsolete but they may not be listed in the install/upgrade script for removal in case they are part of the dependencies of other packages. So, apt-get advises us of any packages that are on the system and are obsolete but not listed as dependencies of any of the packages that we have installed. And are therefore safe to remove.

Regards

---

### Post by tgalati4 on 2014-03-21
Yes, it is quite disconcerting to be told that you have extraneous packages while trying to install something.  That sounds more like a Microsoft annoyance than a Linux notification.  Anyway, apt-get does a reasonably good job keeping tabs on what packages are needed.  The *autoremove* switch is generally safe to use.

You can manually remove other packages, but you risk breakage.  At least you get to keep the pieces.

---

### Post by arroy_0209 on 2014-03-22
Thanks. I have a doubt to clear, should I use purge command to remove those unnecessary packages or is it better to use autoremove command?

---

### Post by coldcritter64 on 2014-03-22
The only real difference in your situation between autoremove and purge is that purge also removes any left over config files (system config not user config).
From "man apt-get":
> purge
           purge is identical to remove except that packages are removed and
           purged (any configuration files are deleted too).

These files are usually very small and leaving them does no harm. Purging is useful when reinstalling an application so as to kill the old configuration for the package being removed. Note that purging only removes system config files for an application, if the application stores config files in hidden files or folders in the user's home directory, they need to be manually removed by the user.

I would suggest you stick just with autoremove if just doing simple cleanup and leave purging for when you need to remove the config specifically.

---

