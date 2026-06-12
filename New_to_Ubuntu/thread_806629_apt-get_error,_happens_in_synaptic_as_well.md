---
title: "apt-get error, happens in synaptic as well"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-05-25
I cant use the repo's for anything, atm (I followed a command on psychocats site to remove kde compleatly and then this started happening)

```
harry@lenovo:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 267302 files and directories currently installed.)
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
harry@lenovo:~$ 

```

gargh, I cant get the codec I need to watch flv, and I really really want it.

---

### Post by sdennie on 2008-05-25
Have you tried running:

```

sudo apt-get install -f

```

That fixes many problems of this nature.

---

### Post by barbedsaber on 2008-05-25
> **vor said:**
> Have you tried running:

```

sudo apt-get install -f

```

That fixes many problems of this nature.

indeed I have, I got

```
harry@lenovo:~$ sudo apt-get install -f
[sudo] password for harry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 267302 files and directories currently installed.)
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
harry@lenovo:~$ 


```

---

