---
title: "Wireless Problem On Eee PC"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by fiveharmony on 2008-08-20
I have the wireless problem on my Eee PC 900. I have installed Ubuntu 8.04.1 Lts Desktop Edition. I used the life cd that sent by Media Motion c/o Ubuntu-Kubuntu-Edubuntu from Netherlands. I have tried the way that written [on this page]("http://justingill.com/blog/2008/03/16/the-perfect-out-of-the-box-asus-eee-pc-linux-install-ubuntu-804/") but my wireless still in problem. Here is the result of my process:

delis@delis-notebook:~$ sudo su
[sudo] password for delis:
root@delis-notebook:/home/delis# sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy Release.gpg
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [45.1kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [11.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [26.2kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [3708B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3874B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy Release
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates Release
Get:6 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/main Packages [1176kB]
Get:7 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/restricted Packages [7452B]
Get:8 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/main Sources [335kB]
Get:9 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/restricted Sources [1632B]
Get:10 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/universe Packages [4301kB]
Get:11 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/universe Sources [1325kB]
Get:12 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/multiverse Packages [175kB]
Get:13 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy/multiverse Sources [60.5kB]
Get:14 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/main Packages [14B]
Get:15 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/restricted Packages [14B]
Get:16 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/main Sources [14B]
Get:17 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/restricted Sources [14B]
Get:18 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/universe Packages [14B]
Get:19 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/universe Sources [14B]
Get:20 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/multiverse Packages [14B]
Get:21 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) hardy-updates/multiverse Sources [14B]
Fetched 21B in 28s (1B/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.bz2) Hash Sum mismatch

W: Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2](http://id.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2) Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@delis-notebook:/home/delis# sudo apt-get install build-essential
Reading package lists… Done
Building dependency tree
Reading state information… Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
root@delis-notebook:/home/delis# wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
–17:55:43– [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
=> `madwifi-ng-r2756+ar5007.tar.gz.2&#8242;
Resolving snapshots.madwifi.org… 217.24.1.134
Connecting to snapshots.madwifi.org|217.24.1.134|:80… connected.
HTTP request sent, awaiting response… 200 OK
Length: 485 [application/x-gzip]

100%[====================================>] 485 –.–K/s

17:55:48 (25.18 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz.2&#8242; saved [485/485]

root@delis-notebook:/home/delis# tar zxvf madwifi-ng-r2756+ar5007.tar.gz
madwifi-ng-r2756+ar5007/
madwifi-ng-r2756+ar5007/README
root@delis-notebook:/home/delis# cd madwifi-ng-r2756+ar5007
root@delis-notebook:/home/delis/madwifi-ng-r2756+ar5007# make clean
make: *** No rule to make target `clean’. Stop.
root@delis-notebook:/home/delis/madwifi-ng-r2756+ar5007# make
make: *** No targets specified and no makefile found. Stop.
root@delis-notebook:/home/delis/madwifi-ng-r2756+ar5007# sudo make install
make: *** No rule to make target `install’. Stop.
root@delis-notebook:/home/delis/madwifi-ng-r2756+ar5007#

What must be done? How to solve this problem?
Thanks so much.

---

### Post by alienexplorers on 2008-08-20
[http://samiux.wordpress.com/2008/04/26/ubuntu-804-lts-on-asus-eee-pc/]("http://samiux.wordpress.com/2008/04/26/ubuntu-804-lts-on-asus-eee-pc/")

---

