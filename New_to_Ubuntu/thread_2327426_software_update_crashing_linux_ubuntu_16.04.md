---
title: "software update crashing linux ubuntu 16.04"
date: 2016-06-10
forum: New to Ubuntu
---

### Post by amr-mahmoud38 on 2016-06-10
Hi
I have installed ubuntu 16.04 (fresh install) 64-bit version 
I used to use the older 14.04 & 15.10 version
now i can't make any update using the update manager it gives me errors 
```
Package operation failed  
The installation or removal of a software package failed 
 
```I don,t know what is went wrong ,
when I try to install any new updates 
can you please help .
I am ready to upload any log files or output from the command window 
that might help resolving this issue 
Thanks very much for your help .

---

### Post by Frogs Hair on 2016-06-10
Hello and Welcome !

Post the output of the following command.

```
sudo apt-get update
```

---

### Post by amr-mahmoud38 on 2016-06-14
```
sudo apt-get update
[sudo] password for admin: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]
Hit:2 [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) xenial InRelease                    
Hit:3 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial InRelease
Get:4 [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]                              
Hit:5 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) xenial InRelease                                                    
Hit:6 [http://ppa.launchpad.net/tuxonice/ppa/ubuntu](http://ppa.launchpad.net/tuxonice/ppa/ubuntu) xenial InRelease                                                    
Hit:7 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial InRelease        
Hit:8 [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) xenial-backports InRelease                 
Fetched 189 kB in 1s (158 kB/s)
Reading package lists... Done
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:3
```

---

### Post by Frogs Hair on 2016-06-14
Is that the entire output , it looks like it's missing the end. Go into Software & Updates  in the other software tab, disable  the PPA > tuxonice-ubuntu-ppa-xenial and run the same command and report back.

---

### Post by amr-mahmoud38 on 2016-06-16
Thanks for the reply 
I have done what you said to disable the tuxonice ppa , but as i entered the software updates 
it suddenly crashed and i uploaded some screen shot of my desktop 
also i applied the same command again as below 

```
sudo apt-get update
[sudo] password for admin: 
Sorry, try again.
[sudo] password for admin: 
Hit:1 [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Hit:3 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) xenial InRelease
Hit:4 [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) xenial-updates InRelease       
Hit:5 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) xenial InRelease         
Hit:6 [http://sa.archive.ubuntu.com/ubuntu](http://sa.archive.ubuntu.com/ubuntu) xenial-backports InRelease     
Hit:7 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) xenial InRelease
Reading package lists... Done
```

please see the attachments

please also see this attachment (the output from the command )

