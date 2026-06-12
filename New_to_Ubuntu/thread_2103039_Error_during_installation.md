---
title: "Error during installation"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by SHINYFATHIMA on 2013-01-09
When i am trying to install rar using the command 

*[COLOR=DarkRed]sudo apt-get install unrar[/COLOR]*

i am getting the below error . PLease help me to resolve this issue.

[B][COLOR=Red]After this operation, 258kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  unrar
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse unrar i386 1:3.9.10-1
  404  Not Found [IP: 91.189.91.13 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.9.10-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.9.10-1_i386.deb)  404  Not Found [IP: 91.189.91.13 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/COLOR][/B]

---

### Post by deadflowr on 2013-01-09
You'll have to update your repos. Maverick is dead.

If you feel the need not to upgrade to a supported version of Ubuntu use the method suggested here:

[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions]("http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions")

---

