---
title: "Java installation ... please help!"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-27
```
****@****:~$ sudo apt-get purge openjdk*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openjdk-6-demo' for regex 'openjdk*'
Note, selecting 'openjdk-7-jre-headless' for regex 'openjdk*'
Note, selecting 'uwsgi-plugin-jwsgi-openjdk-6' for regex 'openjdk*'
Note, selecting 'openjdk-jre' for regex 'openjdk*'
Note, selecting 'openjdk-7-source' for regex 'openjdk*'
Note, selecting 'openjdk-6-dbg' for regex 'openjdk*'
Note, selecting 'openjdk7-jdk' for regex 'openjdk*'
Note, selecting 'openjdk-6-doc' for regex 'openjdk*'
Note, selecting 'openjdk-7-jre-zero' for regex 'openjdk*'
Note, selecting 'openjdk-7-demo' for regex 'openjdk*'
Note, selecting 'openjdk-6-jre-headless' for regex 'openjdk*'
Note, selecting 'openjdk-6-jdk' for regex 'openjdk*'
Note, selecting 'openjdk-6-jre' for regex 'openjdk*'
Note, selecting 'openjdk-6-jre-lib' for regex 'openjdk*'
Note, selecting 'openjdk-6-jre-zero' for regex 'openjdk*'
Note, selecting 'openjdk-7-dbg' for regex 'openjdk*'
Note, selecting 'openjdk-7-doc' for regex 'openjdk*'
Note, selecting 'openjdk-7-jdk' for regex 'openjdk*'
Note, selecting 'openjdk-7-jre' for regex 'openjdk*'
Note, selecting 'openjdk-6-source' for regex 'openjdk*'
Note, selecting 'openjdk-7-jre-lib' for regex 'openjdk*'
Note, selecting 'uwsgi-plugin-jvm-openjdk-6' for regex 'openjdk*'
Package uwsgi-plugin-jvm-openjdk-6 is not installed, so not removed
Package uwsgi-plugin-jwsgi-openjdk-6 is not installed, so not removed
Package openjdk-6-dbg is not installed, so not removed
Package openjdk-6-demo is not installed, so not removed
Package openjdk-6-doc is not installed, so not removed
Package openjdk-6-jdk is not installed, so not removed
Package openjdk-6-jre is not installed, so not removed
Package openjdk-6-jre-headless is not installed, so not removed
Package openjdk-6-jre-lib is not installed, so not removed
Package openjdk-6-source is not installed, so not removed
Package openjdk-6-jre-zero is not installed, so not removed
Package openjdk-7-dbg is not installed, so not removed
Package openjdk-7-demo is not installed, so not removed
Package openjdk-7-doc is not installed, so not removed
Package openjdk-7-jdk is not installed, so not removed
Package openjdk-7-jre is not installed, so not removed
Package openjdk-7-jre-headless is not installed, so not removed
Package openjdk-7-jre-lib is not installed, so not removed
Package openjdk-7-jre-zero is not installed, so not removed
Package openjdk-7-source is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
****@****:~$ sudo add-apt-repository ppa:eugenesan/java
You are about to add the following PPA to your system:
 
 More info: [https://launchpad.net/~eugenesan/+archive/java](https://launchpad.net/~eugenesan/+archive/java)
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.tJ9tlg4zwf --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4346FBB158F4022C896164EEE61380B28313A596
gpg: requesting key 8313A596 from hkp server keyserver.ubuntu.com
gpg: key 8313A596: public key "Launchpad synergy+" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
****@****:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise InRelease                             
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:2 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise Release.gpg [198 B]                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:3 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.8 kB]                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Get:6 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:8 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise Release [49.6 kB]                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [550 B]                    
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [1,376 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:11 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates Release [49.6 kB]          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:12 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [21.1 kB]      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7,120 B]  
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [65.9 kB]
Get:18 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/main Sources [934 kB]              
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [17.4 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:22 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:23 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
Get:24 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                                
Get:25 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]                                                              
Get:26 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]                                                         
Get:27 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]                                                          
Get:28 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                          
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/main TranslationIndex                                                                         
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                   
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/restricted TranslationIndex                                                                   
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/universe TranslationIndex                                                                     
Get:29 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/main Sources [117 kB]                                                              
Get:30 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]                                                       
Get:31 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/universe Sources [28.2 kB]                                                         
Get:32 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]                                                       
Get:33 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/main i386 Packages [299 kB]                                                        
Get:34 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]                                                 
Get:35 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/universe i386 Packages [81.6 kB]                                                   
Get:36 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,049 B]                                                 
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/main TranslationIndex                                                                 
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                           
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                           
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                             
Get:37 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/main Sources [1,346 B]                                                           
Get:38 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                                        
Get:39 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/universe Sources [6,873 B]                                                       
Get:40 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]                                                     
Get:41 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/main i386 Packages [929 B]                                                       
Get:42 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                  
Get:43 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/universe i386 Packages [6,117 B]                                                 
Get:44 [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]                                                 
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/main TranslationIndex                                                               
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                         
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                         
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                           
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/main Translation-en                                                                           
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/multiverse Translation-en                                                                     
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/restricted Translation-en                                                                     
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise/universe Translation-en                                                                       
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/main Translation-en                                                                   
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                             
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/restricted Translation-en                                                             
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-updates/universe Translation-en                                                               
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/main Translation-en                                                                 
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                           
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/restricted Translation-en                                                           
Hit [http://id.archive.ubuntu.com](http://id.archive.ubuntu.com) precise-backports/universe Translation-en                                                             
Fetched 13.2 MB in 2min 8s (103 kB/s)                                                                                                  
Reading package lists... Done
****@****:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11 java-common
Suggested packages:
  default-jre equivs ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho
The following NEW packages will be installed:
  gsfonts-x11 java-common oracle-java7-installer
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
Need to get 85.1 kB of archives.
After this operation, 450 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/eugenesan/java/ubuntu/](http://ppa.launchpad.net/eugenesan/java/ubuntu/) precise/main oracle-java7-installer all 7u3-0~eugenesan~precise4 [14.2 kB]
Get:2 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main java-common all 0.43ubuntu2 [61.7 kB]
Get:3 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main gsfonts-x11 all 0.22 [9,108 B]
Fetched 85.1 kB in 2s (34.2 kB/s) 
Preconfiguring packages ...
Selecting previously unselected package java-common.
(Reading database ... 153835 files and directories currently installed.)
Unpacking java-common (from .../java-common_0.43ubuntu2_all.deb) ...
Selecting previously unselected package oracle-java7-installer.
Unpacking oracle-java7-installer (from .../oracle-java7-installer_7u3-0~eugenesan~precise4_all.deb) ...
Selecting previously unselected package gsfonts-x11.
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.22_all.deb) ...
Processing triggers for doc-base ...
Processing 2 added doc-base files...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for fontconfig ...
Setting up java-common (0.43ubuntu2) ...
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-27 12:58:39--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 125.160.18.98, 125.160.18.84
Connecting to download.oracle.com (download.oracle.com)|125.160.18.98|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-06-27 12:58:39--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-27 12:58:40--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|125.160.18.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  136K=0.04s

2012-06-27 12:58:40 (136 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up gsfonts-x11 (0.22) ...
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
****@****:~$ 
```