```
sudo apt-get upgrade
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  boot-repair boot-sav boot-sav-extra compiz compiz-core compiz-gnome compiz-plugins-default firefox firefox-locale-en grep
  language-selector-common language-selector-gnome libblkid1 libcompizconfig0 libdecoration0 libfdisk1 libmetacity-private3a libmount1
  libnm-gtk-common libnm-gtk0 libnma-common libnma0 libsmartcols1 libunity-control-center1 libuuid1 linux-libc-dev lshw metacity-common mount
  mtr-tiny network-manager-gnome openssh-client snapd thermald unity-control-center unity-control-center-faces uuid-runtime
37 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 5284 kB/57.3 MB of archives.
After this operation, 4708 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-sav all 4ppa38 [416 kB]
Get:2 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-gtk0 amd64 1.2.0-0ubuntu0.16.04.3 [70.0 kB]
Get:3 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-gtk-common all 1.2.0-0ubuntu0.16.04.3 [5344 B]
Get:4 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 network-manager-gnome amd64 1.2.0-0ubuntu0.16.04.3 [290 kB]
Get:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-repair all 4ppa38 [11.5 kB]
Get:6 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 boot-sav-extra all 4ppa38 [142 kB]
Get:7 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnma0 amd64 1.2.0-0ubuntu0.16.04.3 [66.0 kB]
Get:8 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnma-common all 1.2.0-0ubuntu0.16.04.3 [5328 B]                         
Get:9 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snapd amd64 2.0.8 [4278 kB]                                               
Fetched 5284 kB in 1min 10s (75.0 kB/s)                                                                                                       
Extracting templates from packages: 100%
Setting up util-linux (2.27.1-6ubuntu3.1) ...
insserv: warning: script 'K01pmp-service' missing LSB tags and overrides
insserv: warning: script 'pmp-service' missing LSB tags and overrides
insserv: There is a loop between service plymouth and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop between service pmp-service and udev if started
insserv:  loop involving service udev at depth 1
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service plymouth if started
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!sudo apt-get clean 
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service pmp-service if started
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 6
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service pmp-service and dns-clean if started
insserv:  loop involving service dns-clean at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Frogs Hair on 2016-06-16
Looks like there are other things going on there. Enable the PPA again so it updates and run the following one at a time and post the output. To add code tags to the output, paste the output in the reply box, then highlight the text, and select the # symbol in the reply box.  

```
sudo rm -rf /var/lib/apt/lists/* 
```
```
sudo apt-get clean 
```
```
sudo apt-get update

```

---

### Post by amr-mahmoud38 on 2016-06-17
```
sudo rm -rf /var/lib/apt/lists/*
[sudo] password for admin: 
```

```
sudo apt-get clean

```

```
sudo apt-get update
Get:1 http://archive.canonical.com/ubuntu xenial InRelease [11.5 kB]           
Get:2 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease [17.6 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]    
Get:4 http://sa.archive.ubuntu.com/ubuntu xenial InRelease [247 kB]            
Get:5 http://archive.canonical.com/ubuntu xenial/partner Sources [2236 B]      
Get:6 http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial InRelease [18.0 kB]     
Get:7 http://archive.canonical.com/ubuntu xenial/partner amd64 Packages [2708 B]
Get:8 http://archive.canonical.com/ubuntu xenial/partner i386 Packages [3020 B]
Get:9 http://archive.canonical.com/ubuntu xenial/partner Translation-en [1424 B]
Get:10 http://ppa.launchpad.net/tuxonice/ppa/ubuntu xenial InRelease [17.5 kB] 
Get:11 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease [17.5 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages [86.2 kB]
Get:13 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial/main amd64 Packages [680 B]
Get:14 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial/main i386 Packages [680 B]
Get:15 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial/main Translation-en [356 B]
Get:16 http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial/main amd64 Packages [656 B]
Get:17 http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial/main i386 Packages [656 B]
Get:18 http://ppa.launchpad.net/mkusb/ppa/ubuntu xenial/main Translation-en [740 B]
Get:19 http://ppa.launchpad.net/tuxonice/ppa/ubuntu xenial/main Sources [3256 B]
Get:20 http://ppa.launchpad.net/tuxonice/ppa/ubuntu xenial/main amd64 Packages [48.7 kB]
Get:21 http://security.ubuntu.com/ubuntu xenial-security/main i386 Packages [83.2 kB]
Get:22 http://security.ubuntu.com/ubuntu xenial-security/main Translation-en [34.2 kB]
Get:23 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [5685 B]
Get:24 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [27.2 kB]
Get:25 http://security.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata [158 B]
Get:26 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [23.5 kB]
Get:27 http://security.ubuntu.com/ubuntu xenial-security/universe i386 Packages [23.4 kB]
Get:28 http://security.ubuntu.com/ubuntu xenial-security/universe Translation-en [14.7 kB]
Get:29 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [2329 B]
Get:30 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [4102 B]
Get:31 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [1176 B]
Get:32 http://sa.archive.ubuntu.com/ubuntu xenial-updates InRelease [94.5 kB]  
Get:33 http://ppa.launchpad.net/tuxonice/ppa/ubuntu xenial/main i386 Packages [46.2 kB]
Get:34 http://security.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [1344 B]
Get:35 http://security.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [628 B]
Get:36 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [200 B]
Get:37 http://ppa.launchpad.net/tuxonice/ppa/ubuntu xenial/main Translation-en [15.1 kB]
Get:38 http://sa.archive.ubuntu.com/ubuntu xenial-backports InRelease [92.2 kB]
Get:39 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main amd64 Packages [1864 B]
Get:40 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main i386 Packages [1864 B]
Get:41 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial/main Translation-en [2092 B]
Get:42 http://sa.archive.ubuntu.com/ubuntu xenial/main amd64 Packages [1201 kB]
Get:43 http://sa.archive.ubuntu.com/ubuntu xenial/main i386 Packages [1196 kB]                                                                
Get:44 http://sa.archive.ubuntu.com/ubuntu xenial/main Translation-en [568 kB]                                                                
Get:45 http://sa.archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata [733 kB]                                                         
Get:46 http://sa.archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons [409 kB]                                                            
Get:47 http://sa.archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages [8344 B]                                                          
Get:48 http://sa.archive.ubuntu.com/ubuntu xenial/restricted i386 Packages [8684 B]                                                           
Get:49 http://sa.archive.ubuntu.com/ubuntu xenial/restricted Translation-en [2908 B]                                                          
Get:50 http://sa.archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata [186 B]                                                    
Get:51 http://sa.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7532 kB]                                                           
Get:52 http://sa.archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7512 kB]                                                            
Get:53 http://sa.archive.ubuntu.com/ubuntu xenial/universe Translation-en [4354 kB]                                                           
Get:54 http://sa.archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata [3410 kB]                                                    
Get:55 http://sa.archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons [7448 kB]                                                       
Get:56 http://sa.archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [144 kB]                                                          
Get:57 http://sa.archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]                                                           
Get:58 http://sa.archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]                                                          
Get:58 http://sa.archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]                                                          
Get:59 http://sa.archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata [63.8 kB]                                                  
Get:60 http://sa.archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons [230 kB]                                                      
Get:61 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [213 kB]                                                        
Get:62 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [209 kB]                                                         
Get:63 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [81.3 kB]                                                       
Get:64 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [174 kB]                                                 
Get:65 http://sa.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [136 kB]                                                    
Get:66 http://sa.archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata [157 B]                                            
Get:67 http://sa.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [97.1 kB]                                                   
Get:68 http://sa.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [94.3 kB]                                                    
Get:69 http://sa.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [46.3 kB]                                                   
Get:70 http://sa.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [21.4 kB]                                            
Get:71 http://sa.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [53.8 kB]                                               
Get:72 http://sa.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [1176 B]                                                  
Get:73 http://sa.archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [1344 B]                                                   
Get:74 http://sa.archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en [628 B]                                                   
Get:75 http://sa.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [158 B]                                            
Get:76 http://sa.archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [676 B]                                                       
Get:77 http://sa.archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [676 B]                                                        
Get:78 http://sa.archive.ubuntu.com/ubuntu xenial-backports/main Translation-en [528 B]                                                       
Get:79 http://sa.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [197 B]                                                
Get:80 http://sa.archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata [194 B]                                          
Get:81 http://sa.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [194 B]                                            
Get:82 http://sa.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [194 B]                                          
Fetched 37.2 MB in 3min 45s (165 kB/s)                                                                                                        
Reading package lists... Done
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:2 and /etc/apt/sources.list.d/tuxonice-ubuntu-ppa-xenial.list:3


```

please see the attachment

---

### Post by Frogs Hair on 2016-06-17
Go ahead and try to install the updates if you didn't already.

---

### Post by amr-mahmoud38 on 2016-06-17
after trying to apply the new updates 
```

Package Operation failed 
The installation or removal of a software package failed.

```
can you please check the attachment ,
I am on the same problem  as before

---

### Post by Frogs Hair on 2016-06-17
I think this ppa might be the problem , but ppa software is use at your own risk. If this is something you don't need you should consider removing it.  

tuxonice-ubuntu-ppa-xenial. 

[https://askubuntu.com/questions/307/how-can-ppas-be-removed](https://askubuntu.com/questions/307/how-can-ppas-be-removed)

---

### Post by amr-mahmoud38 on 2016-06-18
As I am trying to execute the second command to install ppa-purge 
please see the below output from command line 
Br 

```
sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  aptitude
The following NEW packages will be installed:
  ppa-purge
0 upgraded, 1 newly installed, 0 to remove and 40 not upgraded.
1 not fully installed or removed.
Need to get 0 B/6312 B of archives.
After this operation, 24.6 kB of additional disk space will be used.
Setting up util-linux (2.27.1-6ubuntu3.1) ...
insserv: warning: script 'K01pmp-service' missing LSB tags and overrides
insserv: warning: script 'pmp-service' missing LSB tags and overrides
insserv: There is a loop between service plymouth and urandom if started
insserv:  loop involving service urandom at depth 4
insserv:  loop involving service hwclock at depth 3
insserv: There is a loop between service pmp-service and udev if started
insserv:  loop involving service udev at depth 1
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Max recursions depth 99 reached
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service plymouth if started
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop at service pmp-service if started
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv:  loop involving service networking at depth 6
insserv:  loop involving service mountdevsubfs at depth 3
insserv:  loop involving service mountkernfs at depth 1
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: Starting pmp-service depends on plymouth and therefore on system facility `$all' which can not be true!
insserv: There is a loop between service pmp-service and dns-clean if started
insserv:  loop involving service dns-clean at depth 1
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package util-linux (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by amr-mahmoud38 on 2016-06-18
thanks ,
The problem have been resolved .
I have reinstalled a  more recent daily version of ubuntu 16.04 
Br

---

