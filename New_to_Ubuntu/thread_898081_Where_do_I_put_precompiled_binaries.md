---
title: "Where do I put precompiled binaries?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by raccoonone on 2008-08-22
I've downloaded a couple programs like Songbird and Eclipse 3.4, which aren't in the repos and come as precompiled binaries. Where is the "right" place to put these? I've been keeping them in /home/christopher/bin/, but would it be better to put them in /bin/, /usr/bin/ or maybe /usr/local/bin/? And, is there a site that explains the difference between all these bin folders?

---

### Post by jerome1232 on 2008-08-22
I always put programs like that in /opt/*appname*

from [http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/opt.html](http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/opt.html)
> 1.17. /opt

This directory is reserved for all the software and add-on packages that are not part of the default installation. For example, StarOffice, Kylix, Netscape Communicator and WordPerfect packages are normally found here. To comply with the FSSTND, all third party applications should be installed in this directory. Any package to be installed here must locate its static files (ie. extra fonts, clipart, database files) in a separate /opt/'package-name' directory tree (similar to the way in which Windows will install new software to its own directory tree C:\Windows\Progam Files\"Program Name"), where 'package-name' is a name that describes the software package.

---

### Post by xeth_delta on 2008-08-22
> **raccoonone said:**
> I've downloaded a couple programs like Songbird and Eclipse 3.4, which aren't in the repos and come as precompiled binaries. Where is the "right" place to put these? I've been keeping them in /home/christopher/bin/, but would it be better to put them in /bin/, /usr/bin/ or maybe /usr/local/bin/? And, is there a site that explains the difference between all these bin folders?

If the programs are precompiled and you downloaded them under a deb package, they already have a predefined target directory. I believe there might be a way to change the target, if you want to, though, but if it is a deb package, apt will keep track of it in the local package database.

---

### Post by raccoonone on 2008-08-23
> **jerome1232 said:**
> I always put programs like that in /opt/*appname*

from [http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/opt.html](http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/opt.html)

Thanks! That looks like the perfect place for them.

---

### Post by loell on 2008-08-23
usually this precompiled binaries are installers in itself, most of the the time it will choose some default paths.

---

### Post by raccoonone on 2008-08-23
> **loell said:**
> usually this precompiled binaries are installers in itself, most of the the time it will choose some default paths.

Thanks. I'm pretty sure that's not the case with Songbird and Eclipse though. Each one has an executable file that opens the program without any further configuration/installation.

---

### Post by Nepherte on 2008-08-23
> **raccoonone said:**
> Thanks. I'm pretty sure that's not the case with Songbird and Eclipse though. Each one has an executable file that opens the program without any further configuration/installation.
That is correct.

---

