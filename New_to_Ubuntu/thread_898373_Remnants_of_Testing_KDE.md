---
title: "Remnants of Testing KDE"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-23
I know have a "Broken Dependency" that I cannot uninstall. Its called 

kio-umountwrapper

When I go to synaptic and try to completely remove it, I get:

> E: kio-umountwrapper: subprocess post-removal script returned error exit status 2

When I type in sudo apt-get autoremove in the terminal, I get:

> diego@Zeus:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 120068 files and directories currently installed.)
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
diego@Zeus:~$ 

I have already tried re installation and trying it that way. Any ideas anyone?

---

### Post by iaculallad on 2008-08-23
Try:

```
sudo touch /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop
```

then

```
sudo apt-get autoremove
```

---

### Post by diego898 on 2008-08-23
the first code produced this result:
> 
touch: cannot touch `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory


---