Please help!

---

### Post by QIII on 2012-06-27
Unfortunately, there is something wrong with Eugene San's ppa.

Please see the Java wiki link in my signature.  Down in the Java 7 section, I added a link that says something like "Using webupd8.org's strikingly simple method".

Try that.

Edit:  Remove the Eugene San ppa first!

---

### Post by czgirb on 2012-06-27
> **QIII said:**
> Unfortunately, there is something wrong with Eugene San's ppa.

Please see the Java wiki link in my signature.  Down in the Java 7 section, I added a link that says something like "Using webupd8.org's strikingly simple method".

Try that.

Edit:  Remove the Eugene San ppa first!

How to remove **Eugene San ppa** ?
Please guide me ....
Thank you.

---

### Post by nothingspecial on 2012-06-27
> **czgirb said:**
> How to remove **Eugene San ppa** ?
Please guide me ....
Thank you.
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:eugenesan/java
```

---

### Post by czgirb on 2012-06-27
> **nothingspecial said:**
> ```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:eugenesan/java
```

> 
****@****:~$ sudo apt-get install ppa-purge
[sudo] password for ****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libept1.4.12 libio-string-perl libparse-debianchangelog-perl
  libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libept1.4.12 libio-string-perl libparse-debianchangelog-perl
  libsub-name-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 3,019 kB of archives.
After this operation, 9,277 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main libboost-iostreams1.46.1 i386 1.46.1-7ubuntu3 [39.9 kB]
Get:2 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main libcwidget3 i386 0.5.16-3.1ubuntu1 [392 kB]
Get:3 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main libept1.4.12 i386 1.0.6~exp1ubuntu1 [129 kB]
Get:4 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main aptitude i386 0.6.6-1ubuntu1 [2,352 kB]
Get:5 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main libsub-name-perl i386 0.05-1build2 [9,536 B]
Get:6 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:7 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main libio-string-perl all 1.08-2 [12.0 kB]
Get:8 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Get:9 [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 3,019 kB in 25s (120 kB/s)                                             
Selecting previously unselected package libboost-iostreams1.46.1.
(Reading database ... 154066 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-7ubuntu3_i386.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_i386.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.6~exp1ubuntu1_i386.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.6-1ubuntu1_i386.deb) ...
Selecting previously unselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build2_i386.deb) ...
Selecting previously unselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously unselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Selecting previously unselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-27 16:16:19--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 125.160.18.98, 125.160.18.108
Connecting to download.oracle.com (download.oracle.com)|125.160.18.98|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-06-27 16:16:19--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-27 16:16:21--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|125.160.18.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  133K=0.04s

2012-06-27 16:16:21 (133 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up libept1.4.12 (1.0.6~exp1ubuntu1) ...
Setting up aptitude (0.6.6-1ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build2) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
****@****:~$ sudo ppa-purge ppa:eugenesan/java
Updating packages lists
PPA to be removed: eugenesan java
Package revert list generated:
 oracle-java7-installer/precise

Disabling eugenesan PPA from /etc/apt/sources.list.d/eugenesan-java-precise.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Release 'precise' for 'oracle-java7-installer' was not found
Unable to find an archive "precise" for the package "oracle-java7-installer"
Unable to find an archive "precise" for the package "oracle-java7-installer"
The following partially installed packages will be configured:
  oracle-java7-installer 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-27 16:18:48--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 125.160.18.108, 125.160.18.98
Connecting to download.oracle.com (download.oracle.com)|125.160.18.108|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-06-27 16:18:48--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-27 16:18:49--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|125.160.18.108|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  138K=0.04s

2012-06-27 16:18:50 (138 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-27 16:18:50--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 125.160.18.98, 125.160.18.108
Connecting to download.oracle.com (download.oracle.com)|125.160.18.98|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) [following]
--2012-06-27 16:18:51--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-27 16:18:51--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|125.160.18.98|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100%  131K=0.04s

2012-06-27 16:18:51 (131 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
                                         
Warning:  Something went wrong, packages may not have been reverted
****@****:~$ 


Please help ...

---

### Post by c2tarun on 2012-06-27
I dont think you can install Oracle java through any ppa. Even is someone creates a ppa, launchpad is going to remove it or worse Oracle lawyers may chase him/her.
Anyway refer to this article [http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

---

### Post by czgirb on 2012-06-27
> **c2tarun said:**
> I dont think you can install Oracle java through any ppa. Even is someone creates a ppa, launchpad is going to remove it or worse Oracle lawyers may chase him/her.
Anyway refer to this article [http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

Dear **c2tarun**,
Maybe as U said, it's impossible to** install Java through any ppa**.
Cos when I tried to install **Ubuntu Restricted Extra** from **USC**, I saw the **Extra** is incld **Java**. So, Install the **Extra**. Now, if I typed **Java** in **Dash**, it showed:
[B]* Oracle Java 7 Web Start
* Oracle Java 7 Console
* Oracle Java 7 VisualVM
* Oracle Java 7 Policy tool
* Oracle Java 7 Plugin Control Panel[/B]

Is it necessary for me to erase the previous installation?
If yes, how can it be erased?
[B]Please guide me
Thank you[/B]

---

### Post by czgirb on 2012-06-27
> ***@***:~$ java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
***@***:~$

Is it the **RIGHT** java? Is it the latest version?

---

### Post by c2tarun on 2012-06-27
> **czgirb said:**
> Is it the **RIGHT** java? Is it the latest version?
 
 
No its not right. You do not have any java installed on your machine. Just follow the stackoverflow link I shared and tell what happened after that.
 
Personally I never installed java, I just get the binaries from oracle site and add it to $PATH variable, but that is wrong, I'll never suggest that way to anyone. Follow the link I shared, its proper and step by step.

---

### Post by Cheesemill on 2012-06-27
> **c2tarun said:**
> I dont think you can install Oracle java through any ppa. Even is someone creates a ppa, launchpad is going to remove it or worse Oracle lawyers may chase him/her.
Anyway refer to this article [http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

Yes you can, I use the [WebUpd8]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") team PPA all the time to install Java.

The only thing that has changed with Oracles new licensing is that you are no longer allowed to host the Java binaries in a PPA, the WebUpd8 PPA doesn't contain the binaries instead it contains a script which downloads Java from the official Oracle download site and installs it for you. There is nothing that Oracle can do to challenge this in any way (this exactly how the mscorefonts and flashplugin-installer packages work as well).

---

### Post by c2tarun on 2012-06-27
> **Cheesemill said:**
> Yes you can, I use the [WebUpd8]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") team PPA all the time to install Java.
 
The only thing that has changed with Oracles new licensing is that you are no longer allowed to host the Java binaries in a PPA, the WebUpd8 PPA doesn't contain the binaries instead it contains a script which downloads Java from the official Oracle download site and installs it for you. There is nothing that Oracle can do to challenge this in any way (this exactly how the mscorefonts and flashplugin-installer packages work as well).
 
 
Wow that's new I was not aware of that. Thanks for sharing, I'll try it today.

---

### Post by QIII on 2012-06-27
Let's get back on track.

Thanks to nothingspecial for giving the right poop while I was in bed.  

Unfortunately I did something I try hard not to do:  I gave an instruction that made perfect sense to me, but wouldn't to someone else.

@czgirb:

Let's go back to nothingspecial's post and take the next step

```
sudo apt-get update
```

---

### Post by c2tarun on 2012-06-27
> **Cheesemill said:**
> Yes you can, I use the [WebUpd8]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html") team PPA all the time to install Java.

The only thing that has changed with Oracles new licensing is that you are no longer allowed to host the Java binaries in a PPA, the WebUpd8 PPA doesn't contain the binaries instead it contains a script which downloads Java from the official Oracle download site and installs it for you. There is nothing that Oracle can do to challenge this in any way (this exactly how the mscorefonts and flashplugin-installer packages work as well).

I tried and this method works :) you can also install java this way. Its easier.

---

### Post by czgirb on 2012-06-28
> **QIII said:**
> Let's get back on track.

Thanks to nothingspecial for giving the right poop while I was in bed.  

Unfortunately I did something I try hard not to do:  I gave an instruction that made perfect sense to me, but wouldn't to someone else.

@czgirb:

Let's go back to nothingspecial's post and take the next step

```
sudo apt-get update
```

```

