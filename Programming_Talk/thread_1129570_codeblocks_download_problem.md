---
title: "codeblocks download problem"
date: 2009-04-18
forum: Programming Talk
---

### Post by swappo1 on 2009-04-18
Hello,

I am trying to download codeblocks and I got the following errors.
```
scott@scott-laptop:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  codeblocks-common codeblocks-contrib-common
Suggested packages:
  wx-common
The following NEW packages will be installed:
  codeblocks codeblocks-common codeblocks-contrib codeblocks-contrib-common libcodeblocks0 libwxsmithlib0
0 upgraded, 6 newly installed, 0 to remove and 13 not upgraded.
Need to get 11.5MB of archives.
After this operation, 33.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://lgp203.free.fr hardy/universe codeblocks-common 8.02svn5534 [2614kB]
Get:2 http://lgp203.free.fr hardy/universe libcodeblocks0 8.02svn5534 [1916kB]
Get:3 http://lgp203.free.fr hardy/universe codeblocks 8.02svn5534 [2370kB]
Get:4 http://lgp203.free.fr hardy/universe codeblocks-contrib-common 8.02svn5534 [342kB]
Get:5 http://lgp203.free.fr hardy/universe libwxsmithlib0 8.02svn5534 [1267kB]
Get:6 http://lgp203.free.fr hardy/universe codeblocks-contrib 8.02svn5534 [3026kB]
Fetched 6B in 1s (4B/s)                      
Failed to fetch http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks-common_8.02svn5534_all.deb  Size mismatch
Failed to fetch http://lgp203.free.fr/ubuntu/../pool/codeblocks/libcodeblocks0_8.02svn5534_amd64.deb  Size mismatch
Failed to fetch http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks_8.02svn5534_amd64.deb  Size mismatch
Failed to fetch http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks-contrib-common_8.02svn5534_all.deb  Size mismatch
Failed to fetch http://lgp203.free.fr/ubuntu/../pool/codeblocks/libwxsmithlib0_8.02svn5534_amd64.deb  Size mismatch
Failed to fetch http://lgp203.free.fr/ubuntu/../pool/codeblocks/codeblocks-contrib_8.02svn5534_amd64.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
I tried apt-get update and --fix-missing and still I get these messages.  Any suggestions?

---

### Post by Josef_A on 2009-04-19
It kind of looks like the fellow running that repo breaks things once in between.

Try removing all your codeblocks packages, commenting out the line for the repo in your sources.list, running aptitude update, uncommenting, aptitude update again, and then reinstalling the relevant packages.

---

### Post by swappo1 on 2009-04-19
Josef_A, I followed your advice, now I am getting the following:
```
scott@scott-laptop:~$ sudo apt-get install libcodeblocks0 codeblocks libwxsmithlib0 codeblocks-contrib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  codeblocks-common codeblocks-contrib-common
Suggested packages:
  wx-common
The following NEW packages will be installed:
  codeblocks codeblocks-common codeblocks-contrib codeblocks-contrib-common
  libcodeblocks0 libwxsmithlib0
0 upgraded, 6 newly installed, 0 to remove and 13 not upgraded.
Need to get 11.5MB of archives.
After this operation, 33.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://lgp203.free.fr hardy/universe codeblocks-common 8.02svn5534 [2614kB]
Get:2 http://lgp203.free.fr hardy/universe libcodeblocks0 8.02svn5534 [1915kB]
Get:3 http://lgp203.free.fr hardy/universe codeblocks 8.02svn5534 [2370kB]
Get:4 http://lgp203.free.fr hardy/universe codeblocks-contrib-common 8.02svn5534 [342kB]
Get:5 http://lgp203.free.fr hardy/universe libwxsmithlib0 8.02svn5534 [1267kB]
Get:6 http://lgp203.free.fr hardy/universe codeblocks-contrib 8.02svn5534 [3025kB]
Fetched 6B in 2s (3B/s)
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Firestom on 2009-04-19
You should rather use Synaptic if you are unfamiliar with the command line. You do not need to pass all those packages as arguments for apt-get. You can only ask for codeblocks and it should install the others within and solve dependencies for these other packages. What you are doing messes up apt-get, as it waits for codeblocks to be done to pass on to libwxwidgets. So just try sudo apt-get install codeblocks and it should work fine. Else, think about the order you need them to be installed and pass the most important and independant of other packages you want to install.

Elseway, just go to Code::Blocks web site and download the debian packages.

---

### Post by swappo1 on 2009-04-19
Firestom, sudo apt-get install codeblocks worked.  I did try synaptic and the .deb from codeblocks and I had the same problem with each of these.  I am not unfamiliar with the command line since this is what I normally use.  I was following a tutorial for downloading and installing codeblocks since I didn't have the dependencies and codeblocks wasn't in the package manager and wasn't updating either. Thanks.

---

