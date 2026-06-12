---
title: "Oracle Java."
date: 2015-01-22
forum: New to Ubuntu
---

### Post by murat_tasova on 2015-01-22
Hi There,

I get a little bit frustrated. I try to install Oracle Java SE and get constantly an error like below:

Installing from local file /var/cache/oracle-jdk8-installer/jdk-8u31-linux-x64.tar.gz
Removing outdated cached downloads...
update-alternatives: error: alternative link /usr/bin/javaws is already managed by javac
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

It doesn matter automatic or manual installation. 
[http://www.webupd8.org/2014/03/how-to-install-oracle-java-8-in-debian.html](http://www.webupd8.org/2014/03/how-to-install-oracle-java-8-in-debian.html) doesnt work.

I need Java for managment of EMC storage enviroment. I dont want to go back to windows :mad:

---

### Post by slickymaster on 2015-01-22
Can you please try the following at a terminal window:```
sudo dpkg -P oracle-java8-installer
sudo apt-get -f install
```

---

### Post by murat_tasova on 2015-01-22
Hi master :)

Did that :

```
root@LT13000:~# sudo dpkg -P oracle-java8-installer
dpkg: dependency problems prevent removal of oracle-java8-installer:
 libatk-wrapper-java depends on default-jre | java2-runtime; however:
  Package default-jre is not installed.
  Package oracle-java8-installer which provides default-jre is to be removed.
  Package java2-runtime is not installed.
  Package oracle-java8-installer which provides java2-runtime is to be removed.
 libatk-wrapper-java-jni:amd64 depends on default-jre | java2-runtime; however:
  Package default-jre is not installed.
  Package oracle-java8-installer which provides default-jre is to be removed.
  Package java2-runtime is not installed.
  Package oracle-java8-installer which provides java2-runtime is to be removed.
 libatk-wrapper-java depends on default-jre | java2-runtime; however:
  Package default-jre is not installed.
  Package oracle-java8-installer which provides default-jre is to be removed.
  Package java2-runtime is not installed.
  Package oracle-java8-installer which provides java2-runtime is to be removed.
 libatk-wrapper-java
dpkg: error processing package oracle-java8-installer (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 oracle-java8-installer


---
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ca-certificates-java default-jre-headless fonts-dejavu-extra
  libatk-wrapper-java libatk-wrapper-java-jni libbonobo2-0 libbonobo2-common
  libgconf2-4 libgnome2-0 libgnome2-bin libgnome2-common libgnomevfs2-0
  libgnomevfs2-common libidl-common libidl0 liborbit-2-0 liborbit2
  openjdk-7-jre-headless tzdata-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up oracle-java8-installer (8u31+8u33arm-1~webupd8~0) ...
Installing from local file /var/cache/oracle-jdk8-installer/jdk-8u31-linux-x64.tar.gz
Removing outdated cached downloads...
update-alternatives: error: alternative link /usr/bin/javaws is already managed by javac
dpkg: error processing package oracle-java8-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 oracle-java8-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@LT13000:~#
```

---

### Post by slickymaster on 2015-01-22
Please run:```
sudo dpkg -r --force-all oracle-java8-installer
```and once again post the output you got, [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") for the effect.

---

