---
title: "Unable to open compressed files (.zip, .tar.gz)"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Le-Froid on 2008-07-14
I recently had an issue with nautilus. Once I finally fixed it and was able to use most of my GUI (it froze everything on my screen), I found out I can no longer use any graphical program to open a compressed file. I always get the error message like "No program can open this file" or something.

I would greatly appreciate any help of getting a graphical program that can open such files, as using the terminal for everything can get annoying

---

### Post by braddcadd on 2008-07-14
Have you tried uninstalling tar and nautilus, then reinstalling? (pay close attention to the dependancy packages that are removed.  Then make sure the same dependancy packages are re-installed.)

> 
sudo aptitude remove tar nautilus
sudo aptitude install tar nautilus


---

### Post by Le-Froid on 2008-07-14
> **braddcadd said:**
> Have you tried uninstalling tar and nautilus, then reinstalling? (pay close attention to the dependancy packages that are removed.  Then make sure the same dependancy packages are re-installed.)

while re-installing tar I got this issue:
```

dpkg-deb (subprocess): failed to exec tar: No such file or directory
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/tar_1.19-3_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/tar_1.19-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by SunnyRabbiera on 2008-07-14
check if synaptic spits out issues, its located in your menus under system> administration> synaptic package manager...
you may have a very common issue here but lets see.

---

### Post by Le-Froid on 2008-07-14
No, doesn't say anything is broken or anything (in filter or whatever), while installing through synaptic I get error:
```

E: /var/cache/apt/archives/tar_1.19-3_i386.deb: subprocess dpkg-deb --control returned error exit status 2

```

---

### Post by SunnyRabbiera on 2008-07-14
hmm, you may have to run sudo dpkg -l |grep dpkg or something like that...
did you have two package managers running at the same time?

---

### Post by Le-Froid on 2008-07-14
It returned
```

ii  apt                                        0.7.9ubuntu17                      Advanced front-end for dpkg
ii  dpkg                                       1.14.16.6ubuntu4                   package maintenance system for Debian
ii  dpkg-dev                                   1.14.16.6ubuntu4                   package building tools for Debian

```

When trying to install tar, I only keep one package manager running

---

### Post by braddcadd on 2008-07-14
I can't believe this but evidently tar is required to install tar !?!  It looks like the only way to get tar back is to mount the Ubuntu live CD.

Here is a thread where someone did that successfully (see post #16):
[http://ubuntuforums.org/showthread.php?t=758807&highlight=(subprocess)%3A+failed+exec+tar&page=2](http://ubuntuforums.org/showthread.php?t=758807&highlight=(subprocess)%3A+failed+exec+tar&page=2)

Keep the thread going.  I'll hang with you til you get it working.  Sorry about that uninstall tar business earlier :(

---

### Post by Le-Froid on 2008-07-14
Yeah no problem, I'll try to find my live cd :s

---

### Post by Le-Froid on 2008-07-14
Just got tar working again! :D
Now, to try to get nautilus working :S

edit: reinstalling nautilus didn't work

---

### Post by braddcadd on 2008-07-14
What errors are you getting with that?  I assume you are using aptitude.  Will the live CD trick work for this also?

---

### Post by Le-Froid on 2008-07-14
> **braddcadd said:**
> What errors are you getting with that?  I assume you are using aptitude.  Will the live CD trick work for this also?

I may be missing a plugin for nautilus or something that is preventing me from opening compressed files (without using command line)

EDIT: Not really errors, just says no application can open the files. When I try opening it with nautilus, then it says that nautilus can't open that file type (in this case, .tar.gz)

---

### Post by Le-Froid on 2008-07-14
sweet, found out to install "file-roller", and now everything works! Thanks for your help braddcadd and SunnyRabbiera

---

