---
title: "Package Catalog cannot be repaired"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by taker101 on 2011-09-14
So I have been trying to download python, and it needs to to repair the package catalog, however every time i try to repair it, i receive an error. From a different thread that was not solved (obviously relating to same issue) the person was asked to type the following commands into terminal so i did;
sudo apt-get autoclean             <-- no error
sudo apt-get install -f           <-- error
sudo dpkg --configure -a            <-- error
sudo apt-get check               <-- error

**result from typing sudo apt-get install -f:**
sahar@ubuntu:~$ sudo apt-get install -f
[sudo] password for sahar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8-generic linux-headers-2.6.38-8
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-core
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
11 not fully installed or removed.
Need to get 0 B/28.0 MB of archives.
After this operation, 2,142 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155981 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.3.2-1ubuntu4 (using .../libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Unpacking replacement libreoffice-core ...
xz: (stdin): Compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/basis3.3/program/libsvxlx.so'
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

[B]result from sudo dpkg --configure -a:
[/B]sahar@ubuntu:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-help-en-us:
 libreoffice-help-en-us depends on libreoffice-writer | language-support-translations-en; however:
  Package libreoffice-writer is not configured yet.
  Package language-support-translations-en is not installed.
dpkg: error processing libreoffice-help-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however:
  Version of libreoffice-core on system is 1:3.3.2-1ubuntu4.
 libreoffice-calc depends on libreoffice-base-core (= 1:3.3.3-1ubuntu2); however:
  Package libreoffice-base-core is not configured yet.
dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-emailmerge:
 libreoffice-emailmerge depends on python-uno; however:
  Package python-uno is not configured yet.
dpkg: error processing libreoffice-emailmerge (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libreoffice-math
 libreoffice-impress
 libreoffice-writer
 libreoffice-base-core
 libreoffice-gnome
 libreoffice-gtk
 python-uno
 libreoffice-draw
 libreoffice-help-en-us
 libreoffice-calc
 libreoffice-emailmerge

[B]result from sudo apt-get check:
[/B]sahar@ubuntu:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 libreoffice-calc : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
 python-uno : Depends: libreoffice-core (= 1:3.3.3-1ubuntu2) but 1:3.3.2-1ubuntu4 is installed
E: Unmet dependencies. Try using -f.

---

### Post by jasonrisenburg on 2011-09-14
Do you keep everything on your  backed up?To me a relative noob, I sounds like your in a spot. I keep a harddrive backed up of everthing I need. I might suggest you do as well. or at least on disc.

---

### Post by gmargo on 2011-09-15
> **taker101 said:**
> 
Preparing to replace libreoffice-core 1:3.3.2-1ubuntu4 (using .../libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb) ...
Unpacking replacement libreoffice-core ...
xz: (stdin): [COLOR=Red]Compressed data is corrupt[/COLOR]
dpkg-deb: error: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/basis3.3/program/libsvxlx.so'
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Pay attention to the error.  You almost certainly have a corrupted .deb file.

Remove this file so that a fresh copy is downloaded, then try again:
/var/cache/apt/archives/libreoffice-core_1%3a3.3.3-1ubuntu2_amd64.deb

---

### Post by 54696D on 2011-09-15
Hi,
why do you want to download Python?
In Ubuntu Python is installed per default.

---

### Post by taker101 on 2011-09-15
Thanks for responding but I had a friend help me out and he fix the problem. Would explain it if I understood it**

---

