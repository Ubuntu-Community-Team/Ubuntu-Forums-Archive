---
title: "Fixing dependency hell involving VLC PPA and libebml4/libebml3"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by Paperfairy on 2014-05-21
Okay, so I just learned my lesson about PPAs and why they're bad. I'll never do it again, I swear.

Prior to upgrading to Trusty, I added the stable PPA for VLC to get the newest version of VLC. I then upgraded to Trusty (from saucy) **without removing the ppas**. Yes, I know this is stupid. Oh well.

So, here's where I'm having trouble:

**sudo apt-fast update && sudo apt-fast upgrade --force-yes -y && sudo apt-get autoremove --force-yes -y && sudo apt-get autoclean && sudo apt-get clean**
```
Ign http://ubuntu.mirror.constant.com trusty InRelease
Ign http://ubuntu.mirror.constant.com trusty-updates InRelease                                                                                                                  
Ign http://ubuntu.mirror.constant.com trusty-backports InRelease                                                                                                                
Ign http://ubuntu.mirror.constant.com trusty-security InRelease                                                                                                                 
Hit http://ubuntu.mirror.constant.com trusty Release.gpg                                                                                                                        
Get:1 http://ubuntu.mirror.constant.com trusty-updates Release.gpg [933 B]                                                                                                      
Get:2 http://ubuntu.mirror.constant.com trusty-backports Release.gpg [933 B]                                                
Get:3 http://ubuntu.mirror.constant.com trusty-security Release.gpg [933 B]                                                 
Ign http://archive.canonical.com trusty InRelease                                                                            
Hit http://ubuntu.mirror.constant.com trusty Release                                        
Ign http://extras.ubuntu.com trusty InRelease                                               
Ign http://ppa.launchpad.net trusty InRelease                                                                                            
Get:4 http://ubuntu.mirror.constant.com trusty-updates Release [58.5 kB]                                                                 
Ign http://dl.google.com stable InRelease                                                                                                       
Hit http://archive.canonical.com trusty Release.gpg                                                                                             
Get:5 http://ubuntu.mirror.constant.com trusty-backports Release [58.6 kB]                                        
Hit http://extras.ubuntu.com trusty Release.gpg                                                                       
Get:6 http://ppa.launchpad.net trusty Release.gpg [316 B]                                                             
Get:7 http://ubuntu.mirror.constant.com trusty-security Release [58.5 kB]                                                                  
Ign http://dl.google.com stable InRelease                                                                                 
Hit http://ubuntu.mirror.constant.com trusty/main Sources                                                                                  
Hit http://archive.canonical.com trusty Release                                                                   
Hit http://extras.ubuntu.com trusty Release                                                                        
Hit http://ubuntu.mirror.constant.com trusty/restricted Sources                                                    
Hit http://ubuntu.mirror.constant.com trusty/universe Sources                                                      
Hit http://ubuntu.mirror.constant.com trusty/multiverse Sources                             
Get:8 http://ppa.launchpad.net trusty Release [14.0 kB]                                     
Hit http://ubuntu.mirror.constant.com trusty/main amd64 Packages                                                          
Hit http://ubuntu.mirror.constant.com trusty/restricted amd64 Packages                      
Ign http://dl.google.com stable InRelease                                                   
Hit http://archive.canonical.com trusty/partner Sources                                     
Hit http://extras.ubuntu.com trusty/main Sources                                            
Hit http://ubuntu.mirror.constant.com trusty/universe amd64 Packages                        
Get:9 http://ppa.launchpad.net trusty/main amd64 Packages [10.2 kB]                         
Hit http://ubuntu.mirror.constant.com trusty/multiverse amd64 Packages                                                                   
Hit http://archive.canonical.com trusty/partner amd64 Packages                                                    
Hit http://extras.ubuntu.com trusty/main amd64 Packages                                     
Hit http://ubuntu.mirror.constant.com trusty/main i386 Packages                             
Hit http://dl.google.com stable Release.gpg                                                 
Hit http://ubuntu.mirror.constant.com trusty/restricted i386 Packages                       
Hit http://ubuntu.mirror.constant.com trusty/universe i386 Packages                         
Hit http://ubuntu.mirror.constant.com trusty/multiverse i386 Packages                       
Get:10 http://ppa.launchpad.net trusty/main i386 Packages [10.2 kB]                         
Get:11 http://ubuntu.mirror.constant.com trusty-updates/main Sources [38.9 kB]                                               
Hit http://archive.canonical.com trusty/partner i386 Packages                                                                
Hit http://extras.ubuntu.com trusty/main i386 Packages                                                
Get:12 http://ubuntu.mirror.constant.com trusty-updates/restricted Sources [14 B]
Get:13 http://ubuntu.mirror.constant.com trusty-updates/universe Sources [24.2 kB]
Hit http://dl.google.com stable Release.gpg                            
Get:14 http://ubuntu.mirror.constant.com trusty-updates/multiverse Sources [2,234 B]
Get:15 http://ubuntu.mirror.constant.com trusty-updates/main amd64 Packages [89.8 kB]
Get:16 http://ubuntu.mirror.constant.com trusty-updates/restricted amd64 Packages [14 B]
Get:17 http://ubuntu.mirror.constant.com trusty-updates/universe amd64 Packages [65.2 kB]
Hit http://dl.google.com stable Release.gpg               
Get:18 http://ubuntu.mirror.constant.com trusty-updates/multiverse amd64 Packages [7,089 B]
Get:19 http://ubuntu.mirror.constant.com trusty-updates/main i386 Packages [88.0 kB]
Get:20 http://ubuntu.mirror.constant.com trusty-updates/restricted i386 Packages [14 B]
Get:21 http://ubuntu.mirror.constant.com trusty-updates/universe i386 Packages [65.4 kB]
Hit http://dl.google.com stable Release                   
Get:22 http://ubuntu.mirror.constant.com trusty-updates/multiverse i386 Packages [7,273 B]
Get:23 http://ubuntu.mirror.constant.com trusty-backports/main Sources [14 B]      
Hit http://dl.google.com stable Release                                
Get:24 http://ubuntu.mirror.constant.com trusty-backports/restricted Sources [14 B]
Get:25 http://ubuntu.mirror.constant.com trusty-backports/universe Sources [1,786 B]
Get:26 http://ubuntu.mirror.constant.com trusty-backports/multiverse Sources [14 B]
Get:27 http://ubuntu.mirror.constant.com trusty-backports/main amd64 Packages [14 B]
Get:28 http://ubuntu.mirror.constant.com trusty-backports/restricted amd64 Packages [14 B]
Get:29 http://ubuntu.mirror.constant.com trusty-backports/universe amd64 Packages [1,685 B]
Get:30 http://ubuntu.mirror.constant.com trusty-backports/multiverse amd64 Packages [14 B]
Get:31 http://ubuntu.mirror.constant.com trusty-backports/main i386 Packages [14 B]
Get:32 http://ubuntu.mirror.constant.com trusty-backports/restricted i386 Packages [14 B]
Get:33 http://ubuntu.mirror.constant.com trusty-backports/universe i386 Packages [1,704 B]
Get:34 http://ubuntu.mirror.constant.com trusty-backports/multiverse i386 Packages [14 B]
Hit http://dl.google.com stable Release                                 
Get:35 http://ubuntu.mirror.constant.com trusty-security/main Sources [14.7 kB]
Get:36 http://ubuntu.mirror.constant.com trusty-security/restricted Sources [14 B]            
Get:37 http://ubuntu.mirror.constant.com trusty-security/universe Sources [4,212 B]
Get:38 http://ubuntu.mirror.constant.com trusty-security/multiverse Sources [687 B]
Get:39 http://ubuntu.mirror.constant.com trusty-security/main amd64 Packages [47.0 kB]
Get:40 http://ubuntu.mirror.constant.com trusty-security/restricted amd64 Packages [14 B]
Get:41 http://ubuntu.mirror.constant.com trusty-security/universe amd64 Packages [17.7 kB]
Hit http://dl.google.com stable/main amd64 Packages                     
Get:42 http://ubuntu.mirror.constant.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:43 http://ubuntu.mirror.constant.com trusty-security/main i386 Packages [45.1 kB]
Get:44 http://ubuntu.mirror.constant.com trusty-security/restricted i386 Packages [14 B]
Hit http://dl.google.com stable/main i386 Packages                          
Get:45 http://ubuntu.mirror.constant.com trusty-security/universe i386 Packages [17.7 kB]
Get:46 http://ubuntu.mirror.constant.com trusty-security/multiverse i386 Packages [1,404 B]
Hit http://dl.google.com stable/main amd64 Packages          
Hit http://dl.google.com stable/main i386 Packages
Hit http://dl.google.com stable/main amd64 Packages
Hit http://dl.google.com stable/main i386 Packages
Fetched 756 kB in 2s (365 kB/s)
Reading package lists... Done
 
 Working... this may take a while.
E: Unmet dependencies. Try using -f.

No files to download.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not installed
 vlc-nox : Depends: libebml4 but it is not installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try using -f.

```