***@***:~$ sudo apt-get update
[sudo] password for ***: 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Hit http://packages.medibuntu.org precise InRelease                            
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://id.archive.ubuntu.com precise InRelease                             
Ign http://id.archive.ubuntu.com precise-updates InRelease                     
Ign http://id.archive.ubuntu.com precise-backports InRelease                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:2 http://id.archive.ubuntu.com precise Release.gpg [198 B]                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:4 http://id.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner i386 Packages                 
Get:5 http://id.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:6 http://id.archive.ubuntu.com precise Release [49.6 kB]                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://security.ubuntu.com precise-security/main Sources [21.1 kB]       
Get:8 http://id.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Get:9 http://security.ubuntu.com precise-security/restricted Sources [14 B]    
Get:10 http://security.ubuntu.com precise-security/universe Sources [7,120 B]  
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:12 http://security.ubuntu.com precise-security/main i386 Packages [65.9 kB]
Get:13 http://id.archive.ubuntu.com precise-backports Release [49.6 kB]        
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:14 http://id.archive.ubuntu.com precise/main Sources [934 kB]              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Get:15 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [17.4 kB]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:18 http://id.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:19 http://id.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Get:20 http://id.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:21 http://id.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:22 http://id.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:23 http://id.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:24 http://id.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://id.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://id.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://id.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://id.archive.ubuntu.com precise/universe TranslationIndex             
Get:25 http://id.archive.ubuntu.com precise-updates/main Sources [117 kB]      
Get:26 http://id.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:27 http://id.archive.ubuntu.com precise-updates/universe Sources [28.2 kB] 
Get:28 http://id.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:29 http://id.archive.ubuntu.com precise-updates/main i386 Packages [300 kB]
Get:30 http://id.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:31 http://id.archive.ubuntu.com precise-updates/universe i386 Packages [81.6 kB]
Get:32 http://id.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,049 B]
Hit http://id.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://id.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://id.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://id.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:33 http://id.archive.ubuntu.com precise-backports/main Sources [1,346 B]   
Get:34 http://id.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:35 http://id.archive.ubuntu.com precise-backports/universe Sources [6,873 B]
Get:36 http://id.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:37 http://id.archive.ubuntu.com precise-backports/main i386 Packages [929 B]
Get:38 http://id.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:39 http://id.archive.ubuntu.com precise-backports/universe i386 Packages [6,117 B]
Get:40 http://id.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://id.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://id.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://id.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://id.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://id.archive.ubuntu.com precise/main Translation-en                   
Hit http://id.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://id.archive.ubuntu.com precise/restricted Translation-en             
Hit http://id.archive.ubuntu.com precise/universe Translation-en               
Hit http://id.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://id.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://id.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://id.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://id.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://id.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://id.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://id.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 13.2 MB in 1min 47s (123 kB/s)                                         
Reading package lists... Done
***@***:~$ 

