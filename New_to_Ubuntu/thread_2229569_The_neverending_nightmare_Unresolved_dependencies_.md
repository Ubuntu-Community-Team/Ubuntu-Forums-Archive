---
title: "The neverending nightmare: Unresolved dependencies when installing php5-fpm"
date: 2014-06-13
forum: New to Ubuntu
---

### Post by kean2 on 2014-06-13
Currently running Ubuntu 10.04, lucid.

I'm trying to install php on top of nginx.
In order to do this I need php5-fpm.

Trying to install it gets me:

> The following packages are BROKEN:
  dpkg libapache2-mod-php5 libc-dev-bin libc6-dev libnih1 libxml2 openssh-client openssh-server php5-cli
  php5-common php5-fpm
The following NEW packages will be installed:
  libalgorithm-diff-perl{a} libalgorithm-merge-perl{a} libdpkg-perl{a} libssl1.0.0{a} multiarch-support{a}
  ncurses-term{a}
The following packages will be upgraded:
  dpkg-dev libc-bin libc6
8 packages upgraded, 7 newly installed, 0 to remove and 84 not upgraded.
Need to get 16.6MB of archives. After unpacking 21.1MB will be used.
The following packages have unmet dependencies:
  openssh-server: Depends: libgssapi-krb5-2 (>= 1.10+dfsg~) but 1.8.1+dfsg-2ubuntu0.11 is installed.
  libapache2-mod-php5: Depends: php5-common (= 5.3.2-1ubuntu4.24) but 5.4.6-1ubuntu1.8 is to be installed.
  openssh-client: Depends: libgssapi-krb5-2 (>= 1.10+dfsg~) but 1.8.1+dfsg-2ubuntu0.11 is installed.
  dpkg: PreDepends: liblzma5 (>= 5.1.1alpha+20120614) which is a virtual package.
        PreDepends: tar (>= 1.23) but 1.22-2ubuntu1 is installed.
  libxml2: Depends: liblzma5 (>= 5.1.1alpha+20120614) which is a virtual package.
  libc6-dev: Depends: libc6 (= 2.11.1-0ubuntu7.13) but 2.15-0ubuntu20.2 is to be installed.
  php5-cli: Depends: php5-common (= 5.3.2-1ubuntu4.24) but 5.4.6-1ubuntu1.8 is to be installed.
  libc-dev-bin: Depends: libc6 (< 2.12) but 2.15-0ubuntu20.2 is to be installed.
  php5-fpm: Depends: libdb5.1 which is a virtual package.
            Depends: libpcre3 (>= 8.10) but 7.8-3build1 is installed.
  php5-common: Depends: psmisc (>= 22.15-1~) but 22.10-1 is installed.
  libnih1: Depends: libc6 (< 2.12) but 2.15-0ubuntu20.2 is to be installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
dpkg [1.15.5.6ubuntu4.6 (now)]
dpkg-dev [1.15.5.6ubuntu4.6 (now)]
libc-bin [2.11.1-0ubuntu7.13 (lucid-updates, lucid-security, now)]
libc6 [2.11.1-0ubuntu7.13 (lucid-updates, lucid-security, now)]
libdpkg-perl [Not Installed]
libssl1.0.0 [Not Installed]
libxml2 [2.7.6.dfsg-1ubuntu1.10 (now)]
openssh-client [1:5.3p1-3ubuntu7.1 (lucid-updates, lucid-security, now)]
openssh-server [1:5.3p1-3ubuntu7.1 (lucid-updates, lucid-security, now)]
php5-common [5.3.2-1ubuntu4.24 (lucid-updates, lucid-security, now)]
php5-fpm [Not Installed]


Score is -9485

Accept this solution? [Y/n/q/?]



Of course, hitting yes doesn't do anything. I've scoured countless threads addressing "unmet dependencies" and all of them are so specific that none of them were really helpful. The top-rated answer on stackoverflow for this sort of thing tells me to upgrade my distrobution, which isn't really an option I can risk--if I can't even do this part, I know I can't handle cleanup on a botched distro upgrade for a near-production server.

For example, with the above entries:

> 
The following packages have unmet dependencies:
  openssh-server: Depends: libgssapi-krb5-2 (>= 1.10+dfsg~) but 1.8.1+dfsg-2ubuntu0.11 is installed.
  libapache2-mod-php5: Depends: php5-common (= 5.3.2-1ubuntu4.24) but 5.4.6-1ubuntu1.8 is to be installed.
  openssh-client: Depends: libgssapi-krb5-2 (>= 1.10+dfsg~) but 1.8.1+dfsg-2ubuntu0.11 is installed.


If I try to apt-get install openssh-server, it lists openssh-client as a dependency.
If I try to apt-get install openssh-client, it lists openssh-server as a dependency.
If I try for both, it lists them both as well as something else.

The problem is NOT related to having removed things from my apt sources list. I've only added things to it.

How can I even begin to address all of this?

---

### Post by QIII on 2014-06-13
Is this the server version?

---

### Post by kean2 on 2014-06-13
Thanks for the swift response. Yeah, this is the server (non-GUI) version.

---

### Post by tgalati4 on 2014-06-14
Welcome to *dependency file hell*.  Although I don't recommend it, you can temporarily set your sources.list file to 10.10 repositories and try the update and upgrade.  Then quickly set the dependencies back to 10.04.  That will pull in the newer frameworks and possibly wake you from your nightmare.  

A better solution is to backup and start a fresh server with 12.04.

---

### Post by squakie on 2014-06-14
What did you add to the repository list?  What package(s) did you get from those repositories?  I don't remember the command at the moment, but there is a way with apt to show what packages are dependent on a specific library, etc..  It's possible that something else already installed is preventing some of this from being resolved.

I'll try to find that apt command and post back.

---

### Post by J_Me on 2014-06-14
Not sure if this helps, I followed a tut on installing nginx and php(raspbian OS) which worked out ok. The needed packages were
```
php5-fpm php5-suhosin php5-gd php-apc php5-mcrypt php5-cli php5-curl memcached php5-memcache
``` But looking at the errors your getting a upgrade to a more recent OS version seems to be the only real solution.

Also
```
apt-cache depends php5-fpm
``` will show you the dependencies

---

