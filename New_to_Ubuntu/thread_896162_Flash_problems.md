---
title: "Flash problems"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by HebrewTheHammer on 2008-08-20
My flash plug-in wont work...i just reformatted my computer because it was just bogged down adding to the **** that made it not work...i installed 8.04 from scratch and then flash from the synaptic package manager...to no avail.

Flash will still not work...nothing i do or try make sit work...it was fine on 7.10 but will not work since update...so obviously thats the problem.

if none will help me fix flash. the ncould they tell me where to get gutsy back.

---

### Post by spiderbatdad on 2008-08-20
you installed flashplugin-nonfree or ubuntu-restricted-extras and you can't stream videos?

---

### Post by tuxxy on 2008-08-20
Check if you have it installed, type 

```
about:plugins
```

into your browser and check for Flash plugin

---

### Post by HebrewTheHammer on 2008-08-21
I installed flash plugin not the other one

---

### Post by HebrewTheHammer on 2008-08-21
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No


this is the only one not enabled...do i need to enable it somehow.

---

### Post by forger on 2008-08-21
Is your Ubuntu 64-bit or 32-bit?
Reply with the output of this commands in Applications > Accessories > Terminal:
```
uname -a
apt-cache policy flashplugin-nonfree
```

---

### Post by HebrewTheHammer on 2008-08-21
flashplugin-nonfree:
  Installed: 9.0.124.0ubuntu2
  Candidate: 9.0.124.0ubuntu2
  Version table:
 *** 9.0.124.0ubuntu2 0
        500 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) hardy/multiverse Packages
        100 /var/lib/dpkg/status




32

[EDIT]
Linux chris-desktop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

---

### Post by ctswhole on 2008-08-21
Try this, it totally solved my flash problems

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

---

### Post by HebrewTheHammer on 2008-08-21
> **ctswhole said:**
> Try this, it totally solved my flash problems

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472")

the videos don't even play...not to be testy with an offer of help, but that looks like a lot of work for a sound problem...

The sites im trying to view will tell me the page is completely loaded...but the videos aren't playing. its like it realizes there is flash there and stops trying...it gives me no error message and doesnt say i need to upgrade...just no video.

---

