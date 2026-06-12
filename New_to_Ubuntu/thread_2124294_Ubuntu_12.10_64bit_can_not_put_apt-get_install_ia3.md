---
title: "Ubuntu 12.10 64bit can not put apt-get install ia32-libs?"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by JWebDev on 2013-03-10
Please tell me, that my actions. I need this library, because without it does not want to operate "adb" for programming under Android.

```


root@jdev-VM:~# sudo apt-get update && sudo apt-get upgrade

root@jdev-VM:~# apt-cache search lib32
lib32asound2 - shared library for ALSA applications (32 bit)
lib32asound2-dev - shared library for ALSA applications -- development files (32 bit)
lib32bz2-1.0 - high-quality block-sorting file compressor library - 32bit runtime
lib32bz2-dev - high-quality block-sorting file compressor library - 32bit development
lib32ffi-dev - Foreign Function Interface library (development files, 32bit)
lib32ffi6 - Foreign Function Interface library runtime (32bit)
lib32gcc1 - GCC support library (32 bit Version)
lib32gcc1-dbg - GCC support library (debug symbols)
lib32gfortran3 - Runtime library for GNU Fortran applications (32bit)
lib32gfortran3-dbg - Runtime library for GNU Fortran applications (32 bit debug symbols)
lib32gmp-dev - Multiprecision arithmetic library developers tools (32bit)
lib32gmp10 - Multiprecision arithmetic library (32bit)
lib32gmpxx4 - Multiprecision arithmetic library (C++ bindings, 32bit)
lib32gomp1 - GCC OpenMP (GOMP) support library (32bit)
lib32gomp1-dbg - GCC OpenMP (GOMP) support library (32 bit debug symbols)
lib32itm1 - GNU Transactional Memory Library (32bit)
lib32itm1-dbg - GNU Transactional Memory Library (32 bit debug symbols)
lib32mpfr-dev - multiple precision floating-point computation developers tools (32bit)
lib32mpfr4 - multiple precision floating-point computation (32bit)
lib32ncurses5 - shared libraries for terminal handling (32-bit)
lib32ncurses5-dev - developer's libraries for ncurses (32-bit)
lib32ncursesw5 - shared libraries for terminal handling (wide character support) (32-bit)
lib32ncursesw5-dev - developer's libraries for ncursesw (32-bit)
lib32objc3 - Runtime library for GNU Objective-C applications (32bit)
lib32objc3-dbg - Runtime library for GNU Objective-C applications (32 bit debug symbols)
lib32objc4 - Runtime library for GNU Objective-C applications (32bit)
lib32objc4-dbg - Runtime library for GNU Objective-C applications (32 bit debug symbols)
lib32quadmath0 - GCC Quad-Precision Math Library (32bit)
lib32quadmath0-dbg - GCC Quad-Precision Math Library (32 bit debug symbols)
lib32readline-gplv2-dev - GNU readline and history libraries, development files (32-bit)
lib32readline5 - GNU readline and history libraries, run-time libraries (32-bit)
lib32readline6 - GNU readline and history libraries, run-time libraries (32-bit)
lib32readline6-dev - GNU readline and history libraries, development files (32-bit)
lib32stdc++6 - GNU Standard C++ Library v3 (32 bit Version)
lib32stdc++6-4.4-dbg - GNU Standard C++ Library v3 (debugging files)
lib32stdc++6-4.6-dbg - GNU Standard C++ Library v3 (debugging files)
lib32stdc++6-4.7-dbg - GNU Standard C++ Library v3 (debugging files)
lib32tinfo-dev - developer's library for the low-level terminfo library (32-bit)
lib32tinfo5 - shared low-level terminfo library for terminal handling (32-bit)
lib32z1 - compression library - 32 bit runtime
lib32z1-dev - compression library - 32 bit development
libc6-dev-i386 - Embedded GNU C Library: 32-bit development libraries for AMD64
ia32-libs - ia32 shared libraries - transitional package
lib32cr0 - (32bit) Libraries to Checkpoint and Restart Linux processes
lib32gmp3 - Multiprecision arithmetic library (32bit)
lib32go0 - Runtime library for GNU Go applications (32bit)
lib32go0-dbg - Runtime library for GNU Go applications (32 bit debug symbols)
lib32mudflap0 - GCC mudflap shared support libraries (32bit)
lib32mudflap0-dbg - GCC mudflap shared support libraries (32 bit debug symbols)
lib32nss-mdns - NSS module for Multicast DNS name resolution (32-bits version)
lib32objc2 - Runtime library for GNU Objective-C applications (32bit)
lib32objc2-dbg - Runtime library for GNU Objective-C applications (32 bit debug symbols)
lib32stdc++6-4.5-dbg - GNU Standard C++ Library v3 (debugging files)

root@jdev-VM:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
 libgnutls26 : Depends: libgcrypt11 (>= 1.4.5) but it is not going to be installed
               Depends: libp11-kit0 (>= 0.11) but it is not going to be installed
               Depends: libtasn1-3 (>= 1.6-0) but it is not going to be installed
 libschroedinger-1.0-0 : Depends: liborc-0.4-0 (>= 1:0.4.16) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

root@jdev-VM:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@jdev-VM:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
 libgnutls26 : Depends: libgcrypt11 (>= 1.4.5) but it is not going to be installed
               Depends: libp11-kit0 (>= 0.11) but it is not going to be installed
               Depends: libtasn1-3 (>= 1.6-0) but it is not going to be installed
 libschroedinger-1.0-0 : Depends: liborc-0.4-0 (>= 1:0.4.16) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
root@jdev-VM:~# 

```