```Now! I don't know what kind of Java was installed on my computer.
In order to install a RIGHT one, I wish to fully un-installed the current version!
Would you mind to guide me how to do it?
Thank you

help ... help ... help

---

### Post by czgirb on 2012-06-29
How to remove the existing Java?
Please help ......................

---

### Post by QIII on 2012-06-29
That command more or less "reset" what your machine now knows is available for installation or upgrades.

Type 

```
java -version
```and paste the results so we can take a look.  The problem that started your whole issue with Java is that the Eugene San ppa is faulty.  Had it not been for using that ppa, this would have been extremely easy.

---

### Post by QIII on 2012-06-29
> **c2tarun said:**
> I tried and this method works :) you can also install java this way. Its easier.

That's what we are headed for.   See my first post in this thread.

The problem for czgirb is that we have to clear the problem caused by the Eugene San package so he can use that method.

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> That command more or less "reset" what your machine now knows is available for installation or upgrades.

Type 

```
java -version
```and paste the results so we can take a look.  The problem that started your whole issue with Java is that the Eugene San ppa is faulty.  Had it not been for using that ppa, this would have been extremely easy.

The **Eugene San ppa** has been deleted.
How to **"had it not been for using that ppa"**?

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> 
The problem for czgirb is that we have to clear the problem caused by the Eugene San package so he can use that method.


I wish to use that method also.
That's why I wish to delete the previous version.
Thank you.

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> That command more or less "reset" what your machine now knows is available for installation or upgrades.

Type 

```
java -version
```and paste the results so we can take a look.  The problem that started your whole issue with Java is that the Eugene San ppa is faulty.  Had it not been for using that ppa, this would have been extremely easy.

```

java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu3)
OpenJDK Server VM (build 20.0-b12, mixed mode)
```How to remove it?
Cos within webupd8.org it said:

```
If for some reason, the Java version in use is not 1.7.0, you can try to run the following command:
sudo update-java-alternatives -s java-7-oracle
```But when I copied this command, it was ended with ERROR
**Please help ...**

---

### Post by c2tarun on 2012-06-29
> **czgirb said:**
> ```

java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.1) (6b24-1.11.1-4ubuntu3)
OpenJDK Server VM (build 20.0-b12, mixed mode)
```How to remove it?
Cos within webupd8.org it said:
 
```
If for some reason, the Java version in use is not 1.7.0, you can try to run the following command:
sudo update-java-alternatives -s java-7-oracle
```But when I copied this command, it was ended with ERROR
**Please help ...**
 
 
try this:
 
```
 
