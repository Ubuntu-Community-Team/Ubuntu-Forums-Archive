---
title: "yet more update manager failures"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by bamh1d on 2013-07-16
Well, I thought that the problems I experienced previously with update manager were resolved, but apparently not.  Here is relevant output from the update manager:

E:Unable to synchronize mmap - msync (5: Input/output error), E:The package lists or status file could not be parsed or opened.





Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.10 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.11_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 


(Reading database ... 331582 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.10 (using .../apt_0.8.16~exp12ubuntu10.11_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
debconf: DbDriver "templatedb": could not sync /var/cache/debconf/templates.dat-new: Input/output error
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 man-db
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
debconf: DbDriver "templatedb": could not sync /var/cache/debconf/templates.dat-new: Input/output error
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.1-2ubuntu1) ...
Updating database of manual pages ...
debconf: DbDriver "templatedb": could not sync /var/cache/debconf/templates.dat-new: Input/output error
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apt (0.8.16~exp12ubuntu10.11) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4

I don't understand the problem, much less how to solve it.  Any help would be appreciated.

---

### Post by ibjsb4 on 2013-07-16
Run the commands in post #5 and then do a terminal update.
[http://ubuntuforums.org/showthread.php?t=2143731&p=12641770&viewfull=1#post12641770](http://ubuntuforums.org/showthread.php?t=2143731&p=12641770&viewfull=1#post12641770)

```
sudo apt-get update
```

And please post the errors using code tags please :)

```
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.10 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.11_amd64.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.11) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 


(Reading database ... 331582 files and directories currently installed.)
Preparing to replace apt 0.8.16~exp12ubuntu10.10 (using .../apt_0.8.16~exp12ubuntu10.11_amd64.deb) ...
Unpacking replacement apt ...
Processing triggers for man-db ...
debconf: DbDriver "templatedb": could not sync /var/cache/debconf/templates.dat-new: Input/output error
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 man-db
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
debconf: DbDriver "templatedb": could not sync /var/cache/debconf/templates.dat-new: Input/output error
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.6.1-2ubuntu1) ...
Updating database of manual pages ...
debconf: DbDriver "templatedb": could not sync /var/cache/debconf/templates.dat-new: Input/output error
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up apt (0.8.16~exp12ubuntu10.11) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
```

[ATTACH=CONFIG]244805[/ATTACH]

---

### Post by bamh1d on 2013-07-17
I have run the commands from #5 and include the output from Terminal.
Am I correct in thinking that the terminal update (your last instruction) is performed by the sudo apt-get update command?

```
owner@ubuntu:~$ sudo rm -r /var/lib/apt/lists/* 
[sudo] password for owner: 
owner@ubuntu:~$ sudo mkdir /var/lib/apt/lists/partial 
owner@ubuntu:~$ sudo apt-get update
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://archive.canonical.com precise Release.gpg [198 B]                 
Get:5 http://archive.ubuntu.com precise Release [49.6 kB]            
Get:6 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:7 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:8 http://archive.canonical.com precise Release [7,078 B]                   
Get:9 http://ppa.launchpad.net precise Release [11.9 kB]                       
Get:10 http://archive.canonical.com precise/partner amd64 Packages [7,883 B]   
Get:11 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Get:12 http://security.ubuntu.com precise-security/main amd64 Packages [296 kB]
Get:13 http://archive.canonical.com precise/partner i386 Packages [8,941 B]    
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:14 http://ppa.launchpad.net precise/main Sources [1,150 B]                 
Get:15 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]        
Get:16 http://ppa.launchpad.net precise/main amd64 Packages [2,143 B]          
Get:17 http://ppa.launchpad.net precise/main i386 Packages [2,157 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:18 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:19 http://security.ubuntu.com precise-security/universe amd64 Packages [77.7 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [311 kB] 
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [80.4 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,371 B]
Get:25 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:26 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:27 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:28 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:29 http://security.ubuntu.com precise-security/main Translation-en [144 kB]
Get:30 http://archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]   
Get:31 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]    
Get:32 http://security.ubuntu.com precise-security/multiverse Translation-en [995 B]
Get:33 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:34 http://security.ubuntu.com precise-security/universe Translation-en [49.6 kB]
Get:35 http://archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]    
Get:36 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:37 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:38 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:39 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:40 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:41 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B] 
Get:42 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B] 
Get:43 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]   
Get:44 http://archive.ubuntu.com precise-updates/main amd64 Packages [650 kB]  
Get:45 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:46 http://archive.ubuntu.com precise-updates/universe amd64 Packages [209 kB]
Get:47 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]
Get:48 http://archive.ubuntu.com precise-updates/main i386 Packages [671 kB]   
Get:49 http://archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:50 http://archive.ubuntu.com precise-updates/universe i386 Packages [213 kB]
Get:51 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Get:52 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:53 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:54 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:55 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:56 http://archive.ubuntu.com precise/main Translation-en [726 kB]          
Get:57 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]   
Get:58 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]   
Get:59 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]    
Get:60 http://archive.ubuntu.com precise-updates/main Translation-en [299 kB]  
Get:61 http://archive.ubuntu.com precise-updates/multiverse Translation-en [7,834 B]
Get:62 http://archive.ubuntu.com precise-updates/restricted Translation-en [2,432 B]
Get:63 http://archive.ubuntu.com precise-updates/universe Translation-en [123 kB]
Fetched 20.0 MB in 1min 40s (199 kB/s)                                         
Reading package lists... Done
owner@ubuntu:~$ 

```

---

### Post by hansdown on 2013-07-17
Hi bamh1d.

A slight variation of ibjsb4's post may be better.

> sudo rm -rf /var/lib/apt/lists/* 

> sudo apt-get update

> sudo apt-get upgrade

---

### Post by ibjsb4 on 2013-07-17
Hay hansdown :)  

Hopefully the upgrade will work, but I been looking at samba4.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Unknown+parameter+encountered&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Unknown+parameter+encountered&sa=Search&cof=FORID:9)

---

### Post by hansdown on 2013-07-17
:D> **ibjsb4 said:**
> Hay hansdown :)  

Hopefully the upgrade will work, but I been looking at samba4.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Unknown+parameter+encountered&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Unknown+parameter+encountered&sa=Search&cof=FORID:9)

Good point.

Not trying to 'dis 'ya.

My emoticoms don't seem to work?

---

### Post by bamh1d on 2013-07-17
so...the problem may be the Samba4 installation? Should I remove it to see if doing so solves the problem with update manager?  :confused:
If so, what are the precise steps I should take?

---

### Post by ibjsb4 on 2013-07-18
Did the upgrade work (post #4 - sudo apt-get upgrade)?

 Not sure what your skill level is, so in case you need an explanation of apt-get commands:

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Apt-get is a text only (no GUI) package manager.

And 'hansdown', please jump in as I do not use samba and appreciate all input.

---

### Post by bamh1d on 2013-07-18
I have just now run the commands suggested  by hansdown, results shown below.
Not sure how to interpret this, as several things apparently did not go as expected.
Samba4 does seem to consistently resist update/upgrade.
What's next?

```
owner@ubuntu:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for owner: 
owner@ubuntu:~$ sudo apt-get update
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:2 http://archive.canonical.com precise Release.gpg [198 B]                 
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:4 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Get:5 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:6 http://archive.ubuntu.com precise Release [49.6 kB]
Get:7 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:8 http://archive.canonical.com precise Release [7,078 B]                   
Get:9 http://ppa.launchpad.net precise Release [11.9 kB]                       
Get:10 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Get:11 http://archive.canonical.com precise/partner amd64 Packages [7,883 B]   
Get:12 http://security.ubuntu.com precise-security/main amd64 Packages [296 kB]
Get:13 http://ppa.launchpad.net precise/main Sources [1,150 B]                 
Get:14 http://archive.canonical.com precise/partner i386 Packages [8,941 B]    
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:15 http://archive.ubuntu.com precise/main amd64 Packages [1,273 kB]        
Get:16 http://ppa.launchpad.net precise/main amd64 Packages [2,143 B]          
Get:17 http://ppa.launchpad.net precise/main i386 Packages [2,157 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:18 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:19 http://security.ubuntu.com precise-security/universe amd64 Packages [77.7 kB]
Get:20 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:21 http://security.ubuntu.com precise-security/main i386 Packages [311 kB] 
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en                
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [80.4 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,371 B]
Get:25 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:26 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:27 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:28 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:29 http://security.ubuntu.com precise-security/main Translation-en [144 kB]
Get:30 http://security.ubuntu.com precise-security/multiverse Translation-en [995 B]
Get:31 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]
Get:32 http://security.ubuntu.com precise-security/universe Translation-en [49.6 kB]
Get:33 http://archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]   
Get:34 http://archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]    
Get:35 http://archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]    
Get:36 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:37 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:38 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:39 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:40 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:41 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B] 
Get:42 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B] 
Get:43 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]   
Get:44 http://archive.ubuntu.com precise-updates/main amd64 Packages [650 kB]  
Get:45 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:46 http://archive.ubuntu.com precise-updates/universe amd64 Packages [209 kB]
Get:47 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]
Get:48 http://archive.ubuntu.com precise-updates/main i386 Packages [671 kB]   
Get:49 http://archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:50 http://archive.ubuntu.com precise-updates/universe i386 Packages [213 kB]
Get:51 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Get:52 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:53 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:54 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:55 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:56 http://archive.ubuntu.com precise/main Translation-en [726 kB]          
Get:57 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]   
Get:58 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]   
Get:59 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]    
Get:60 http://archive.ubuntu.com precise-updates/main Translation-en [299 kB]  
Get:61 http://archive.ubuntu.com precise-updates/multiverse Translation-en [7,834 B]
Get:62 http://archive.ubuntu.com precise-updates/restricted Translation-en [2,432 B]
Get:63 http://archive.ubuntu.com precise-updates/universe Translation-en [123 kB]
Fetched 20.0 MB in 2min 0s (165 kB/s)                                          
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages  Hash Sum mismatch


W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.
owner@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libxml2 python-libxml2
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 860 kB of archives.
After this operation, 5,120 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ precise-security/main libxml2 amd64 2.7.8.dfsg-5.1ubuntu4.6 [673 kB]
Get:2 http://security.ubuntu.com/ubuntu/ precise-security/main python-libxml2 amd64 2.7.8.dfsg-5.1ubuntu4.6 [187 kB]
Fetched 860 kB in 2s (333 kB/s)     
(Reading database ... 331582 files and directories currently installed.)
Preparing to replace libxml2 2.7.8.dfsg-5.1ubuntu4.5 (using .../libxml2_2.7.8.dfsg-5.1ubuntu4.6_amd64.deb) ...
Unpacking replacement libxml2 ...
Preparing to replace python-libxml2 2.7.8.dfsg-5.1ubuntu4.5 (using .../python-libxml2_2.7.8.dfsg-5.1ubuntu4.6_amd64.deb) ...
Unpacking replacement python-libxml2 ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
Setting up libxml2 (2.7.8.dfsg-5.1ubuntu4.6) ...
Setting up python-libxml2 (2.7.8.dfsg-5.1ubuntu4.6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
owner@ubuntu:~$ 

```

---

### Post by ibjsb4 on 2013-07-18
This is what Im looking at

[ATTACH=CONFIG]244847[/ATTACH]

I think you should remove it and if you want, replace it with samba.

In terminal:

```
sudo apt-get remove --purge samba4
```

---

### Post by hansdown on 2013-07-18
bamh1d, I was curious about the 32bit, **and** 64bit packages in your lists.

 ibjsb4 has a good plan.

---

### Post by bamh1d on 2013-07-18
I removed Samba4 as suggested and replaced it with Samba.  Using Samba I am able to connect to shared folders on other computers in my WiFi LAN.
And Update Manager runs successfully!
Many thanks to you, ibjsb4 and hansdown , for helping me to find my way through the wilderness.

---

### Post by newb85 on 2013-07-18
> **ibjsb4 said:**
> I think you should remove it and if you want, replace it with samba.

samba is a dependency of samba4, so it's probably already installed.  If it was automatically installed, a future autoremove command might unexpectedly remove it.  You might want to run 
```
sudo apt-get autoremove
```
after purging samba4, just to check.

---

### Post by bamh1d on 2013-07-18
Hansdown,
please see my earlier message and accept my many thanks for your help.  Removing Samba4 seems to have resolved the problem my Update Manager had.
As far as I know, I am running a 64-bit version of Ubuntu 12.04.  I used the Wubi to install a dual boot OS.  The processor is an Intel Core&#8482;2 CPU T7200 @ 2.00GHz × 2 running a 64 bit instruction set. 
What 32 bit packages are you referring to?

---

### Post by hansdown on 2013-07-18
Glad you fixed it, bamh1d.



 ibjsb4 had it pegged.:D

I was looking at the i386, and amd64 parts.

I thought you might be running a 32bit install.

---

