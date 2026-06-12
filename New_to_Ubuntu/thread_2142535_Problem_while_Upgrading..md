---
title: "Problem while Upgrading."
date: 2013-05-06
forum: New to Ubuntu
---

### Post by Anupam123 on 2013-05-06
Hello People,
I am a Beginner.
I am using Ubuntu 12.04.1 LTS

when i type : sudo apt-get upgrade, i get the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.4 is installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.4) but 2.15-0ubuntu10.3 is installed
E: Unmet dependencies. Try using -f.

when i  sudo apt-get install ubuntu-restricted-extras

it says :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.4 is to be installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.4) but 2.15-0ubuntu10.3 is to be installed
 ubuntu-restricted-extras : Depends: ubuntu-restricted-addons but it is not going to be installed
                            Recommends: ttf-mscorefonts-installer but it is not going to be installed
                            Recommends: unrar but it is not going to be installed
                            Recommends: gstreamer0.10-plugins-bad-multiverse but it is not going to be installed
                            Recommends: libavcodec-extra-53 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

when i do this : sudo apt-get -f  install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be REMOVED:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 1 to remove and 260 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,941 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:i386
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 145636 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.3 (using .../libc6_2.15-0ubuntu10.4_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

when i do sudo apt-get install synaptic

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.4 is to be installed
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.4) but 2.15-0ubuntu10.3 is to be installed
 synaptic : Depends: libept1.4.12 but it is not installable
            Depends: libvte9 (>= 1:0.24.0) but it is not installable
            Recommends: rarian-compat but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



Please Help !

---

### Post by lovebluesky2009 on 2013-05-06
try```
sudo apt-get -f install
```

---

### Post by Impavidus on 2013-05-06
Then try upgrading those 260 not upgraded packages, taking into account any changed dependencies. There are old versions amongst those packages that may be incompatible with the latest versions of packages available from the repositories, that you are trying to install.
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by Anupam123 on 2013-05-07
Thank you people.
I tried both your solutions.
And I was succesfull in installing the synaptic package manager.

---

