---
title: "Problems with apt-get"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by timmy_1891 on 2012-12-21
I'm trying to install NSF server, but apt-get returns errors stating I should run another commend which I did but that errored as well.

```
timmy@ubuntu:~$ sudo apt-get install nfs-kernel-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 nfs-kernel-server : Depends: libgssglue1 but it is not going to be installed
                     Depends: libnfsidmap2 but it is not going to be installed
                     Depends: libtirpc1 but it is not going to be installed
                     Depends: nfs-common (= 1:1.2.5-3ubuntu3.1) but it is not going to be installed
 teamviewer7:i386 : Depends: bash:i386 (>= 3.0) but it is not going to be installed
                    Depends: libc6:i386 (>= 2.7) but it is not going to be installed
                    Depends: libasound2:i386 but it is not going to be installed
                    Depends: zlib1g:i386 but it is not going to be installed
                    Depends: libxext6:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


```
timmy@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libdpkg-perl libalgorithm-merge-perl g++-4.6 libalgorithm-diff-xs-perl g++ libstdc++6-4.6-dev libalgorithm-diff-perl mscompress
  libc6:i386 libasound2:i386 libgcc1:i386 zlib1g:i386 libxext6:i386 libx11-6:i386 gcc-4.6-base:i386 libxcb1:i386 libxau6:i386
  libxdmcp6:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  base-files gcc-4.6-base:i386 libasound2:i386 libc-bin libc-dev-bin libc6 libc6:i386 libc6-dev libgcc1:i386 libx11-6:i386
  libxau6:i386 libxcb1 libxcb1:i386 libxdmcp6:i386 libxext6:i386 zlib1g:i386
Suggested packages:
  libasound2-plugins:i386 libasound2-python:i386 glibc-doc glibc-doc:i386 locales:i386
Recommended packages:
  manpages-dev
The following packages will be REMOVED:
  teamviewer7:i386
The following NEW packages will be installed:
  base-files gcc-4.6-base:i386 libasound2:i386 libc6:i386 libgcc1:i386 libx11-6:i386 libxau6:i386 libxcb1:i386 libxdmcp6:i386
  libxext6:i386 zlib1g:i386
The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dev libxcb1
5 upgraded, 11 newly installed, 1 to remove and 90 not upgraded.
9 not fully installed or removed.
Need to get 0 B/14.4 MB of archives.
After this operation, 68.3 MB disk space will be freed.
Do you want to continue [Y/n]? y
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true

```

Seemed to start earlier when trying to install teamviewer, so as suggested in another post:

```
sudo dpkg -r teamviewer7
dpkg: warning: 'sh' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

```

Finally:

```
sudo apt-get update && sudo apt-get -f install
...
Fetched 2,287 kB in 6s (355 kB/s)
E: Problem executing scripts APT::Update::Post-Invoke-Success 'touch /var/lib/apt/periodic/update-success-stamp 2>/dev/null || true'
E: Sub-process returned an error code

```

Then:

```
sudo dpkg --clear-avail
```

Which produced no output. Now I'm stumped and stuck. Any ideas?

Thanks in advance
Tim

--
Ubuntu Linux 12.04.1

---

