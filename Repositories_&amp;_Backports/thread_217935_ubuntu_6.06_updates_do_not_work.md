---
title: "ubuntu 6.06 updates do not work"
date: 2006-07-17
forum: Repositories &amp; Backports
---

### Post by abeeber on 2006-07-17
Good day everyone,

I just installed ubuntu 6.06 and am unable to install the updates. I have tried using apt-get udpate and I receive a number of errors. They are posted below..

As I start to troubleshoot, my question is are these errors due to a server/repository issue? Or, are they due to a network access issue with my isp blocking access to this site?

Any help would be greatly appreciated!.

Thanks,

Andrew Beeber.

Errors listed below when running sudo apt-get udpate

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 82.211.81.182 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 82.211.81.182 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 82.211.81.182 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 82.211.81.182 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by abeeber on 2006-07-18
Hi

Just another update, I have updated the sources.list file that was listed in the sticky will not success. I still get the same error.

I am able to browse all the links in the source list, so at this point I have no idea why I get fetch errors. Any ideas?](*,)

---

### Post by abeeber on 2006-07-18
Ok. Changed http to ftp and everything started working. I guess the 6.06 LTS CD's source.list needs to be updated.

---

### Post by pfhorge on 2006-07-19
Fixed the problem for me as well.

The http repositories worked fine for me from home, but not from work. As far as I know, there's no firewall blocking at work, so I'm not sure why the behavior would be different.

---

### Post by catlett on 2006-07-19
It seems to be a server issue at the "Alpaca Farm". That is a  mirror site that holds archive.ubuntu. Both http and ftp archive ubuntu connect there. For some reason ftp is downloading the tar with the repo cache but the http isn't. 
This is the actual page you go to when you run apt-get (or one of the pages, it isn't the only one) You can hit on the links in the repository list and follow them to the repo sites. You will at least know if the site is up and running or if you are being blocked by a firewall etc
[IMG][IMG]http://i80.photobucket.com/albums/j180/brthomas503/archive.jpg[/IMG]

---

### Post by RJARRRPCGP on 2006-07-19
It's likely because of Firestarter. Firestarter may have been causing IP addresses to be blocked back when I had Hoary and connection to 127.0.0.1 always failed.

---

