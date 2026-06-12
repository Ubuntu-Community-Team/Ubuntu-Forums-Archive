---
title: "How to delete unused files"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by alcla on 2012-11-15
How do I delete unused files that remain after running the Update Manager. I would appreciate your assistance. Thank you.

---

### Post by Mr_JMM on 2012-11-15
```
sudo apt-get update
```
```
sudo apt-get autoremove
```
```
sudo apt-get autoclean
``` or instead of autoclean ```
sudo apt-get clean
``` for more thorough cleaning.

---

### Post by Jibbals on 2012-12-24
The autoclean freed me up a little bit of space, there were still some files left over from old packages which I had to find and rm -rf myself, is there a nice way to pinpoint folders which have more than a threshold of space usage?

---

### Post by ibjsb4 on 2012-12-25
Give "Bleachbit" a try, its in the software center.

---

### Post by Zill on 2012-12-25
> **Jibbals said:**
> The autoclean freed me up a little bit of space, there were still some files left over from old packages which I had to find and rm -rf myself, is there a nice way to pinpoint folders which have more than a threshold of space usage?
Unless you are *really* short of disk space I recommend you do not do this as the space taken up by "unused" files from old packages is generally insignificant.

Your post count (and question!) implies you are a "newbie" to Linux and, as such, you are very likely to cause major damage to your system by using commands such as "rm -rf".  The "cleaning" utilites can also cause damage if not used correctly.  My advice is just to stay clear of these things - you generally don't need them. ;-)

---

### Post by Pjotr123 on 2012-12-25
As Zill says. Linux hardly pollutes. Avoid Bleachbit and their lot.

Should you wish to do some cleaning anyway, then these are safe cleaning actions:
[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

Good luck! :)

---

### Post by The Spectre on 2012-12-25
Ubuntu Tweak has a Janitor function for cleaning out unneeded files plus many other useful features.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

I have used it several time with no ill effect.

I would recommend leaving the Old Kernel files.

---

### Post by grahammechanical on 2012-12-25
Please tell me how you know they are unused. I see Update Manager removing files/packages that have been replaced by newer packages.

Regards

---

### Post by alcla on 2013-05-26
I used the site "How to clean up Ubuntu" : [https://sites.google.com/site/easylinuxtipsproject/clean#TOC-The-registry](https://sites.google.com/site/easylinuxtipsproject/clean#TOC-The-registry). I Used the "Remove unused remains of uninstalled software" procedure. That was about three days ago, and still the old kernals remain. I am still running  version 10.04 which is an updated version. Is this process something that I have to wait on, and if so how long? Thank you.

---

### Post by Impavidus on 2013-05-27
That procedure will get rid of remaining configuration files of removed packages.

Old kernels are kept, so that you have something to fall back on in case the new kernel unexpectedly doesn't work with your hardware. You can remove them by removing the packages **linux-image-<some version>** using synaptic. It's best to keep one old kernel at all times. This is explained under point 4 (Remove old kernels) in the link you gave.

Unless you use the server edition, 10.04 is no longer updated. Consider upgrading to 12.04 LTS.

---

### Post by mustafi05 on 2013-06-01
though ubuntu tweak has an great feature tarmed as janitor which i use successfully to remove the old stored binaries , in some wiki someone had forbid to use it, i do not know why . i will be greatful if somebody give some explanation why.

---

