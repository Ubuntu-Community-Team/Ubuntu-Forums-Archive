---
title: "Problems installing VirtualBox in Ubuntu 16.04"
date: 2018-02-15
forum: New to Ubuntu
---

### Post by chris53 on 2018-02-15
Hi there,

I'm having issues installing VirtualBox on my Ubuntu 16.04 Dell XPS laptop.  

I followed the instructions on the webpage: [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

I first executed the following commands:  
```
wget -q [https://www.virtualbox.org/download/oracle_vbox_2016.asc](https://www.virtualbox.org/download/oracle_vbox_2016.asc) -O- | sudo apt-key add -

Returned = OK

wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -

Returned=OK

```
Then to install VirturalBox I executed: 
```
sudo apt-get update 
```

Seems to be an error with this.   Output pasted below:

```
Hit:1http://archive.canonical.com/ubuntu xenial InRelease
Ign:2http://dl.google.com/linux/chrome/deb stable InRelease                                                                               
Get:3http://dl.google.com/linux/chrome/deb stable Release [1,189 B]                                                                       
Hit:4http://archive.ubuntu.com/ubuntu xenial InRelease                                                                                    
Get:5http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]                                         
Ign:6http://dell.archive.canonical.com/updates xenial-dell InRelease                                                        
Get:7http://dl.google.com/linux/chrome/deb stable Release.gpg [819 B]                                                       
Get:8http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]                                                                 
Hit:9http://dell.archive.canonical.com/updates xenial-dell Release                                                  
Get:10http://dl.google.com/linux/chrome/deb stable/main amd64 Packages[1,392 B]                                     
Get:12http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]                                                     
Get:13http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages[442 kB]
Get:14http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages[724 kB]
Get:15http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages[399 kB]
Get:16http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages[674 kB]
Get:17http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11Metadata [67.5 kB]
Get:18http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64Icons [77.2 kB]          
Get:19http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en[301 kB]          
Get:20http://security.ubuntu.com/ubuntu xenial-security/universe amd64DEP-11 Metadata [51.4 kB]     
Get:21http://security.ubuntu.com/ubuntu xenial-security/universe DEP-1164x64 Icons [85.1 kB]            
Get:22http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11Metadata [317 kB]            
Get:23http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64Icons [229 kB]
Get:24http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64Packages [588 kB]
Get:25http://archive.ubuntu.com/ubuntu xenial-updates/universe i386Packages [545 kB]
Get:26http://archive.ubuntu.com/ubuntu xenial-updates/universeTranslation-en [238 kB]
Get:27http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11Metadata [191 kB]
Get:28http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64Icons [272 kB]
Get:29http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64DEP-11 Metadata [5,888 B]
Get:30http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11Metadata [3,328 B]
Get:31http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64DEP-11 Metadata [4,696 B]
Fetched 5,522 kB in1s (3,301 kB/s)                                           
*** Error in`appstreamcli': double free or corruption (fasttop):0x000000000221b010 ***
======= Backtrace:=========
/lib/x86_64-linux-gnu/libc.so.6(+0x777e5)[0x7f90f11507e5]
/lib/x86_64-linux-gnu/libc.so.6(+0x8037a)[0x7f90f115937a]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x4c)[0x7f90f115d53c]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_component_complete+0x439)[0x7f90f14d5d19]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_data_pool_update+0x44a)[0x7f90f14d6f0a]
/usr/lib/x86_64-linux-gnu/libappstream.so.3(as_cache_builder_refresh+0x1c2)[0x7f90f14cc272]
appstreamcli(ascli_refresh_cache+0x12e)[0x4049de]
appstreamcli(as_client_run+0x6fb)[0x403ceb]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f90f10f9830]
appstreamcli(_start+0x29)[0x403519]
```

I looked into this error and I THINK I found a solution..

```
sudo apt-get purge libappstream2
sudo rm /etc/apt/apt.conf.d/50appstreamThen I re-executed 
sudo apt-get update 
```

Seems to have ran successfully..   Output below:

```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                                                                           
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                                
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease                                   
Ign:6 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell InRelease   
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease          
Hit:8 [http://dell.archive.canonical.com/updates](http://dell.archive.canonical.com/updates) xenial-dell Release      
Hit:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Reading package lists... Done                     
```

Then I tried to run the install for VirtualBox...

```
sudo apt-get install virtualbox-5.2
```

Seems to have failed..   Not sure what this is telling me..   Can you please provide input???   Do I need to install some other packages before installing Virtualbox?

Output below:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-5.2:i386 is already the newest version (5.2.6-120293~Ubuntu~xenial).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 virtualbox-5.2:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                                libgl1:i386
                       Recommends: libsdl-ttf2.0-0:i386 but it is not going to be installed
                       Recommends: linux-headers-generic:i386 but it is not going to be installed or
                                   linux-headers-generic-pae:i386 but it is not installable or
                                   linux-headers-686-pae:i386 but it is not installable or
                                   linux-headers-amd64:i386 but it is not installable or
                                   linux-headers-2.6-686:i386 but it is not installable or
                                   linux-headers-2.6-amd64:i386 but it is not installable or
                                   linux-headers:i386
                       Recommends: linux-image:i386
                       Recommends: gcc:i386 but it is not going to be installed
                       Recommends: binutils:i386 but it is not going to be installed
                       Recommends: pdf-viewer:i386
                       Recommends: libgl1:i386
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
Thank you for your input!
Chris

---

### Post by wildmanne39 on 2018-02-15
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by chris53 on 2018-02-15
> **wildmanne39 said:**
> Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Thanks

---

### Post by deadflowr on 2018-02-16
It doesn't look like you added the virtualbox entry to your sources.
(You only imported the keys)

This one liner should add the entry for you 
```
sudo sh -c 'echo "deb https://download.virtualbox.org/virtualbox/debian xenial  contrib" >> /etc/apt/sources.list.d/virtualbox.org.list' 

```


Also, any reason why you downloaded the 32-bit version?
Seems weird in this day and age to run the 32-bit version if not on a 32-bit OS.

Are you actually on a 32-bit version of Ubuntu?

---

### Post by chris53 on 2018-02-16
> **deadflowr said:**
> It doesn't look like you added the virtualbox entry to your sources.
(You only imported the keys)

This one liner should add the entry for you 
```
sudo sh -c 'echo "deb https://download.virtualbox.org/virtualbox/debian xenial  contrib" >> /etc/apt/sources.list.d/virtualbox.org.list' 

```


Also, any reason why you downloaded the 32-bit version?
Seems weird in this day and age to run the 32-bit version if not on a 32-bit OS.

Are you actually on a 32-bit version of Ubuntu?
 
No, Its 64bit.  Atleast it should be!!   Where did you see that!?   BTW I fixed my issue by running:

sudo apt-get install -f    (I guess this updated some packages that i needed as VirtualBox came right up afterwards.)

---

### Post by deadflowr on 2018-02-16
> No, Its 64bit. Atleast it should be!! Where did you see that!?
> virtualbox-5.2:i386 is already the newest version 
i386 is 32-bit
amd64 is 64-bit
Don't let the amd part confuse you, that's for all 64-bit users. Amd or Intel.

---

