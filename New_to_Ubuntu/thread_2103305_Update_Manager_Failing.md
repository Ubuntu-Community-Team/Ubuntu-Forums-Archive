---
title: "Update Manager Failing"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by DeK0521 on 2013-01-09
Hey everyone here on ubuntu forums. i have no real experience with linux yet, but i thought i would give it a try since Microsoft's windows OS keeps disappointing me. I installed ubuntu12.04, 32 bit on my SAGER NP 5160 notebook.

CPU: INTEL CORE i5 2ND GEN 
RAM:4GB
HDD:500GB
GPU: GEFORCE GT 540M

    after the install i keep running into problems, one of them happens when i try to update with up date mannager
```

PACKAGE OPERATION FAILED 

THE INSTALLATION OR REMOVAL OF A SOFTWARE PACKAGE FAILED 

installArchives() failed:  Extracting templates from packages: 11%% Extracting templates from packages: 22%% Extracting templates from packages: 33%% Extracting templates from packages: 44%% Extracting templates from packages: 55%% Extracting templates from packages: 66%% Extracting templates from packages: 77%% Extracting templates from packages: 88%% Extracting templates from packages: 99%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 11%% Extracting templates from packages: 22%% Extracting templates from packages: 33%% Extracting templates from packages: 44%% Extracting templates from packages: 55%% Extracting templates from packages: 66%% Extracting templates from packages: 77%% Extracting templates from packages: 88%% Extracting templates from packages: 99%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 11%% Extracting templates from packages: 22%% Extracting templates from packages: 33%% Extracting templates from packages: 44%% Extracting templates from packages: 55%% Extracting templates from packages: 66%% Extracting templates from packages: 77%% Extracting templates from packages: 88%% Extracting templates from packages: 99%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 11%% Extracting templates from packages: 22%% Extracting templates from packages: 33%% Extracting templates from packages: 44%% Extracting templates from packages: 55%% Extracting templates from packages: 66%% Extracting templates from packages: 77%% Extracting templates from packages: 88%% Extracting templates from packages: 99%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 169084 files and directories currently installed.) 
Preparing to replace base-files 6.5ubuntu6.2 (using .../base-files_6.5ubuntu6.4_i386.deb) ... 
Unpacking replacement base-files ... 
Processing triggers for install-info ... 
Processing triggers for man-db ... 
Processing triggers for plymouth-theme-ubuntu-text ... 
update-initramfs: deferring update (trigger activated) 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae 
Setting up base-files (6.5ubuntu6.4) ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 169085 files and directories currently installed.) 
Preparing to replace coreutils 8.13-3ubuntu3 (using .../coreutils_8.13-3ubuntu3.2_i386.deb) ... 
Unpacking replacement coreutils ... 
Processing triggers for man-db ... 
Processing triggers for install-info ... 
Setting up coreutils (8.13-3ubuntu3.2) ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 169085 files and directories currently installed.) 
Preparing to replace login 1:4.1.4.2+svn3283-3ubuntu5 (using .../login_1%%3a4.1.4.2+svn3283-3ubuntu5.1_i386.deb) ... 
Unpacking replacement login ... 
Processing triggers for man-db ... 
Setting up login (1:4.1.4.2+svn3283-3ubuntu5.1) ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 169085 files and directories currently installed.) 
Preparing to replace perl 5.14.2-6ubuntu2.1 (using .../perl_5.14.2-6ubuntu2.2_i386.deb) ... 
Unpacking replacement perl ... 
Preparing to replace libperl5.14 5.14.2-6ubuntu2.1 (using .../libperl5.14_5.14.2-6ubuntu2.2_i386.deb) ... 
Unpacking replacement libperl5.14 ... 
Preparing to replace perl-base 5.14.2-6ubuntu2.1 (using .../perl-base_5.14.2-6ubuntu2.2_i386.deb) ... 
Unpacking replacement perl-base ... 
Processing triggers for man-db ... 
Setting up perl-base (5.14.2-6ubuntu2.2) ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 169085 files and directories currently installed.) 
Preparing to replace perl-modules 5.14.2-6ubuntu2.1 (using .../perl-modules_5.14.2-6ubuntu2.2_all.deb) ... 
Unpacking replacement perl-modules ... 
Preparing to replace libc-dev-bin 2.15-0ubuntu10 (using .../libc-dev-bin_2.15-0ubuntu10.3_i386.deb) ... 
Unpacking replacement libc-dev-bin ... 
Preparing to replace libc6-dev 2.15-0ubuntu10 (using .../libc6-dev_2.15-0ubuntu10.3_i386.deb) ... 
Unpacking replacement libc6-dev ... 
Preparing to replace libc-bin 2.15-0ubuntu10 (using .../libc-bin_2.15-0ubuntu10.3_i386.deb) ... 
Unpacking replacement libc-bin ... 
Processing triggers for man-db ... 
Setting up libc-bin (2.15-0ubuntu10.3) ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 169085 files and directories currently installed.) 
Preparing to replace libc6 2.15-0ubuntu10 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ... 
Unpacking replacement libc6 ... 
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error 
dpkg-deb: error: subprocess paste returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./usr/lib/i386-linux-gnu/gconv/IBM933.so' 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb 
Error in function:  
Setting up libperl5.14 (5.14.2-6ubuntu2.2) ... 
dpkg: dependency problems prevent configuration of libc6-dev: 
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.3); however: 
  Version of libc6 on system is 2.15-0ubuntu10. 
dpkg: error processing libc6-dev (--configure): 
 dependency problems - leaving unconfigured 
Setting up libc-dev-bin (2.15-0ubuntu10.3) ... 
Setting up perl-modules (5.14.2-6ubuntu2.2) ... 
Setting up perl (5.14.2-6ubuntu2.2) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 

```

