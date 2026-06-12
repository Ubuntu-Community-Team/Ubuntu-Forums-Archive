---
title: "Need to mirror install and update repositories"
date: 2011-03-11
forum: Repositories &amp; Backports
---

### Post by ACCS on 2011-03-11
I find that I need to install and update Ubuntu on a number of systems, and I'd like to do this over the network (installation from CDs would be a pain, due to required system customizations). The Internet bandwidth available makes network installations from the Internet repositories slow, and I expect that updates will have similar issues.
 
I'd like to make a local repository for a single release (lucid - 10.04.2), containing the files necessary for both initial install and updates. Being new to Ubuntu, I'm not sure as to what the best method would be. While I understand that this would be a non-trivial task, it's a one-time task, instead of one time per system (customizations after CD installation), and I believe it will save time in the long-run.
 
There is a CFEngine setup planned (it could do many of the customizations), but it's not high in the priority queue :(
 
I've looked at the following threads, and didn't find what I needed:
 
[http://ubuntuforums.org/showthread.php?t=7455](http://ubuntuforums.org/showthread.php?t=7455)
[http://ubuntuforums.org/showthread.php?t=1579445](http://ubuntuforums.org/showthread.php?t=1579445)
 
Based on what I saw in the Ubuntu mirrors web page ([https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)), I think I need to set up a local "release mirror", but I can't seem to locate the instructions for doing so.
 
Any help would be appreciated.

---

### Post by ACCS on 2011-03-14
I kept digging, and found this page:
[http://www.ubuntu.com/system/files/u1/AutomatedDeploymentsWP-20090126.pdf](http://www.ubuntu.com/system/files/u1/AutomatedDeploymentsWP-20090126.pdf)

While this paper appears to have been written for Hardy ("Setting up a local mirror", P15), there's another paper that lists the repository locations for Lucid (~2/3 down):
[https://help.ubuntu.com/10.04/serverguide/C/jeos-and-vmbuilder.html](https://help.ubuntu.com/10.04/serverguide/C/jeos-and-vmbuilder.html)
 
Finally, there's the description of the preseed file for Lucid:
[https://help.ubuntu.com/10.04/installation-guide/amd64/preseed-contents.html](https://help.ubuntu.com/10.04/installation-guide/amd64/preseed-contents.html)
 
 
Is there anything I missed that would be useful in this task?
 
TIA

---

### Post by ACCS on 2011-03-17
> **ACCS said:**
> Is there anything I missed that would be useful in this task?
Apparently, I missed something. The apt-mirror completed, but it missed the debian installer (in both main and restricted). Is there something I need to add to get this?
 
My apache logs show the missing files (four, then the install fails). How do I get this mirrored, if apt-mirror didn't pull it in? What else did apt-mirror miss?
 
```
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/Release HTTP/1.1" 200 57242 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/Release HTTP/1.1" 200 57242 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/main/binary-amd64/Release HTTP/1.1" 200 95 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/Release HTTP/1.1" 200 57242 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/Release.gpg HTTP/1.1" 200 189 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/main/debian-installer/binary-amd64/Packages.gz HTTP/1.1" 404 336 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/main/debian-installer/binary-amd64/Packages HTTP/1.1" 404 333 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/restricted/debian-installer/binary-amd64/Packages.gz HTTP/1.1" 404 342 "-" "Wget"
192.168.1.152 - - [17/Mar/2011:14:59:13 -0700] "GET /ubuntu//dists/lucid/restricted/debian-installer/binary-amd64/Packages HTTP/1.1" 404 339 "-" "Wget"
```

---

### Post by ACCS on 2011-03-17
OK. One more configuration issue resolved:D
 
Ubuntu treats these directories as separate repositories. My original mirror.list file was:
 
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
```
 
I added:
 
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main/debian-installer universe/debian-installer
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main/debian-installer universe/debian-installer
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main/debian-installer
```
 
Now, the installation tool has the information it needs to run.
 
It should be noted that there are several entries in the original list that don't have corresponding entries in the debian-installer list. This is because there's no debian installer directory for them, and apt-mirror will fail when it tries to synchronize these non-existent repositories.
 
The local repository problems are now resolved. I need to get the Preseed/Kickstart files working, and I'll be done. As I've previously done this in RedHat/CentOS (Kiskstart only), I'm hoping to not encounter any more major issues.

---