thanks

---

### Post by Bashing-om on 2013-03-10
JWebDev; Hi !
Insure that multiarch is enabled on your system: Post the output of Terminal code:
```
cat /etc/dpkg/dpkg.cfg.d/multiarch
```
If the return is "foreign-architecture i386" multiarch is enabled.
I would then try to install the dependency - ia32-libs-multiarch  - . See what results from this action / hopefully will install the other dependencies.[INDENT=2]just my thoughts on the matter

[/INDENT]

---

### Post by JWebDev on 2013-03-10
Hi, **Bashing-om**

Maybe the problem is that Linux under a virtual machine? Maybe something in the settings to turn on the virtual machine(VMware.)? 

Here's what happened.
> **Bashing-om said:**
> JWebDev; Hi !
Insure that multiarch is enabled on your system: Post the output of Terminal code:
```
cat /etc/dpkg/dpkg.cfg.d/multiarch
```
```
root@jdev-VM:~# cat /etc/dpkg/dpkg.cfg.d/multiarch
cat: /etc/dpkg/dpkg.cfg.d/multiarch: No such file or directory
```

> If the return is "foreign-architecture i386" multiarch is enabled.
I would then try to install the dependency - ia32-libs-multiarch  - .  See what results from this action / hopefully will install the other  dependencies.just my thoughts on the matter
```

root@jdev-VM:~# apt-get install foreign-architecture i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'type-handling:i386' instead of 'i386:i386'
E: Unable to locate package foreign-architecture

root@jdev-VM:~# apt-get install type-handling:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvga1 linux-headers-3.5.0-25
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
Suggested packages:
  debian-keyring g++-multilib g++-4.7-multilib gcc-4.7-doc libstdc++6-4.7-dbg libstdc++6-4.7-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.7 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl libstdc++6-4.7-dev
  type-handling:i386
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 10,5 MB of archives.
After this operation, 29,8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ quantal/main libstdc++6-4.7-dev amd64 4.7.2-2ubuntu1 [1 716 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ quantal/main g++-4.7 amd64 4.7.2-2ubuntu1 [7 966 kB]                                                           
Get:3 http://archive.ubuntu.com/ubuntu/ quantal/main g++ amd64 4:4.7.2-1ubuntu2 [1 448 B]                                                              
Get:4 http://archive.ubuntu.com/ubuntu/ quantal/main dpkg-dev all 1.16.7ubuntu6 [595 kB]                                                               
Get:5 http://archive.ubuntu.com/ubuntu/ quantal/main build-essential amd64 11.5ubuntu3 [5 814 B]                                                       
Get:6 http://archive.ubuntu.com/ubuntu/ quantal/main fakeroot amd64 1.18.4-2 [88,2 kB]                                                                 
Get:7 http://archive.ubuntu.com/ubuntu/ quantal/main libalgorithm-diff-perl all 1.19.02-2 [50,7 kB]                                                    
Get:8 http://archive.ubuntu.com/ubuntu/ quantal/main libalgorithm-diff-xs-perl amd64 0.04-2build3 [12,5 kB]                                            
Get:9 http://archive.ubuntu.com/ubuntu/ quantal/main libalgorithm-merge-perl all 0.08-2 [12,7 kB]                                                      
Get:10 http://archive.ubuntu.com/ubuntu/ quantal/universe type-handling i386 0.2.23build1 [6 386 B]                                                    
Fetched 10,5 MB in 1min 45s (99,5 kB/s)                                                                                                                
Selecting previously unselected package libstdc++6-4.7-dev.
(Reading database ... 184608 files and directories currently installed.)
Unpacking libstdc++6-4.7-dev (from .../libstdc++6-4.7-dev_4.7.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package g++-4.7.
Unpacking g++-4.7 (from .../g++-4.7_4.7.2-2ubuntu1_amd64.deb) ...
Selecting previously unselected package g++.
Unpacking g++ (from .../g++_4%3a4.7.2-1ubuntu2_amd64.deb) ...
Selecting previously unselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.16.7ubuntu6_all.deb) ...
Selecting previously unselected package build-essential.
Unpacking build-essential (from .../build-essential_11.5ubuntu3_amd64.deb) ...
Selecting previously unselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.18.4-2_amd64.deb) ...
Selecting previously unselected package libalgorithm-diff-perl.
Unpacking libalgorithm-diff-perl (from .../libalgorithm-diff-perl_1.19.02-2_all.deb) ...
Selecting previously unselected package libalgorithm-diff-xs-perl.
Unpacking libalgorithm-diff-xs-perl (from .../libalgorithm-diff-xs-perl_0.04-2build3_amd64.deb) ...
Selecting previously unselected package libalgorithm-merge-perl.
Unpacking libalgorithm-merge-perl (from .../libalgorithm-merge-perl_0.08-2_all.deb) ...
Selecting previously unselected package type-handling.
Unpacking type-handling (from .../type-handling_0.2.23build1_i386.deb) ...
Processing triggers for man-db ...
Setting up dpkg-dev (1.16.7ubuntu6) ...
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Setting up libalgorithm-diff-perl (1.19.02-2) ...
Setting up libalgorithm-diff-xs-perl (0.04-2build3) ...
Setting up libalgorithm-merge-perl (0.08-2) ...
Setting up type-handling (0.2.23build1) ...
Setting up libstdc++6-4.7-dev (4.7.2-2ubuntu1) ...
Setting up g++-4.7 (4.7.2-2ubuntu1) ...
Setting up g++ (4:4.7.2-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode
Setting up build-essential (11.5ubuntu3) ...
root@jdev-VM:~# apt-get install foreign-architecture i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'type-handling:i386' instead of 'i386:i386'
E: Unable to locate package foreign-architecture

root@jdev-VM:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
 libgnutls26 : Depends: libgcrypt11 (>= 1.4.5) but it is not going to be installed
               Depends: libp11-kit0 (>= 0.11) but it is not going to be installed
               Depends: libtasn1-3 (>= 1.6-0) but it is not going to be installed
 libschroedinger-1.0-0 : Depends: liborc-0.4-0 (>= 1:0.4.16) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
root@jdev-VM:~# 

```

