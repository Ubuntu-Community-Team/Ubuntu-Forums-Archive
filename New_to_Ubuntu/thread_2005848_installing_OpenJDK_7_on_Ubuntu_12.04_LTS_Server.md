---
title: "installing OpenJDK 7 on Ubuntu 12.04 LTS Server"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Immad2010 on 2012-06-18
AoA
Dear Masters
I am totally new to system administration and ubuntu server/any server. I need to install OpenJDK on my server and desktop. Both are Ubuntu 12.04 LTS.  I have the following to report. I have taken this from my desktop terminal. its the same on my server as well. i am unable to install using the Ubuntu software center as well. Please Guide. TIA.

dsuuser00@dsu-ubumtu-d:~$ sudo apt-get install openjdk-7-jre
[sudo] password for dsuuser00: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
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
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)


dsuuser00@dsu-ubumtu-d:~$ sudo apt-get update
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise InRelease
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates InRelease                                             
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports InRelease                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease 
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise Release.gpg
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates Release.gpg                                         
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports Release.gpg                                       
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                            
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise Release                                                              
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                         
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates Release                                                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                          
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports Release                                                                            
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/main Sources                                                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                              
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/restricted Sources                                                    
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/universe Sources                                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/main amd64 Packages                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                            
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/restricted amd64 Packages                                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [18.4 kB]                              
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/universe amd64 Packages                                              
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/multiverse amd64 Packages    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]                           
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [5,337 B]                          
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]                
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [57.7 kB]             
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/restricted i386 Packages              
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]                              
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [12.9 kB]                  
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/universe i386 Packages                                                                     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,155 B]        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [59.5 kB]                            
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/multiverse i386 Packages                                       
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [13.0 kB]           
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/main TranslationIndex                                          
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                                     
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/multiverse TranslationIndex                                                          
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/restricted TranslationIndex                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                             
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/universe TranslationIndex                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                               
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/main Sources                                         
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/restricted Sources             
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/universe Sources               
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/multiverse Sources             
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/main amd64 Packages            
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/restricted amd64 Packages      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                     
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/universe amd64 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                        
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/main i386 Packages             
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/main Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/main amd64 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/restricted amd64 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/universe amd64 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/main Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise/universe Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                   
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) precise-backports/universe Translation-en                                                                     
Fetched 220 kB in 6s (35.3 kB/s)                                                                                                               
Reading package lists... Done

dsuuser00@dsu-ubumtu-d:~$ sudo apt-get install openjdk-7-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
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
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)

dsuuser00@dsu-ubumtu-d:~$ sudo dpkg --configure -a
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
Errors were encountered while processing:
 samba4

dsuuser00@dsu-ubumtu-d:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
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
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
dsuuser00@dsu-ubumtu-d:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise universe
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

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

---

### Post by Curtis6767 on 2012-06-18
Maybe one of these will be helpful. Maybe. Please look them both over before doing anything as neither solution may apply to your problem.

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

GL

---

### Post by dolphin194 on 2012-06-18
Are you trying to set up a Minecraft server?

---

### Post by jtarin on 2012-06-18
> dsuuser00@dsu-ubumtu-d:~$ sudo apt-get install openjdk-7-jre
[sudo] password for dsuuser00:
Reading package lists... Done
Building dependency tree
Reading state information... Done
**_openjdk-7-jre is already the newest version._**
There is nothing to upgrade you already have the newest version.

---

### Post by Azdour on 2012-06-18
Hi,

Looking at what you have posted it looks like at some point you tried to install samba and for whatever reason it never fully installed.

Now each time you run apt-get install it tries to finish off the install but fails possibly because of corrupted files.

Maybe someone else on here can give you more instructions on how to remove packages that are not fully installed.

As a side note you can probably test if Java is installed and which version by opening a terminal and typing:

```
java -version
```

As jtarin said it looks like its already installed, but the problem I mentioned above will probably repeat each time you try and install something.

---

