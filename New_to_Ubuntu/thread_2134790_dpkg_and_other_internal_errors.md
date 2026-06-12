---
title: "dpkg and other internal errors"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by cluelesswonder on 2013-04-12
I think I'm having serious problems with ubuntu 12.04 (not sure that they're actually serious).
I'm not very experienced with the terminal and need basic instructions to know what to do.
I've been running 12.04 since early 2012 with no real issues until a recent attempt at installing upgrades and now everything seems to be screwed up. I keep getting the 'ubuntu has experienced an internal error' message and many of them seem to have to do with dpkg or apt-get but today the error reports have been crashing before i've been able to read them.
My firefox was crashing constantly before this and I tried to install the latest flash player upgrade in synaptic hoping that might have something to do with the issue. . .
that didn't work because of a dpkg error
so I tried to reinstall dpkg in synaptic and it cause synaptic to totally crash so that now I can't open it. I'm going to try to restart my computer and see if that helps but I have a feeling that I'm over my head in terms of what needs to be done.
Please help! I'm not even sure how to get the proper error report for anyone to understand what exactly the problem is so that would probably be the first step.
Thank you so much!

---

### Post by MG&amp;TL on 2013-04-12
Okay, first of all we'll need to check if *dpkg* and *APT *are still installed properly. Try running:

```
dpkg
```

and

```
apt-get
```

in a terminal (just type the command and press return) and copy-paste the output here. Thanks!

Quick hint for later installs: if something goes wrong, re-installing the package manager isn't always the best idea. :)

---

### Post by cluelesswonder on 2013-04-12
dpkg gives this:

> enigma@Peanut:~$ dpkg
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !




apt-get
> enigma@Peanut:~$ apt-get
apt 0.8.16~exp12ubuntu10.10 for i386 compiled on Mar 13 2013 21:23:56
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.



---

### Post by fantab on 2013-04-12
Can you post the output of:

```
sudo apt-get update
```

---

### Post by cluelesswonder on 2013-04-12
yes!

```
enigma@Peanut:~$ sudo apt-get update
[sudo] password for enigma: 
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://ca.archive.ubuntu.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://dl.google.com stable Release.gpg                                    
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Get:2 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://dl.google.com stable Release                                        
Hit http://ca.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://ca.archive.ubuntu.com precise Release                               
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:4 http://ca.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://ca.archive.ubuntu.com precise-backports Release                     
Hit http://ca.archive.ubuntu.com precise/main Sources                          
Hit http://ca.archive.ubuntu.com precise/restricted Sources                    
Get:6 http://security.ubuntu.com precise-security/main Sources [65.6 kB]       
Hit http://ca.archive.ubuntu.com precise/universe Sources                      
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ca.archive.ubuntu.com precise/multiverse Sources                    
Ign http://archive.canonical.com precise/partner Translation-en_CA             
Get:7 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Hit http://ca.archive.ubuntu.com precise/main i386 Packages                    
Ign http://extras.ubuntu.com precise/main Translation-en_CA                    
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages              
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:8 http://security.ubuntu.com precise-security/universe Sources [24.0 kB]
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages                
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages     
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,389 B]
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex  
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex    
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [249 kB]
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Get:11 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:12 http://ca.archive.ubuntu.com precise-updates/main Sources [377 kB]
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [73.5 kB]
Get:14 http://ca.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:15 http://ca.archive.ubuntu.com precise-updates/universe Sources [83.4 kB]
Get:16 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,368 B]
Get:17 http://ca.archive.ubuntu.com precise-updates/multiverse Sources [6,562 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex  
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Get:18 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [610 kB]
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Get:19 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Get:20 http://ca.archive.ubuntu.com precise-updates/universe i386 Packages [196 kB]
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Get:21 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/main Sources                
Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://ca.archive.ubuntu.com precise-backports/universe Sources            
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com precise/main Translation-en                   
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en             
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA            
Hit http://ca.archive.ubuntu.com precise/universe Translation-en               
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA        
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA    
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 1,824 kB in 9s (198 kB/s)                                              
Reading package lists... Done

```

---

### Post by schragge on 2013-04-12
Looks okey to me. Could you please also post the output of
```
dpkg -l dpkg synaptic
``` :?:

---

### Post by fantab on 2013-04-12
From Grub Boot into "[Recovery Mode]("https://wiki.ubuntu.com/RecoveryMode")" and try to fix dpkg. You will be presented with a simple GUI and its not too difficult from there on.

---

### Post by cluelesswonder on 2013-04-12
```
enigma@Peanut:~$ dpkg -l dpkg synaptic
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  dpkg           1.16.1.2ubuntu Debian package management system
ii  synaptic       0.75.9ubuntu1  Graphical package manager
enigma@Peanut:~$ 


```

---

### Post by fantab on 2013-04-12
Looks fine to me. 
Try the Recovery mode and see if it fixes things.
If not, and if its an option, then download and install [Ubuntu 13.04 beta (daily-build)]("http://cdimage.ubuntu.com/daily-live/current/"). Its quite stable for a Beta. I ditched 12.10 long time back. :D

---

### Post by cluelesswonder on 2013-04-12
The recovery mode was easy, as you said!
I'm not sure that it fixed things but my firefox hasn't crashed yet and I haven't gotten any error messages thus far. . .so here's hoping!
I'll change the thread to solved for now and post again if something comes up.

Thank you so much for your help!

---