thanks

---

### Post by mc4man on 2013-03-10
Seems similar to what could be seen on a live session of amd_64, the :i386 isn't enabled in dpkg
(can be seen in synaptic > Architecture, no arch:i386 shown.

So try this - (no sudo if from root terminal
```
sudo dpkg --add-architecture i386 && sudo apt-get update
```
```
sudo apt-get  install ia32-libs
```

---

### Post by JWebDev on 2013-03-10
does not help

```

root@jdev-VM:~# dpkg --add-architecture i386 && sudo apt-get update
Ign http://archive.ubuntu.com quantal InRelease
Ign http://ppa.launchpad.net quantal InRelease                      
Ign http://archive.ualinux.com quantal InRelease                     
Ign http://archive.ubuntu.com quantal-updates InRelease              
Ign http://ppa.launchpad.net quantal InRelease                                                     
Ign http://extras.ubuntu.com quantal InRelease                                                     
Ign http://archive.ubuntu.com quantal-backports InRelease                                          
Hit http://ppa.launchpad.net quantal Release.gpg                                                   
Ign http://archive.ubuntu.com quantal-security InRelease                                           
Hit http://archive.ualinux.com quantal Release.gpg                   
Hit http://ppa.launchpad.net quantal Release.gpg                     
Hit http://extras.ubuntu.com quantal Release.gpg                                                   
Hit http://archive.ubuntu.com quantal Release.gpg                                                  
Hit http://ppa.launchpad.net quantal Release                                                       
Hit http://archive.ubuntu.com quantal-updates Release.gpg                                                         
Hit http://extras.ubuntu.com quantal Release                                               
Hit http://ppa.launchpad.net quantal Release                                                
Hit http://archive.ualinux.com quantal Release                                                                    
Get:1 http://archive.ubuntu.com quantal-backports Release.gpg [933 B]                        
Hit http://ppa.launchpad.net quantal/main Sources                                                                                   
Hit http://archive.ubuntu.com quantal-security Release.gpg                                                               
Hit http://extras.ubuntu.com quantal/main Sources                                                                        
Hit http://ppa.launchpad.net quantal/main amd64 Packages                                   
Hit http://archive.ualinux.com quantal/main amd64 Packages                                 
Hit http://archive.ubuntu.com quantal Release                                              
Hit http://ppa.launchpad.net quantal/main i386 Packages                                                                                         
Hit http://extras.ubuntu.com quantal/main amd64 Packages                                                                 
Hit http://archive.ubuntu.com quantal-updates Release                                                                    
Get:2 http://archive.ubuntu.com quantal-backports Release [49,6 kB]                                                      
Hit http://archive.ualinux.com quantal/main i386 Packages                                           
Hit http://extras.ubuntu.com quantal/main i386 Packages                                                                            
Hit http://ppa.launchpad.net quantal/main Sources                                                                                  
Hit http://ppa.launchpad.net quantal/main amd64 Packages                                                                           
Hit http://ppa.launchpad.net quantal/main i386 Packages                                                                                            
Hit http://archive.ubuntu.com quantal-security Release                                                                    
Hit http://archive.ubuntu.com quantal/main Sources                                                                        
Hit http://archive.ualinux.com quantal/main Translation-en                                  
Hit http://archive.ubuntu.com quantal/restricted Sources                                                                  
Hit http://archive.ubuntu.com quantal/universe Sources                                                                    
Hit http://archive.ualinux.com quantal/main Translation-ru                                                                
Hit http://archive.ubuntu.com quantal/multiverse Sources                                                                  
Hit http://archive.ubuntu.com quantal/main amd64 Packages                                                                 
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages                                                           
Hit http://archive.ubuntu.com quantal/universe amd64 Packages                                                             
Ign http://archive.ualinux.com quantal/main Translation-en_US                                                             
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages                             
Hit http://archive.ubuntu.com quantal/main i386 Packages              
Hit http://archive.ubuntu.com quantal/restricted i386 Packages        
Hit http://archive.ubuntu.com quantal/universe i386 Packages          
Hit http://archive.ubuntu.com quantal/multiverse i386 Packages        
Hit http://archive.ubuntu.com quantal/main Translation-en             
Hit http://archive.ubuntu.com quantal/main Translation-ru             
Hit http://archive.ubuntu.com quantal/multiverse Translation-en       
Ign http://ppa.launchpad.net quantal/main Translation-en_US           
Ign http://extras.ubuntu.com quantal/main Translation-en_US           
Ign http://ppa.launchpad.net quantal/main Translation-en              
Ign http://ppa.launchpad.net quantal/main Translation-ru              
Hit http://archive.ubuntu.com quantal/multiverse Translation-ru
Ign http://ppa.launchpad.net quantal/main Translation-en_US           
Ign http://ppa.launchpad.net quantal/main Translation-en              
Hit http://archive.ubuntu.com quantal/restricted Translation-en
Ign http://extras.ubuntu.com quantal/main Translation-en              
Ign http://ppa.launchpad.net quantal/main Translation-ru              
Hit http://archive.ubuntu.com quantal/restricted Translation-ru       
Ign http://extras.ubuntu.com quantal/main Translation-ru
Hit http://archive.ubuntu.com quantal/universe Translation-en
Hit http://archive.ubuntu.com quantal/universe Translation-ru
Hit http://archive.ubuntu.com quantal-updates/main Sources
Hit http://archive.ubuntu.com quantal-updates/restricted Sources
Hit http://archive.ubuntu.com quantal-updates/universe Sources
Hit http://archive.ubuntu.com quantal-updates/multiverse Sources
Hit http://archive.ubuntu.com quantal-updates/main amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted i386 Packages
Hit http://archive.ubuntu.com quantal-updates/universe i386 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-updates/main Translation-en
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en
Get:3 http://archive.ubuntu.com quantal-backports/main Sources [14 B]                                                                                  
Get:4 http://archive.ubuntu.com quantal-backports/restricted Sources [14 B]                                                                            
Get:5 http://archive.ubuntu.com quantal-backports/universe Sources [7 750 B]                                                                           
Get:6 http://archive.ubuntu.com quantal-backports/multiverse Sources [781 B]                                                                           
Get:7 http://archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]                                                                           
Get:8 http://archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]                                                                     
Get:9 http://archive.ubuntu.com quantal-backports/universe amd64 Packages [11,6 kB]                                                                    
Get:10 http://archive.ubuntu.com quantal-backports/multiverse amd64 Packages [1 118 B]                                                                 
Get:11 http://archive.ubuntu.com quantal-backports/main i386 Packages [14 B]                                                                           
Get:12 http://archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]                                                                     
Get:13 http://archive.ubuntu.com quantal-backports/universe i386 Packages [12,4 kB]                                                                    
Get:14 http://archive.ubuntu.com quantal-backports/multiverse i386 Packages [1 118 B]                                                                  
Hit http://archive.ubuntu.com quantal-backports/main Translation-en                                                                                    
Hit http://archive.ubuntu.com quantal-backports/multiverse Translation-en                                                                              
Hit http://archive.ubuntu.com quantal-backports/restricted Translation-en                                                                              
Hit http://archive.ubuntu.com quantal-backports/universe Translation-en                                                                                
Hit http://archive.ubuntu.com quantal-security/main Sources                                                                                            
Hit http://archive.ubuntu.com quantal-security/restricted Sources                                                                                      
Hit http://archive.ubuntu.com quantal-security/universe Sources                                                                                        
Hit http://archive.ubuntu.com quantal-security/multiverse Sources                                                                                      
Hit http://archive.ubuntu.com quantal-security/main amd64 Packages                                                                                     
Hit http://archive.ubuntu.com quantal-security/restricted amd64 Packages                                                                               
Hit http://archive.ubuntu.com quantal-security/universe amd64 Packages                                                                                 
Hit http://archive.ubuntu.com quantal-security/multiverse amd64 Packages                                                                               
Hit http://archive.ubuntu.com quantal-security/main i386 Packages                                                                                      
Hit http://archive.ubuntu.com quantal-security/restricted i386 Packages                                                                                
Hit http://archive.ubuntu.com quantal-security/universe i386 Packages                                                                                  
Hit http://archive.ubuntu.com quantal-security/multiverse i386 Packages                                                                                
Hit http://archive.ubuntu.com quantal-security/main Translation-en                                                                                     
Hit http://archive.ubuntu.com quantal-security/multiverse Translation-en                                                                               
Hit http://archive.ubuntu.com quantal-security/restricted Translation-en                                                                               
Hit http://archive.ubuntu.com quantal-security/universe Translation-en                                                                                 
Ign http://archive.ubuntu.com quantal/main Translation-en_US                                                                                           
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/main Translation-ru
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-ru
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-ru
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/universe Translation-ru
Ign http://archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/main Translation-ru
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-ru
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-ru
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/universe Translation-ru
Ign http://archive.ubuntu.com quantal-security/main Translation-en_US
Ign http://archive.ubuntu.com quantal-security/main Translation-ru
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-ru
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-security/restricted Translation-ru
Ign http://archive.ubuntu.com quantal-security/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-security/universe Translation-ru
Fetched 85,4 kB in 24s (3 506 B/s)
Reading package lists... Done

root@jdev-VM:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
 libgnutls26 : Depends: libgcrypt11 (>= 1.4.5) but it is not going to be installed
               Depends: libp11-kit0 (>= 0.11) but it is not going to be installed
               Depends: libtasn1-3 (>= 1.6-0) but it is not going to be installed
 libschroedinger-1.0-0 : Depends: liborc-0.4-0 (>= 1:0.4.16) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



```

---

### Post by Bashing-om on 2013-03-10
JWebDev;
WoW. I would have expected          mc4man's advise to be effective, given that multiarch was not enabled.
Lets see what dpkg has to say about multiarch; terminal code:
```
dpkg --print-foreign-architectures
```

tbh, I have never used a virtual machine environment, so my help may be short lived (??)
This link gives the skinny on multiarch, might find some direction there.
[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)[INDENT=2]
My 2 cents worth

[/INDENT]

---

### Post by JWebDev on 2013-03-10
```

root@jdev-VM:~# dpkg --print-foreign-architectures
i386

```

---

### Post by mc4man on 2013-03-10
If you have synaptic installed maybe do a little digging on these mentioned packages, both amd64 (default) packages & i386 ones
libgnutls26
libgcrypt11 
libp11-kit0
libtasn1-3
screen shows ex. in arch:i386 section

Do you have any ppa's installed?

---

### Post by Bashing-om on 2013-03-10
JWebDev;
That output leads to some speculation as it indicates that the 32 bit architecture is available....huummmm...
Try this, will not hurt to install  "architecture i386" again, see what results.
```

sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get -f upgrade
sudo apt-get install ia32-libs
```


//If you are still in root console - disregard "sudo"--.
[INDENT=2]
recon what 

[/INDENT]

---

### Post by JWebDev on 2013-03-10
> **mc4man said:**
> If you have synaptic installed maybe do a little digging on these mentioned packages, both amd64 (default) packages & i386 ones
libgnutls26
libgcrypt11 
libp11-kit0
libtasn1-3
screen shows ex. in arch:i386 section

Do you have any ppa's installed?

If I choose any package, I discarded the list of packages that will be removed and which will be installing. The list is long. If I did I press OK. I get it now.
See screen.


> 

JWebDev;
That output leads to some speculation as it indicates that the 32 bit architecture is available....huummmm...
Try this, will not hurt to install  "architecture i386" again, see what results.
 	Code:
 	
sudo dpkg --add-architecture i386 sudo apt-get update sudo apt-get -f upgrade sudo apt-get install ia32-libs 

//If you are still in root console - disregard "sudo"--.

recon what

```


root@jdev-VM:~# apt-get update
Ign http://ppa.launchpad.net quantal InRelease
Ign http://archive.ubuntu.com quantal InRelease                     
Ign http://archive.ualinux.com quantal InRelease                     
Ign http://extras.ubuntu.com quantal InRelease                       
Ign http://ppa.launchpad.net quantal InRelease                                                     
Ign http://archive.ubuntu.com quantal-updates InRelease                                            
Hit http://ppa.launchpad.net quantal Release.gpg                                                   
Ign http://archive.ubuntu.com quantal-backports InRelease                                          
Hit http://extras.ubuntu.com quantal Release.gpg                     
Hit http://archive.ualinux.com quantal Release.gpg                   
Hit http://ppa.launchpad.net quantal Release.gpg                     
Ign http://archive.ubuntu.com quantal-security InRelease                                           
Hit http://extras.ubuntu.com quantal Release                                                       
Hit http://ppa.launchpad.net quantal Release                                                                              
Hit http://archive.ubuntu.com quantal Release.gpg                                                                 
Hit http://extras.ubuntu.com quantal/main Sources                                                                 
Hit http://ppa.launchpad.net quantal Release                                               
Hit http://archive.ubuntu.com quantal-updates Release.gpg                                                         
Hit http://archive.ualinux.com quantal Release                                                                    
Hit http://ppa.launchpad.net quantal/main Sources                                            
Hit http://archive.ubuntu.com quantal-backports Release.gpg                                                              
Hit http://extras.ubuntu.com quantal/main amd64 Packages                                                                 
Hit http://ppa.launchpad.net quantal/main amd64 Packages                                                                 
Hit http://archive.ubuntu.com quantal-security Release.gpg                                                               
Hit http://archive.ualinux.com quantal/main amd64 Packages                                 
Hit http://extras.ubuntu.com quantal/main i386 Packages                                    
Hit http://ppa.launchpad.net quantal/main i386 Packages                                                                  
Hit http://archive.ubuntu.com quantal Release                                                                            
Hit http://archive.ubuntu.com quantal-updates Release                                                                                           
Hit http://archive.ubuntu.com quantal-backports Release                                                                  
Hit http://archive.ualinux.com quantal/main i386 Packages                                  
Hit http://archive.ubuntu.com quantal-security Release                                                                                          
Hit http://ppa.launchpad.net quantal/main Sources                                                                                               
Hit http://archive.ubuntu.com quantal/main Sources                                                                       
Hit http://ppa.launchpad.net quantal/main amd64 Packages                                   
Hit http://archive.ubuntu.com quantal/restricted Sources                                                                 
Hit http://ppa.launchpad.net quantal/main i386 Packages                                                                  
Hit http://archive.ubuntu.com quantal/universe Sources                                                                   
Hit http://archive.ualinux.com quantal/main Translation-en                                 
Hit http://archive.ubuntu.com quantal/multiverse Sources                                                                 
Hit http://archive.ubuntu.com quantal/main amd64 Packages                                                                
Hit http://archive.ualinux.com quantal/main Translation-ru                                                               
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages                                                          
Hit http://archive.ubuntu.com quantal/universe amd64 Packages                                                            
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages                                                          
Hit http://archive.ubuntu.com quantal/main i386 Packages                                   
Ign http://extras.ubuntu.com quantal/main Translation-en_US                                                              
Hit http://archive.ubuntu.com quantal/restricted i386 Packages                                                           
Ign http://archive.ualinux.com quantal/main Translation-en_US                              
Hit http://archive.ubuntu.com quantal/universe i386 Packages                               
Hit http://archive.ubuntu.com quantal/multiverse i386 Packages       
Ign http://extras.ubuntu.com quantal/main Translation-en             
Hit http://archive.ubuntu.com quantal/main Translation-en            
Ign http://extras.ubuntu.com quantal/main Translation-ru             
Hit http://archive.ubuntu.com quantal/main Translation-ru            
Hit http://archive.ubuntu.com quantal/multiverse Translation-en
Hit http://archive.ubuntu.com quantal/multiverse Translation-ru
Hit http://archive.ubuntu.com quantal/restricted Translation-en
Hit http://archive.ubuntu.com quantal/restricted Translation-ru
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://archive.ubuntu.com quantal/universe Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-ru
Hit http://archive.ubuntu.com quantal/universe Translation-ru
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Hit http://archive.ubuntu.com quantal-updates/main Sources
Ign http://ppa.launchpad.net quantal/main Translation-en
Hit http://archive.ubuntu.com quantal-updates/restricted Sources
Ign http://ppa.launchpad.net quantal/main Translation-ru
Hit http://archive.ubuntu.com quantal-updates/universe Sources
Hit http://archive.ubuntu.com quantal-updates/multiverse Sources
Hit http://archive.ubuntu.com quantal-updates/main amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-updates/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates/restricted i386 Packages
Hit http://archive.ubuntu.com quantal-updates/universe i386 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-updates/main Translation-en
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en
Hit http://archive.ubuntu.com quantal-backports/main Sources
Hit http://archive.ubuntu.com quantal-backports/restricted Sources
Hit http://archive.ubuntu.com quantal-backports/universe Sources
Hit http://archive.ubuntu.com quantal-backports/multiverse Sources
Hit http://archive.ubuntu.com quantal-backports/main amd64 Packages
Hit http://archive.ubuntu.com quantal-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-backports/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-backports/main i386 Packages
Hit http://archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://archive.ubuntu.com quantal-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-backports/main Translation-en
Hit http://archive.ubuntu.com quantal-backports/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-backports/restricted Translation-en
Hit http://archive.ubuntu.com quantal-backports/universe Translation-en
Hit http://archive.ubuntu.com quantal-security/main Sources
Hit http://archive.ubuntu.com quantal-security/restricted Sources
Hit http://archive.ubuntu.com quantal-security/universe Sources
Hit http://archive.ubuntu.com quantal-security/multiverse Sources
Hit http://archive.ubuntu.com quantal-security/main amd64 Packages
Hit http://archive.ubuntu.com quantal-security/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-security/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-security/main i386 Packages
Hit http://archive.ubuntu.com quantal-security/restricted i386 Packages
Hit http://archive.ubuntu.com quantal-security/universe i386 Packages
Hit http://archive.ubuntu.com quantal-security/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-security/main Translation-en
Hit http://archive.ubuntu.com quantal-security/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-security/restricted Translation-en
Hit http://archive.ubuntu.com quantal-security/universe Translation-en
Ign http://archive.ubuntu.com quantal/main Translation-en_US
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/main Translation-ru
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-ru
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-ru
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/universe Translation-ru
Ign http://archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/main Translation-ru
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-ru
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-ru
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/universe Translation-ru
Ign http://archive.ubuntu.com quantal-security/main Translation-en_US
Ign http://archive.ubuntu.com quantal-security/main Translation-ru
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-ru
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-security/restricted Translation-ru
Ign http://archive.ubuntu.com quantal-security/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-security/universe Translation-ru
Reading package lists... Done
[1]+  Exit 1                  gksudo synaptic

root@jdev-VM:~# apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@jdev-VM:~# apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
 libgnutls26 : Depends: libgcrypt11 (>= 1.4.5) but it is not going to be installed
               Depends: libp11-kit0 (>= 0.11) but it is not going to be installed
               Depends: libtasn1-3 (>= 1.6-0) but it is not going to be installed
 libschroedinger-1.0-0 : Depends: liborc-0.4-0 (>= 1:0.4.16) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

root@jdev-VM:~# gksudo synaptic &
[1] 7240
root@jdev-VM:~# Failed to SetCandidateRelease for quantal-updates


```

---

### Post by mc4man on 2013-03-10
did you happen to upgrade some packages from quantal-proposed and then disable the proposed source? (like libc6

What's this show 
```
apt-cache policy libc6 libc6:i386
```

---

### Post by JWebDev on 2013-03-10
```

root@jdev-VM:~# apt-cache policy libc6 libc6:i386
libc6:
  Installed: 2.15-0ubuntu20.1
  Candidate: 2.15-0ubuntu20.1
  Version table:
 *** 2.15-0ubuntu20.1 0
        100 /var/lib/dpkg/status
     2.15-0ubuntu20 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main amd64 Packages
libc6:i386:
  Installed: (none)
  Candidate: 2.15-0ubuntu20
  Version table:
     2.15-0ubuntu20 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/main i386 Packages
        500 http://archive.ualinux.com/ubuntu/ quantal/main i386 Packages
root@jdev-VM:~# 

```

---

### Post by mc4man on 2013-03-10
So enable quantal-proposed in software sources,  update your sources & try again to install ia32-libs
libc6 is @ 2.15-0ubuntu20[COLOR="#FF0000"].1[/COLOR] from proposed but the current available for i386 is 2.15-0ubuntu20, they **have** to match

---

### Post by JWebDev on 2013-03-10
> **mc4man said:**
> So enable quantal-proposed in software sources,  update your sources & try again to install ia32-libs
libc6 is @ 2.15-0ubuntu20[COLOR=#FF0000].1[/COLOR] from proposed but the current available for i386 is 2.15-0ubuntu20, they **have** to match
Thanks a lot! It works! Issue resolved.

---

### Post by mc4man on 2013-03-10
> **JWebDev said:**
>  Issue resolved.
Well have fun with your android stuff, ect.
As far as -proposed, you should probably disable again after all is installed, if leaving enabled then pay attention to what's being updated, ect.
Best done in synaptic as you'll be prompted when marking packages for update as to what will happen, plus synaptic keeps a nice tidy history for you.
(the Origin tab in synaptic is also useful...

---