After that i cannot access software center it gives me this message:

SORRY UBUNTU 12.04 HAS EXPERIENCED AN INTERNAL ERROR

when i try restarting my computer it takes me to a black screen for like 10 minutes then ubuntu says that there is a error in my  drive partitions and press F to try and fix them. So i push F and Ubuntu says that my drive has been repaired and continues to boot to desktop but i still cannot install new software packages and it does that every time i reboot.

if anyone can anyone help or have experience with similar  issues i would appreciate any feedback i realy want to start using ubuntu but i cant use it like this.

---

### Post by Sef on 2013-01-09
Let's check your partitions to see if there is a problem with them.

Click on the ubuntu logo, then type terminal and click on it.  Then copy and put in this code: ```
sudo fdisc -l
```. 

Last copy and paste the results in here.

---

### Post by iponeverything on 2013-01-09
open a prompt and remove the libc6-dev package with the command:

```
sudo dpkg -r libc6-dev
```

then try to rerun the update.

---

### Post by DeK0521 on 2013-01-09
okay so  i tried copying and pasting sudo fdisc -l in terminal and it tells me :sudo: fdisc: command not found

i then tried :sudo dpkg -r libc6-dev and reupdating through update manager but hit install it tells me :THE PACKAGE MANAGER SYSTEM IS BROKEN

The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.15-0ubuntu10) but 2.15-0ubuntu10.3 is installed

---

### Post by Bashing-om on 2013-01-09
DeK0521; Hi !

Typo: "fdisc"  should be "fdisk -l"

Try this simpler approach to repair the file manager:
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by DeK0521 on 2013-01-09
hey Bashing-om thank you i typed fdisk - l and this is what came back 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c71c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968572927   484285440   83  Linux
/dev/sda2       968574974   976771071     4098049    5  Extended
/dev/sda5       968574976   976771071     4098048   82  Linux swap / Solaris

and i tried 

dek@dek-W150HNM-W170HN:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6
1 upgraded, 0 newly installed, 0 to remove and 258 not upgraded.
Need to get 0 B/3,940 kB of archives.
After this operation, 20.5 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 168567 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
Unpacking replacement libc6 ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/i386-linux-gnu/gconv/IBM933.so'
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2013-01-09
DeK0521;

Does not look to bad, I have not seen this error before and will take some thought on my part; Late here and I am tired and not think'n too good presently. I am going to sleep on it and get back at ya in my later AM.

[INDENT][INDENT][INDENT]where there is a will, there is a way <== BDQ
 
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-01-10
DeK0521;

Try this from a cold boot (wait a couple of minutes to restart, so all settles out):
```

sudo dpkg --configure -a
sudo apt-get -f install

```I would prefer to repair the lib package as try and replace it as it is a crucial library package.
[INDENT][INDENT]see what haps <== BDQ

[/INDENT][/INDENT]

---

