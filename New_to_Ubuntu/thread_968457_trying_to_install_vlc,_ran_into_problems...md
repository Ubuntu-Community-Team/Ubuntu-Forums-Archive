---
title: "trying to install vlc, ran into problems.."
date: 2008-11-02
forum: New to Ubuntu
---

### Post by fignig on 2008-11-02
so i just upgraded yesterday to intrepid ibex, only b/c of the adobe flash issue, that is yet to be resolved.

but i digress, there's a problem when i'm trying to install the vlc player, thru synaptic and the terminal. errors keep popping up left and right. and when i closed synaptic the update manager was trying to update another thing, not really sure what it is, maybe u could tell me?

E: /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_amd64.deb: trying to overwrite `/usr/lib/libvlccore.so.0.0.2', which is also in package libvlc0
E: /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_amd64.deb: trying to overwrite `/usr/lib/libvlc.so.2.0.2', which is also in package libvlc0

---

### Post by fignig on 2008-11-02
can anyone tell me what this means? or anything i can do to reslove this issue?

---

### Post by fignig on 2008-11-02
one of the error boxes told me to run: sudo apt-get install -f

this is what it displayed:
```
pete@pete:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavutil1d libswscale1d libvlc0 libpostproc1d
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libvlc2 libvlccore0
The following NEW packages will be installed:
  libvlc2 libvlccore0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/430kB of archives.
After this operation, 1065kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154610 files and directories currently installed.)
Unpacking libvlccore0 (from .../libvlccore0_0.9.4-1ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libvlccore.so.0.0.2', which is also in package libvlc0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libvlc2 (from .../libvlc2_0.9.4-1ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libvlc.so.2.0.2', which is also in package libvlc0
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_amd64.deb
 /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Crafty Kisses on 2008-11-02
Try running the following commands:
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
```
Once you have run those commands, run the following command:
```
sudo apt-get install vlc
```
Let's see if that brings VLC to life.

---

### Post by fignig on 2008-11-02
okay i tried doing those commands, and the problem is still here. the following is what i did in my terminal to help fix the problem, but it seems to still be the problem:

```

pete@pete:~$ sudo dpkg --configure -a
[sudo] password for pete: 
dpkg: dependency problems prevent configuration of vlc-nox:
 vlc-nox depends on libvlc2 (>= 0.9.1); however:
  Package libvlc2 is not installed.
 vlc-nox depends on libvlccore0 (>= 0.9.1); however:
  Package libvlccore0 is not installed.
dpkg: error processing vlc-nox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of vlc:
 vlc depends on vlc-nox (= 0.9.4-1ubuntu3); however:
  Package vlc-nox is not configured yet.
 vlc depends on libvlccore0 (>= 0.9.1); however:
  Package libvlccore0 is not installed.
dpkg: error processing vlc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 vlc-nox
 vlc
pete@pete:~$ sudo apt-get clean
pete@pete:~$ sudo apt-get update
Hit http://packages.medibuntu.org intrepid Release.gpg
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US                   
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Hit http://us.archive.ubuntu.com intrepid Release.gpg                          
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]                       
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg        
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Ign http://packages.medibuntu.org intrepid/free Translation-en_US              
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://security.ubuntu.com intrepid-security Release                       
Hit http://us.archive.ubuntu.com intrepid Release                              
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com intrepid-updates Release                      
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Hit http://us.archive.ubuntu.com intrepid/main Packages
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://us.archive.ubuntu.com intrepid/main Sources                         
Hit http://us.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://us.archive.ubuntu.com intrepid/universe Packages                    
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://us.archive.ubuntu.com intrepid/universe Sources                     
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://packages.medibuntu.org intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources      
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages  
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://packages.medibuntu.org intrepid/free Packages 
Get:2 http://packages.medibuntu.org intrepid/non-free Packages [12.0kB]
Fetched 12.0kB in 1s (6289B/s)
Reading package lists... Done
pete@pete:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  vlc: Depends: libvlccore0 (>= 0.9.1) but it is not going to be installed
  vlc-nox: Depends: libvlc2 (>= 0.9.1) but it is not going to be installed
           Depends: libvlccore0 (>= 0.9.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
pete@pete:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libavutil1d libswscale1d libvlc0 libpostproc1d
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libvlc2 libvlccore0
The following NEW packages will be installed:
  libvlc2 libvlccore0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 430kB of archives.
After this operation, 1065kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/multiverse libvlccore0 0.9.4-1ubuntu3 [382kB]
Get:2 http://us.archive.ubuntu.com intrepid/multiverse libvlc2 0.9.4-1ubuntu3 [48.1kB]
Fetched 430kB in 2s (204kB/s)
(Reading database ... 154610 files and directories currently installed.)
Unpacking libvlccore0 (from .../libvlccore0_0.9.4-1ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libvlccore.so.0.0.2', which is also in package libvlc0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking libvlc2 (from .../libvlc2_0.9.4-1ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_amd64.deb (--unpack):
 trying to overwrite `/usr/lib/libvlc.so.2.0.2', which is also in package libvlc0
Errors were encountered while processing:
 /var/cache/apt/archives/libvlccore0_0.9.4-1ubuntu3_amd64.deb
 /var/cache/apt/archives/libvlc2_0.9.4-1ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by fignig on 2008-11-02
anyone?

---

### Post by kansasnoob on 2008-11-02
I don't see where you ever ran

```
sudo apt-get autoremove
```

as it says to here:

> The following packages were automatically installed and are no longer required:
  libavutil1d libswscale1d libvlc0 libpostproc1d
Use 'apt-get autoremove' to remove them.


Then once again run:

```
sudo apt-get -f install
```

---

### Post by sdowney717 on 2008-11-02
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

gives some instructions to follow

"vlc is already the newest version."
have you tried removing it first?

sudo apt-get remove --purge vlc

---

### Post by fignig on 2008-11-03
> **sdowney717 said:**
> [http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

gives some instructions to follow

"vlc is already the newest version."
have you tried removing it first?

sudo apt-get remove --purge vlc

this is what i get when i try to remove vlc w/ that command...

```

pete@pete:~$ sudo apt-get remove --purge vlc
[sudo] password for pete: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  vlc-nox: Depends: libvlc2 (>= 0.9.1) but it is not going to be installed
           Depends: libvlccore0 (>= 0.9.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by fignig on 2008-11-03
this problem is really getting on my nerves, can someone please help?

---

### Post by adaur on 2008-11-28
I've been having the same issue and all of the above fixes never worked for me either.  I finally got it to work tonight.  

I opened Synaptic Package Manager, searched for VLC.  I marked vlc, vlc-nox and libvlccore0 and libvlc2 for complete removal.  Once that finished, I marked vlc for installation and now it works.

---

### Post by Yfrwlf on 2009-01-11
> **adaur said:**
> I've been having the same issue and all of the above fixes never worked for me either.  I finally got it to work tonight.  

I opened Synaptic Package Manager, searched for VLC.  I marked vlc, vlc-nox and libvlccore0 and libvlc2 for complete removal.  Once that finished, I marked vlc for installation and now it works.

That worked for me when vlccore1 wouldn't install, I think it was because core0 was still there, but removing everything VLC and then installing VLC fixed it for me.

---

