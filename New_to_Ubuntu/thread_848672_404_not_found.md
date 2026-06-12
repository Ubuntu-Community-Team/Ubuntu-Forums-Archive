---
title: "404 not found"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by gulmer on 2008-07-03
When ever I get updates and the update manager checks the package info, I get a error message:Failed to fetch [http://ppa.launchpad.net/amaranth/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ppa.launchpad.net/amaranth/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/amaranth/ubuntu/dists/hardy/main/source/Sources.gz](http://ppa.launchpad.net/amaranth/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://ubuntu.org.ua/getdeb/Packages.gz](http://ubuntu.org.ua/getdeb/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
  What do I do with this info?is there something that needs fixing?

---

### Post by sayakb on 2008-07-03
These resources seem to be removed from the respective web locations. Goto System->Administration->Software sources, click on *Third-party software* and **uncheck** these resources. Click Reload when prompted to and retry updating.

---

### Post by G1ZmO65 on 2008-07-04
I am also getting frequent 404 errors

[I]Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main libglib2.0-0 2.16.3-1ubuntu2
  404 Not Found[/I]

Surely the hardy updates shoul be there as they are not third party?

---

### Post by hyper_ch on 2008-07-04
sometimes a server is down and then you can't reach it... or there might be some dns issues or or or....

if it's like that for 2-3 days then you should worry ;)

---

### Post by gulmer on 2008-07-06
> **LinuxIsInnovation said:**
> These resources seem to be removed from the respective web locations. Goto System->Administration->Software sources, click on *Third-party software* and **uncheck** these resources. Click Reload when prompted to and retry updating.

Thanks for the help, solved the problem

---

