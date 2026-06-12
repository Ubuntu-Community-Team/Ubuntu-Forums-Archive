---
title: "linux mint installing wine using live cd"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-22
hi.
using linux mint live cd at the moment.
trying to install wine
but unable to install some pacages. is it because I'm using the live cd
here is terminal text
mint@mint ~ $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support
The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 118 not upgraded.
Need to get 11.7MB/11.8MB of archives.
After this operation, 55.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
mint@mint ~ $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-supportmint@mint ~ $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support
The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 118 not upgraded.
Need to get 11.7MB/11.8MB of archives.
After this operation, 55.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
mint@mint ~ $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support
The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 118 not upgraded.
Need to get 11.7MB/11.8MB of archives.
After this operation, 55.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe wine 0.9.59-0ubuntu5
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mint@mint ~ $ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mint@mint ~ $ -fix-missing?
bash: -fix-missing?: command not found
mint@mint ~ $ 

mint@mint ~ $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support
The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 118 not upgraded.
Need to get 11.7MB/11.8MB of archives.
After this operation, 55.1MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
mint@mint ~ $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support
The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 118 not upgraded.
Need to get 11.7MB/11.8MB of archives.
After this operation, 55.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe wine 0.9.59-0ubuntu5
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mint@mint ~ $ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mint@mint ~ $ -fix-missing?
bash: -fix-missing?: command not found
mint@mint ~ $ 


The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 118 not upgraded.
Need to get 11.7MB/11.8MB of archives.
After this operation, 55.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe wine 0.9.59-0ubuntu5
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.59-0ubuntu5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
mint@mint ~ $ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mint@mint ~ $ -fix-missing?
bash: -fix-missing?: command not found
mint@mint ~ $

---

### Post by maybeway36 on 2008-11-22
It looks like your network connection isn't working.
Alternatively, you might need to run sudo apt-get update first.

---

### Post by roger_1960 on 2008-11-22
Hi

As you are running from a live CD, you cant install any packages as there is nowhere to write them to!  The live CD is intended not to alter your existing HD in any way. If you wish to install packages you need to first install Ubuntu/Mint to your HD.  You could try WUBI, a dual boot system or a clean install.

---

### Post by irish66 on 2008-11-22
Thanks you, Roger, and for your contribution Maybe. I thought that might be the problem. Although when i first loaded Ubunto through a live cd, I was able to install pacages, but maybe they were coming from pacage manager, and not through the internet. I guess I'm assuming that pacage manager has a repositry of pacages which only need to be updated through the net.
I'm still using live cd, but if I do install Mint, will let you know if
things worked out.
M

---