So I follow the instructions:
**sudo apt-get install -f**

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libebml4
The following NEW packages will be installed:
  libebml4
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
7 not fully installed or removed.
Need to get 0 B/51.7 kB of archives.
After this operation, 178 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 206914 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: error processing archive /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0
Errors were encountered while processing:
 /var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So now I know what the problem is - libebml4 and 3 both are claiming to be the same thing. My google-fu has led me to threads where individuals have used Synaptic to fix the problem. I do not have this installed, nor can I install it (or anything... and no, I don't have ppa-purge either).

**sudo apt-get install synaptic**
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not going to be installed
 vlc-nox : Depends: libebml4 but it is not going to be installed
           Recommends: libdvdcss2 but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

My attempts to manually remove '/usr/lib/x86_64-linux-gnu/libebml.so.4' '/var/cache/apt/archives/libebml4_1.3.0-2_amd64.deb' or purge any of the aforementioned packages also have no impact and lead me back into the circle.

What's my next step?

---

### Post by squakie on 2014-05-21
Did you edit /etc/apt/sources.list and remove those PPA's now prior to trying to go any further?  gksudo gedit /etc/apt/sources.list

Depending on what you've done gksudo may not be installed on your system - so if you get an error try just sudo gedit /etc/apt/sources.list

If you can get that straightened out, install a package manager - sudo apt-get install synaptic

Always use the package manager to install packages.  There is usually a reason why some version of an application may be at a lower release than that on the applications' website, and installing from the normal dependencies with apt - or a front end like synaptic - will automatically get the dependencies.

---

### Post by mc4man on 2014-05-21
libebml3:amd64 1.3.0-0~ppa0 did not come from the vlc ppa, it came from here - [https://launchpad.net/~jacob/+archive/media](https://launchpad.net/~jacob/+archive/media)

To fix either try removing  - 
sudo apt-get purge libebml3
or find the libebml4 package in /var/cache/apt/archives or [download it ]("http://packages.ubuntu.com/trusty/libebml4") & force an overwrite with dpkg
sudo dpkg -i --force-overwrite /path/to/libebml4_1.3.0-2_amd64.deb
ex.
> .....
The following packages have unmet dependencies:
 libmatroska6 : Depends: libebml4 but it is not going to be installed
 vlc-nox : Depends: libebml4 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
doug@doug-Lenovo-IdeaPad-Y510P:~$ sudo dpkg -i --force-overwrite  /home/doug/Downloads/libebml4_1.3.0-2_amd64.deb 
(Reading database ... 244226 files and directories currently installed.)
Preparing to unpack .../libebml4_1.3.0-2_amd64.deb ...
Unpacking libebml4:amd64 (1.3.0-2) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/lib/x86_64-linux-gnu/libebml.so.4', which is also in package libebml3:amd64 1.3.0-0~ppa0
Setting up libebml4:amd64 (1.3.0-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...


After that remove  libebml3, install vlc, ect.

---

### Post by Paperfairy on 2014-05-21
The following command fixed the problem:

**cd ~/Downloads && wget [http://mirrors.kernel.org/ubuntu/pool/universe/libe/libebml/libebml4_1.3.0-2_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/universe/libe/libebml/libebml4_1.3.0-2_amd64.deb) && sudo dpkg -i --force-overwrite /home/paperfairy/Downloads/libebml4_1.3.0-2_amd64.deb && sudo apt-get purge libebml3**

Or, for those of you reading from the future: download the aforementioned .deb file, use dpkg to overwrite the original file, then purge the old libebml3.

Thanks everybody!

---