sudo update-alternatives --config java

```
 
 
after this you might get an option with all the java's installed. Try to choose one and it'll be your default

---

### Post by czgirb on 2012-06-29
> **c2tarun said:**
> try this:
 
```
 
sudo update-alternatives --config java

```after this you might get an option with all the java's installed. Try to choose one and it'll be your default

```

* 0            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      auto mode
  1            /usr/bin/gij-4.6                                1046      manual mode
  2            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
  3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual
```

according to your opinion, if I wish to upgrade to Java7, which one should I choose?
Plesae guide me ...
Cos in Windows, there is only one Java
Please help ...

---

### Post by QIII on 2012-06-29
You do not need to uninstall OpenJDK.  Both Oracle Java and OpenJDK can exist together.  You choose which one to run with the alternatives selection described above.

Now that the Eugene San ppa is gone, please go to the Java wiki link and find the link I added that says "Use webupd8.org's strinkingly simple method" and follow the instructions in that link.  You must INSTALL as instructed.

If you do so, you will have Oracle Java 7 installed as your alternative and the Oracle Java web browser plug in enabled.  If you ever want to switch to OpenJDK, you don't need to uninstall Oracle Java.  You simply use the update alternatives method to select it.

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> You do not need to uninstall OpenJDK.  Both Oracle Java and OpenJDK can exist together.  You choose which one to run with the alternatives selection described above.

Now that the Eugene San ppa is gone, please go to the Java wiki link and find the link I added that says "Use webupd8.org's strinkingly simple method" and follow the instructions in that link.  You must INSTALL as instructed.

If you do so, you will have Oracle Java 7 installed as your alternative and the Oracle Java web browser plug in enabled.  If you ever want to switch to OpenJDK, you don't need to uninstall Oracle Java.  You simply use the update alternatives method to select it.

I follow the instruction, choose #3, and ended like this:

```
***@***:~$ sudo update-alternatives --config java
[sudo] password for ***: 
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      auto mode
  1            /usr/bin/gij-4.6                                1046      manual mode
  2            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
  3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode

Press enter to keep the current choice
[*], or type selection number: 3
update-alternatives: using /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java to provide /usr/bin/java (java) in manual mode.
***@***:~$ sudo add-apt-repository ppa:webupd8team/java
[sudo] password for ***: 
You are about to add the following PPA to your system:
 Oracle Java (JDK) Installer (automatically downloads and installs Oracle JDK7). There are no actual Java files in this PPA. More info: http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
 More info: https://launchpad.net/~webupd8team/+archive/java
Press [ENTER] to continue or ctrl-c to cancel adding it
 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.xCPvpeiwZs --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: key EEA14886: "Launchpad VLC" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
***@***:~$ sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://id.archive.ubuntu.com precise InRelease                             
Ign http://id.archive.ubuntu.com precise-updates InRelease                     
Ign http://id.archive.ubuntu.com precise-backports InRelease                   
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://ppa.launchpad.net precise InRelease                                 
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:3 http://id.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:5 http://id.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://id.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner i386 Packages                 
Get:7 http://ppa.launchpad.net precise Release [11.9 kB]                       
Get:8 http://id.archive.ubuntu.com precise Release [49.6 kB]                   
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:9 http://id.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:10 http://ppa.launchpad.net precise/main Sources [10.5 kB]                 
Get:11 http://security.ubuntu.com precise-security/main Sources [22.1 kB]      
Get:12 http://ppa.launchpad.net precise/main i386 Packages [16.8 kB]           
Get:13 http://id.archive.ubuntu.com precise-backports Release [49.6 kB]        
Hit http://packages.medibuntu.org precise InRelease                            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Get:14 http://id.archive.ubuntu.com precise/main Sources [934 kB]              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://archive.canonical.com precise/partner Translation-en                
Get:15 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:16 http://security.ubuntu.com precise-security/universe Sources [7,120 B]  
Get:17 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [69.4 kB]
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Get:19 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:20 http://security.ubuntu.com precise-security/universe i386 Packages [17.4 kB]
Get:21 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                      
Ign http://packages.medibuntu.org precise/non-free TranslationIndex           
Ign http://ppa.launchpad.net precise/main Translation-en_US                   
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:22 http://id.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:23 http://id.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Get:24 http://id.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:25 http://id.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:26 http://id.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:27 http://id.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:28 http://id.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://id.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://id.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://id.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://id.archive.ubuntu.com precise/universe TranslationIndex             
Get:29 http://id.archive.ubuntu.com precise-updates/main Sources [118 kB]      
Get:30 http://id.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:31 http://id.archive.ubuntu.com precise-updates/universe Sources [28.2 kB] 
Get:32 http://id.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:33 http://id.archive.ubuntu.com precise-updates/main i386 Packages [304 kB]
Get:34 http://id.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:35 http://id.archive.ubuntu.com precise-updates/universe i386 Packages [81.6 kB]
Get:36 http://id.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,049 B]
Get:37 http://id.archive.ubuntu.com precise-updates/main TranslationIndex [74 B]
Get:38 http://id.archive.ubuntu.com precise-updates/multiverse TranslationIndex [71 B]
Get:39 http://id.archive.ubuntu.com precise-updates/restricted TranslationIndex [71 B]
Get:40 http://id.archive.ubuntu.com precise-updates/universe TranslationIndex [73 B]
Get:41 http://id.archive.ubuntu.com precise-backports/main Sources [1,845 B]   
Get:42 http://id.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:43 http://id.archive.ubuntu.com precise-backports/universe Sources [8,251 B]
Get:44 http://id.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:45 http://id.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:46 http://id.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:47 http://id.archive.ubuntu.com precise-backports/universe i386 Packages [7,341 B]
Get:48 http://id.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://id.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://id.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://id.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://id.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://id.archive.ubuntu.com precise/main Translation-en                   
Hit http://id.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://id.archive.ubuntu.com precise/restricted Translation-en             
Hit http://id.archive.ubuntu.com precise/universe Translation-en               
Get:49 http://id.archive.ubuntu.com precise-updates/main Translation-en [139 kB]
Hit http://id.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://id.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://id.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://id.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://id.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://id.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://id.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 13.4 MB in 4min 58s (44.8 kB/s)                                        
Reading package lists... Done
***@***:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  visualvm ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho
  ttf-sazanami-mincho
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/15.3 kB of archives.
After this operation, 3,072 B of additional disk space will be used.
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-29 22:51:54--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 118.98.42.114, 118.98.42.88
Connecting to download.oracle.com (download.oracle.com)|118.98.42.114|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2012-06-29 22:51:55--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-06-29 22:51:58--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|118.98.42.114|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 18.8K=0.3s

