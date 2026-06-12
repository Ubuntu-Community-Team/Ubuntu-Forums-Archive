---
title: "SOS!!!Cannot install build essential"
date: 2008-03-13
forum: Programming Talk
---

### Post by naria on 2008-03-13
I was trying to compile a C source code when I got the following messege:

```

master.c:1:19: error: stdio.h: No such file or directory
master.c:2:20: error: stdlib.h: No such file or directory
master.c:3:18: error: math.h: No such file or directory

```

So i tried to reinstall the build-essential package. When I open the synaptic I saw that build-essential was not installed, although the last year I've been compiling C programs. So I tried to install it. And the following messege appeared:
```

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev
 Depends: g++ but it is not going to be installed

```

I tried libc6-dev. Messege:

```

libc6-dev:
  Depends: libc6 (=2.3.6-0ubuntu20.5) but 2.7-6 is to be installed

```

I tried libc6 was installed so I tried to completly remove it and install it again. Messege:
```

Could not apply changes!
Fix broken packages first

```
So i tried to fix them but I got 
```

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

I had the same problems when trying to install g++, which depends on g++4.0,which depends on libstdc++6-4.0-dev,which depends on g++4.0, which depends on libc6-dev. Which I can't install!!!


I read several posts in the forum in order to fix the problem but nothing seems to happen. Please someone help I try to work it out by myself for the last 2 days.    ](*,)


And something else when hitting the reload button in the synaptic it stops downloading and after i cancel the download i get:

```

Could not download all repository indexes
http://gr.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg
http://gr.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg
http://gr.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg
http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz: 404 Not Found
http://au.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz: 404 Not Found
http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz: 404 Not Found
http://au.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz: 404 Not Found


```

---

### Post by rklauco on 2008-03-13
There seems to be some problem with your internet connection as you are unable to refresh the content of the apt sources.
Maybe a proxy server problem?

---

### Post by naria on 2008-03-13
I finally work it out!!!
There was nothing wrong with my internet connection.
:D
It was something wrong in my sources.list!
I just coppied the sources.list given in the FAQ and followed the instructions.
Thanx!!!

---

