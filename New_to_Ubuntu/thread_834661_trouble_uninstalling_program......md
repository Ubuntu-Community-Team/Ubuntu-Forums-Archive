---
title: "trouble uninstalling program....."
date: 2008-06-19
forum: New to Ubuntu
---

### Post by gsub on 2008-06-19
Hi, all.

I was messing with KDE/Gnome, and long story short, I'm back to Gnome, trying to remove this package called "kio-umountwrapper". This is the error message i get:

gsub@XXXXXX:~$ sudo apt-get autoremove
[sudo] password for gsub: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 162774 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)



the upshot of all this - i cannot install new packages using apt-get, as it tries to remove the package before installing, fails, and therefore exits. help please !

---

### Post by bumanie on 2008-06-19
Try > sudo aptitude rm <package name>

---

### Post by gsub on 2008-06-19
did that.. doesnt work..

"dpkg --remove" worked, though. <grin>

this is a work in progress.. might holler in panic again... <head hurts>

---

### Post by JoshuaRL on 2008-06-19
Just to help clean stuff out a little, try the following set of commands:
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade

```
Just a little house-cleaning to make sure things are working correctly.

---

### Post by gsub on 2008-06-19
done!!!

if only actual house-cleaning were this painless....

---

