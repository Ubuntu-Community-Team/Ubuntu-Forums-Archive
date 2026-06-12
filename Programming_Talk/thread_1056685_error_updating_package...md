---
title: "error: updating package.."
date: 2009-02-01
forum: Programming Talk
---

### Post by admsys on 2009-02-01
Hello,

I need solution or clue how to resolve the issue.I can't install gcc from CD or update package.

See the code..

```

localhost@esiahost:~$ sudo apt-get install gcc build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  binutils cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc-4.1 libc6-dev
  libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  binutils-doc cpp-doc gcc-4.1-locales debian-keyring gcc-4.1-doc lib64stdc++6
  manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc
  libc6-dev-amd64 lib64gcc1 glibc-doc libstdc++6-4.1-doc diff-doc
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential cpp cpp-4.1 dpkg-dev g++ g++-4.1 gcc gcc-4.1
  libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
0 upgraded, 13 newly installed, 0 to remove and 65 not upgraded.
Need to get 0B/12.7MB of archives.
After unpacking 48.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/b/binutils/binutils_2.17.20070103cvs-0ubuntu2_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/glibc/libc6-dev_2.5-0ubuntu14_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-4.1/cpp-4.1_4.1.2-0ubuntu4_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-defaults/cpp_4.1.2-1ubuntu1_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-4.1/gcc-4.1_4.1.2-0ubuntu4_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-defaults/gcc_4.1.2-1ubuntu1_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-4.1/libstdc++6-4.1-dev_4.1.2-0ubuntu4_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-4.1/g++-4.1_4.1.2-0ubuntu4_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/g/gcc-defaults/g++_4.1.2-1ubuntu1_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/p/patch/patch_2.5.9-4_i386.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/d/dpkg/dpkg-dev_1.13.24ubuntu6_all.deb  MD5Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/pool/main/b/build-essential/build-essential_11.3_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
localhost@esiahost:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
localhost@esiahost:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418) feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty Release.gpg
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:1 http://security.ubuntu.com feisty-security Release.gpg [189B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [189B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/main Packages
Ign http://us.archive.ubuntu.com feisty/main Packages
Ign http://us.archive.ubuntu.com feisty/restricted Packages
Ign http://us.archive.ubuntu.com feisty/main Sources
Ign http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Ign http://us.archive.ubuntu.com feisty/universe Packages
Ign http://us.archive.ubuntu.com feisty/universe Sources
Ign http://us.archive.ubuntu.com feisty/multiverse Packages
Ign http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Ign http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Err http://us.archive.ubuntu.com feisty/main Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/restricted Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/main Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/restricted Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/universe Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/universe Sources
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/multiverse Packages
  404 Not Found [IP: 91.189.88.45 80]
Err http://us.archive.ubuntu.com feisty/multiverse Sources
  404 Not Found [IP: 91.189.88.45 80]
Get:3 http://us.archive.ubuntu.com feisty-updates/main Sources [63.6kB]
99% [3 Sources gzip 0]
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com feisty-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 3B in 3s (1B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