2012-06-29 22:51:58 (18.8 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
***@***:~$ 
```
Any suggestion?

---

### Post by QIII on 2012-06-29
It appears that the Eugene San package is still causing problems. That is clear from the fact that you are receiveing a message about Oracle 7 Update 3 from the Eugene San PPA, when the webupd8 PPA should be giving you Oracle 7 Update 5.
 
Let me do a bit of research.

---

### Post by QIII on 2012-06-29
OK.  Let's see if we can remove the bad installer completely.
 
Navigate to the directory where the installer should live:
```
cd /var/lib/dpkg/info/
```
 
Remove the installer.  BE VERY CAREFUL!  The rm command completely removes files, forever.  When you are told to use the rm command, sometimes it is best to wait for someone else to look at the thread and make a response.
```
sudo rm oracle-java7-installer*
```
 
Just to make sure:
```
sudo apt-get remove --purge oracle-java7-installer
```
 
Let me know how that goes and we'll try again.

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> OK.  Let's see if we can remove the bad installer completely.
 
Navigate to the directory where the installer should live:
```
cd /var/lib/dpkg/info/
```Remove the installer.  BE VERY CAREFUL!  The rm command completely removes files, forever.  When you are told to use the rm command, sometimes it is best to wait for someone else to look at the thread and make a response.
```
sudo rm oracle-java7-installer*
```Just to make sure:
```
sudo apt-get remove --purge oracle-java7-installer
```Let me know how that goes and we'll try again.

Oh my God! I'm not an experienced, bro! I don't know what it is.
Would you mind to guide me regarding to your suggestion ...
Do you want me to copy-paste the following code inside terminal?
```

cd /var/lib/dpkg/info/
sudo rm oracle-java7-installer*
sudo apt-get remove --purge oracle-java7-installer

```

---

### Post by QIII on 2012-06-29
Copy and paste each one of those in the terminal and press enter -- one at a time.
 
I know this is confusing at this point because we are trying to undo a mess left by a bad PPA.  When I used to help on Windows forums we had to have people do similar things in the windows command line.

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> Copy and paste each one of those in the terminal and press enter -- one at a time.
 
I know this is confusing at this point because we are trying to undo a mess left by a bad PPA.  When I used to help on Windows forums we had to have people do similar things in the windows command line.

This is my results:
```

***@***:~$ cd /var/lib/dpkg/info/
***@***:/var/lib/dpkg/info$ sudo rm oracle-java7-installer*
[sudo] password for ******: 
rm: cannot remove `oracle-java7-installer*': No such file or directory
***@***:/var/lib/dpkg/info$ sudo apt-get remove --purge oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package oracle-java7-installer is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
***@***:/var/lib/dpkg/info$ 

```Any suggestion?

---

### Post by QIII on 2012-06-29
That little bugger.
 
Next try:
 
```
sudo apt-get autoclean
```

---

### Post by QIII on 2012-06-29
I typed too fast.  That should be autoclean!

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> That little bugger.
 
Next try:
 
```
sudo apt-get autoclean
```

Done ... after that?

---

### Post by QIII on 2012-06-29
```
sudo apt-get update
```

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> ```
sudo apt-get update
```

Done ... after that?

---

### Post by QIII on 2012-06-29
The next command will upgrade your current packages if there have been changes.  I want you to look for two things:
 
1.  If you see something that looks like "the following packages will be held back", do not type "y" when prompted.  You could get a mess.  Let me know if you see that.
 
2.  If you get a list of packages that will be updated, look carefully for the Java installer.  Again, if you see it in the list, do not type "y" when prompted.  Let me know if you see that.
 
```
sudo apt-get upgrade
```

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> The next command will upgrade your current packages if there have been changes.  I want you to look for two things:
 
1.  If you see something that looks like "the following packages will be held back", do not type "y" when prompted.  You could get a mess.  Let me know if you see that.
 
2.  If you get a list of packages that will be updated, look carefully for the Java installer.  Again, if you see it in the list, do not type "y" when prompted.  Let me know if you see that.
 
```
sudo apt-get upgrade
```

The following packages will be upgraded:
  foomatic-filters language-pack-en language-pack-gnome-en libavcodec-extra-53
  libavutil-extra-51 libgutenprint2 printer-driver-gutenprint
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,010 kB of archives.
After this operation, 2,195 kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by QIII on 2012-06-29
Looks good.
 
Go ahead.

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> Looks good.
 
Go ahead.

```
Get:1 http://id.archive.ubuntu.com/ubuntu/ precise-updates/main foomatic-filters i386 4.0.16-0ubuntu0.1 [96.9 kB]
Get:2 http://packages.medibuntu.org/ precise/non-free libavcodec-extra-53 i386 4:0.8.3ubuntu0.12.04.1+medibuntu1 [5,860 kB]
Get:3 http://id.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-en all 1:12.04+20120618 [115 kB]
Get:4 http://id.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-gnome-en all 1:12.04+20120618 [267 kB]
Get:5 http://id.archive.ubuntu.com/ubuntu/ precise-updates/main libgutenprint2 i386 5.2.8~pre1-0ubuntu2.1 [1,119 kB]
Get:6 http://id.archive.ubuntu.com/ubuntu/ precise-updates/main printer-driver-gutenprint i386 5.2.8~pre1-0ubuntu2.1 [381 kB]
Get:7 http://packages.medibuntu.org/ precise/non-free libavutil-extra-51 i386 4:0.8.3ubuntu0.12.04.1+medibuntu1 [170 kB]
Fetched 8,010 kB in 1min 6s (120 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 216616 files and directories currently installed.)
Preparing to replace foomatic-filters 4.0.15-0ubuntu1 (using .../foomatic-filters_4.0.16-0ubuntu0.1_i386.deb) ...
Unpacking replacement foomatic-filters ...
Preparing to replace language-pack-en 1:12.04+20120508 (using .../language-pack-en_1%3a12.04+20120618_all.deb) ...
Unpacking replacement language-pack-en ...
Replacing files in old package language-pack-en-base ...
Preparing to replace language-pack-gnome-en 1:12.04+20120508 (using .../language-pack-gnome-en_1%3a12.04+20120618_all.deb) ...
Unpacking replacement language-pack-gnome-en ...
Replacing files in old package language-pack-gnome-en-base ...
Preparing to replace libavcodec-extra-53 4:0.8.3ubuntu0.12.04.1 (using .../libavcodec-extra-53_4%3a0.8.3ubuntu0.12.04.1+medibuntu1_i386.deb) ...
Unpacking replacement libavcodec-extra-53 ...
Preparing to replace libavutil-extra-51 4:0.8.3ubuntu0.12.04.1 (using .../libavutil-extra-51_4%3a0.8.3ubuntu0.12.04.1+medibuntu1_i386.deb) ...
Unpacking replacement libavutil-extra-51 ...
Preparing to replace libgutenprint2 5.2.8~pre1-0ubuntu2 (using .../libgutenprint2_5.2.8~pre1-0ubuntu2.1_i386.deb) ...
Unpacking replacement libgutenprint2 ...
Preparing to replace printer-driver-gutenprint 5.2.8~pre1-0ubuntu2 (using .../printer-driver-gutenprint_5.2.8~pre1-0ubuntu2.1_i386.deb) ...
Unpacking replacement printer-driver-gutenprint ...
Processing triggers for man-db ...
Processing triggers for software-center ...
INFO:softwarecenter.db.update:no translation information in database needed
Processing triggers for cups ...
Updating PPD files for gutenprint ...
Setting up foomatic-filters (4.0.16-0ubuntu0.1) ...
Setting up language-pack-en (1:12.04+20120618) ...
Setting up language-pack-gnome-en (1:12.04+20120618) ...
Setting up libavutil-extra-51 (4:0.8.3ubuntu0.12.04.1+medibuntu1) ...
Setting up libavcodec-extra-53 (4:0.8.3ubuntu0.12.04.1+medibuntu1) ...
Setting up libgutenprint2 (5.2.8~pre1-0ubuntu2.1) ...
Setting up printer-driver-gutenprint (5.2.8~pre1-0ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by QIII on 2012-06-29
As long as it eventually took you back to your normal command prompt after the processing, that looks normal.
 
On reviewing some you your earlier posts, it does not appear that the webupd8 PPA was properly added to your sources.
 
Would you please run
 
```
sudo add-apt-repository ppa:webupd8team/java
```
 
and let me know what you get so I can look at it closely?

---

### Post by czgirb on 2012-06-29
> **QIII said:**
> As long as it eventually took you back to your normal command prompt after the processing, that looks normal.
 
On reviewing some you your earlier posts, it does not appear that the webupd8 PPA was properly added to your sources.
 
Would you please run
 
```
sudo add-apt-repository ppa:webupd8team/java
```and let me know what you get so I can look at it closely?

loks like better now!

---

### Post by QIII on 2012-06-29
What was displayed in the terminal?  We need to be sure it was properly added to your sources.list this time.
 
You can view the contents of your sources.list by 
 
```
cat /etc/sources.list
```
 
and scroll down through it to be sure the webupd8 PPA is there.

---

### Post by czgirb on 2012-06-30
> **QIII said:**
> What was displayed in the terminal?  We need to be sure it was properly added to your sources.list this time.
 
You can view the contents of your sources.list by 
 
```
cat /etc/sources.list
```and scroll down through it to be sure the webupd8 PPA is there.

SORRY! I haven't check with a above command.
Tonight I will.
But yesterday ... from the Terminal's information, it was informed that Java 7 is installed.
Regardless it was installed or not ... at first, I would like to say Thank you very very much!
After I check with the above command, I will mark this thread as SOLVED.
Thank you for your guidance QIII.

---

### Post by QIII on 2012-06-30
If you got it installed, what I would have been looking for is there so, there is no need to look.

Sorry this was such a chore.  That original PPA got you off on the wrong foot and it took a bit to figure out how to clean it up.

All's well that ends well!

---

### Post by czgirb on 2012-07-01
> **QIII said:**
> If you got it installed, what I would have been looking for is there so, there is no need to look.

Sorry this was such a chore.  That original PPA got you off on the wrong foot and it took a bit to figure out how to clean it up.

All's well that ends well!

SORRY! Yesterday, I fall asleep
So tonight I give it a try
> ***@***:~$ cat /etc/sources.list
cat: /etc/sources.list: No such file or directory
***@***:~$ 

---

### Post by czgirb on 2012-07-01
[SIZE=4]**HELP ... HELP ... HELP ...**[/SIZE]
I remember I read Java 7 was installed from Terminal, but now ...

---

### Post by scradock on 2012-07-01
> **czgirb said:**
> SORRY! Yesterday, I fall asleep
So tonight I give it a try

That should have been "cat /etc/apt/sources.list"

HTH

---

### Post by czgirb on 2012-07-01
> **scradock said:**
> 
... "cat /etc/apt/sources.list"


***@***:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise universe
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
***@***:~$

---

### Post by czgirb on 2012-07-02
Help ... Help ... Help

---

### Post by czgirb on 2012-07-02
is there anybody here?

HELP ... HELP ... HELP ...

---

### Post by czgirb on 2012-07-03
is there anybody here?

[SIZE=4]** HELP ... HELP ... HELP ...**[/SIZE]

---

### Post by c2tarun on 2012-07-03
> **czgirb said:**
> is there anybody here?

[SIZE=4]** HELP ... HELP ... HELP ...**[/SIZE]

can you please share your output of

```
java -version
```

---

### Post by QIII on 2012-07-03
> **scradock said:**
> That should have been "cat /etc/apt/sources.list"

HTH

Thanks for the typo correction.  Hasty here.

---

### Post by QIII on 2012-07-03
@czgirb --

In post #42, you said it was installed.

In post #43, I said if it was installed, you didn't need to look in your sources list.

Don't worry.  If it said it was installed, it was.  No help, help, help needed.  :)

But if you want to convince yourself, do as the poster above suggested to determine your version.

---

### Post by fballem on 2012-07-03
And if you ever have to install Oracle java again, you may find the instructions in the following link to be of some help. They use the webupd8 team repository

[https://wiki.ubuntu.com/fballem/Software/external/oracle_java](https://wiki.ubuntu.com/fballem/Software/external/oracle_java)

Hope this helps,

---

### Post by chief grand teriki on 2012-07-04
What version of ubuntu are you using? You could try install sun java jdk-6. I reckon it's better too!

---

### Post by QIII on 2012-07-04
> **fballem said:**
> And if you ever have to install Oracle java again, you may find the instructions in the following link to be of some help. They use the webupd8 team repository

[https://wiki.ubuntu.com/fballem/Software/external/oracle_java](https://wiki.ubuntu.com/fballem/Software/external/oracle_java)

Hope this helps,

That, or use the Ubuntu Community Java wiki, which explains how to use the webupd8 PPA, as I suggested in my first post and he did...;)

---

### Post by QIII on 2012-07-04
> **chief grand teriki said:**
> What version of ubuntu are you using? You could try install sun java jdk-6. I reckon it's better too!


Please see the wiki in my signature for an explanation of why that would not be a good idea in my opinion.

There is no longer a "Sun Java".  Oracle bought Sun and it is now Oracle Java.  Java 6 has significant security issues and will reach its end of life in November.

The webupd8 Java installer installs the JRE, JDK and browser plugin at the same time.  It is actually included in the ubuntu-restricted-extras package, but I don't recommend that in general because that package is not included in Ubuntu by default because of potential legal issues depending on where the user lives.

---

### Post by czgirb on 2012-07-06
> **c2tarun said:**
> can you please share your output of

```
java -version
```
> 
***@***:~$ java -version
java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b05)
Java HotSpot(TM) Server VM (build 23.1-b03, mixed mode)
***@***:~$

Thanx to QIII

---

