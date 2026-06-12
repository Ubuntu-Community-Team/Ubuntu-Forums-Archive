---
title: "Unmet dependencies causing errors"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by EmperorMoo on 2013-02-12
Hi all,

I'm stuck in a bit of a loop here and can't fugure out how to get out.

I'm trying to install emacs over ssh onto a Ubuntu 12.04LTS Server.

On running ```
sudo apt-get install emacs
``` I get an unmet dependencies error, with running  ```
apt-get -f install
``` as the fix.

While processing this, it stops when ```
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-37-generic-pae_3.2.0-37.58_i386.deb
 /var/cache/apt/archives/linux-image-3.2.0-37-virtual_3.2.0-37.58_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried removing these packages manually, but as soon as I try to reinstall emacs they reapear and the whole cycle begins again.

I've also tried refreshing the sources list (as the problematic packages are for an obsolete kernel) with ```
sudo rm /var/lib/apt/lists/* -vf
```
.

Any help appreciated,

Cheers,

EM

---

### Post by kc1di on 2013-02-12
try ```
sudo apt-get autoclean
```

---

### Post by EmperorMoo on 2013-02-12
I've given this a go, and still the problem's there.

---

### Post by ibjsb4 on 2013-02-12
How bout

```
sudo apt-get clean && sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by schragge on 2013-02-12
I'd like to see the lines before that in the output of apt-get:
```

Errors were encountered while processing:

```

---

### Post by EmperorMoo on 2013-02-12
```
jon@hswtechnical:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-3.2.0-37-generic-pae linux-image-3.2.0-37-virtual
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-37-generic-pae linux-image-3.2.0-37-virtual
0 upgraded, 2 newly installed, 0 to remove and 44 not upgraded.
7 not fully installed or removed.
Need to get 0 B/50.3 MB of archives.
After this operation, 140 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: warning: files list file for package `linux-image-3.2.0-36-virtual' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-35-lowlatency-pae' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-36-generic-pae' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-34-generic-pae' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-35-lowlatency' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-36-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-35-virtual' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-35-generic-pae' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-3.2.0-35-generic' missing, assuming package has no files currently installed.
(Reading database ... 190155 files and directories currently installed.)
Unpacking linux-image-3.2.0-37-generic-pae (from .../linux-image-3.2.0-37-generic-pae_3.2.0-37.58_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-37-generic-pae_3.2.0-37.58_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-37-generic-pae': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
Unpacking linux-image-3.2.0-37-virtual (from .../linux-image-3.2.0-37-virtual_3.2.0-37.58_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-37-virtual_3.2.0-37.58_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-37-virtual': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-37-virtual /boot/vmlinuz-3.2.0-37-virtual
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-37-virtual /boot/vmlinuz-3.2.0-37-virtual
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-37-generic-pae_3.2.0-37.58_i386.deb
 /var/cache/apt/archives/linux-image-3.2.0-37-virtual_3.2.0-37.58_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

That's what comes before the "Errors were encountered while processing:"

I'll also give lbjsb4's advice a go too, and then post after that.

edit: have done that:```

jon@hswtechnical:~$ sudo apt-get clean && sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for jon: 
Ign http://gb.archive.ubuntu.com precise InRelease
Ign http://gb.archive.ubuntu.com precise-updates InRelease
Ign http://gb.archive.ubuntu.com precise-backports InRelease
Hit http://gb.archive.ubuntu.com precise Release.gpg  
Get:1 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:2 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://gb.archive.ubuntu.com precise Release                               
Get:3 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:4 http://gb.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                    
Hit http://gb.archive.ubuntu.com precise/universe Sources                      
Hit http://gb.archive.ubuntu.com precise/multiverse Sources                    
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                    
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages            
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex               
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:5 http://gb.archive.ubuntu.com precise-updates/main Sources [366 kB]       
Get:6 http://gb.archive.ubuntu.com precise-updates/restricted Sources [5,135 B]
Get:7 http://gb.archive.ubuntu.com precise-updates/universe Sources [78.6 kB]
Get:8 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [4,726 B]
Get:9 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [584 kB]
Ign http://security.ubuntu.com precise-security InRelease                 
Get:10 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [9,503 B]
Get:11 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [181 kB]
Get:12 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex      
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Get:13 http://gb.archive.ubuntu.com precise-backports/main Sources [2,422 B]
Get:14 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:15 http://gb.archive.ubuntu.com precise-backports/universe Sources [21.8 kB]
Get:16 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:17 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:18 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:19 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [22.4 kB]
Get:20 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex     
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Get:21 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:22 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:23 http://security.ubuntu.com precise-security/main Sources [63.1 kB]
Get:24 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:25 http://security.ubuntu.com precise-security/universe Sources [20.9 kB]
Get:26 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]
Get:27 http://security.ubuntu.com precise-security/main i386 Packages [234 kB]
Get:28 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:29 http://security.ubuntu.com precise-security/universe i386 Packages [67.1 kB]
Get:30 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,371 B]
Get:31 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:32 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:33 http://security.ubuntu.com precise-security/restricted TranslationIndex [71 B]
Get:34 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 1,837 kB in 1s (1,089 kB/s)              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-backports-modules-hv-3.2.0-37-generic-pae : Depends: linux-image-3.2.0-37-generic-pae but it is not installed
 linux-backports-modules-hv-3.2.0-37-virtual : Depends: linux-image-3.2.0-37-virtual but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by schragge on 2013-02-12
This
```

No space left on device

```

---

### Post by ibjsb4 on 2013-02-12
No need to try my idea, your out of boot space.  Need to remove those old kernels.

> failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.2.0-37-generic-pae': No space left on device

---

### Post by EmperorMoo on 2013-02-12
Thanks, will give that a go tomorrow when I'm back at work.

I did think this might be an issue, and cleared out other old kernels from /boot.

I guess I could also adjust the partition if necessary as I think I only have about 300MB of space on /boot total.

---

### Post by LuisGMarine on 2013-02-12
```
sudo apt-get autoremove
```

should take care of your old kernels that are no longer in use.

---

### Post by kc1di on 2013-02-12
Also you may want to run ```
sudo dpkg --configure -a
```
After you remove those extra kernels.

---

### Post by EmperorMoo on 2013-02-13
Right, finally fixed.  This post is just briefly what I did in case anyone eklse has this issue.

First, I tried removing the older kernels manually to free up some room on /boot:
```
  385  rm /boot/initrd.img-3.2.0-29-generic-pae
  386  sudo rm /boot/initrd.img-3.2.0-29-generic-pae
  387  sudo apt-get remove --purge linux-image-3.2.0-29-generic-pae

```

but the same issue kept repeating on running:
```

sudo apt-get -f install

```

so, I decided to have a look at what was actually in /boot, and then (a bit recklessly) used:
```

sudo rm -f *xx*

```
to remove some really obsolete kernels.  I only actually removed 3.2.0.21 and 3.2.0.29 by this method.

Emacs and updates would then install as I wanted.  I'm going to do a bit more housekeeping now to free some more room on /boot so this doesn't happen again.

Thanks for your help

---

### Post by kc1di on 2013-02-13
Glad you found the problem and got it going :)

---

