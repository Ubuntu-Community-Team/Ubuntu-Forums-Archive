---
title: "Packages No Longer Needed: efibootmgr libfwup1"
date: 2020-04-15
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2020-04-15
What can I expect if I do autoremove?
How might I prevent devastating issues?

Ubuntu 18.04.4 LTS (No Dual Boot)

Most recent changes...
Installed Wine-Staging
Installed IMVU 3D Chat Client software (not Linux supported. They don't have a Linux version)
Installed Gnome Tweaks

Message (apt full-upgrade)
```
The following packages were automatically installed and are no longer required:
  efibootmgr libfwup1
Use 'sudo apt autoremove' to remove them.


```
Full Message (apt update)
```

wyatt@wyatt-Aspire-5733Z:~$ sudo apt update
[sudo] password for wyatt: 
Sorry, try again.
[sudo] password for wyatt: 
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:7 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Get:9 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [38.7 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [668 kB]
Get:11 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [42.1 kB]
Get:12 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [914 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [308 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,013 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,065 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [273 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [457 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:20 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,972 B]
Fetched 5,044 kB in 18s (280 kB/s)                                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

Full Message (apt full-upgrade)
```
wyatt@wyatt-Aspire-5733Z:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  efibootmgr libfwup1
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wyatt@wyatt-Aspire-5733Z:~$ 

```

---

### Post by ajgreeny on 2020-04-15
Is your system using UEFI or MBR/BIOS?

Both those packages that autoremove will get rid of are for UEFI so if you have MBR/BIOS they will not be needed, though I didn't think they were installed in an MBR/BIOS setup; I must check that and get back to you.

---

### Post by wyattwhiteeagle on 2020-04-15
> **ajgreeny said:**
> Is your system using UEFI or MBR/BIOS?

Both those packages that autoremove will get rid of are for UEFI so if you have MBR/BIOS they will not be needed, though I didn't think they were installed in an MBR/BIOS setup; I must check that and get back to you.

Factory specs are Acer Aspire 5733z Windows 7 (SP1) 64 bit MBR/BIOS.

The only hardware upgrades I've done is...

MBR HDD from 500 GB to 1 TB
RAM from 4 GB to 8 GB
BIOS V1.10

---

### Post by ajgreeny on 2020-04-15
Windows 7 was alwsy installed using MBR/BIOS if pre-installed before purchase, so the likelihood is that your machine is still using that system, and therefore those two packages can be removed quite safely.

---

### Post by wyattwhiteeagle on 2020-04-15
> **ajgreeny said:**
> Windows 7 was alwsy installed using MBR/BIOS if pre-installed before purchase, so the likelihood is that your machine is still using that system, and therefore those two packages can be removed quite safely.

Awesome

I'll let ya know how it goes

---

### Post by wyattwhiteeagle on 2020-04-15
Thanks so much. Everything is all good so far

apt autoremove
```
wyatt@wyatt-Aspire-5733Z:~$ sudo apt autoremove
[sudo] password for wyatt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

apt autoclean
```
wyatt@wyatt-Aspire-5733Z:~$ sudo apt autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

apt update
```
wyatt@wyatt-Aspire-5733Z:~$ sudo apt update
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Hit:7 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [914 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [668 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,013 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,065 kB]
Fetched 3,913 kB in 3s (1,206 kB/s)                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

```

apt full-upgrade
```
wyatt@wyatt-Aspire-5733Z:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wyatt@wyatt-Aspire-5733Z:~$ 

```

---

### Post by wyattwhiteeagle on 2020-04-25
What about libwayland-egl1-mesa

```
wyatt@wyatt-Aspire-5733Z:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  libwayland-egl1-mesa
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
wyatt@wyatt-Aspire-5733Z:~$ 
```

---

### Post by CelticWarrior on 2020-04-25
> **wyattwhiteeagle said:**
> What about libwayland-egl1-mesa

It can be removed as well. It's just a transitional 'dummy' package. You should find the proper 'libwayland-egl1' package installed instead.

---

