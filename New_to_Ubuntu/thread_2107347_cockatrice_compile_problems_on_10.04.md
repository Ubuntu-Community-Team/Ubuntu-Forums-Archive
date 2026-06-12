---
title: "cockatrice compile problems on 10.04"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by joshcanfield on 2013-01-21
hey I am trying to install cockatrice on 10.04 but am running in to this problem

canfield@canfield-laptop:~$ cd Cockatrice
canfield@canfield-laptop:~/Cockatrice$ cd build
canfield@canfield-laptop:~/Cockatrice/build$ cmake ..
-- Could NOT find PROTOBUF  (missing:  PROTOBUF_LIBRARY PROTOBUF_INCLUDE_DIR)
-- Could NOT find PROTOBUF  (missing:  PROTOBUF_LIBRARY PROTOBUF_INCLUDE_DIR)
CMake Error at cockatrice/FindQtMobility.cmake:52 (message):
  Couldn't find any version of QtMobility.
Call Stack (most recent call first):
  cockatrice/CMakeLists.txt:197 (FIND_PACKAGE)


CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
PROTOBUF_INCLUDE_DIR (ADVANCED)
   used as include directory in directory /home/canfield/Cockatrice/common

-- Configuring incomplete, errors occurred!
canfield@canfield-laptop:~/Cockatrice/build$ 



I downloaded the current stable version of cockatrice from their website.

---

### Post by oldos2er on 2013-01-21
Try ```
sudo apt-get install libprotobuf-dev qtmobility-dev
```

---

### Post by joshcanfield on 2013-01-21
I got this in response

canfield@canfield-laptop:~$ sudo apt-get install libprotobuf-dev qtmobility-dev
[sudo] password for canfield: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qtmobility-dev
canfield@canfield-laptop:~$


I also got this for the protobuf 

canfield@canfield-laptop:~$ sudo apt-get install libprotobuf-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  libprotobuf-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 116kB of archives.
After this operation, 762kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main libprotobuf-dev 2.2.0a-0.1ubuntu1 [116kB]
Fetched 116kB in 0s (250kB/s)         
Selecting previously deselected package libprotobuf-dev.
(Reading database ... 167274 files and directories currently installed.)
Unpacking libprotobuf-dev (from .../libprotobuf-dev_2.2.0a-0.1ubuntu1_i386.deb) ...
Setting up libprotobuf-dev (2.2.0a-0.1ubuntu1) ...
canfield@canfield-laptop:~$


after installing protobuf I now get this error when trying to compile cockatrice

canfield@canfield-laptop:~$ cd Cockatrice
canfield@canfield-laptop:~/Cockatrice$ cd build
canfield@canfield-laptop:~/Cockatrice/build$ cmake ..
-- Found PROTOBUF: /usr/lib/libprotobuf.so
CMake Error at cockatrice/FindQtMobility.cmake:52 (message):
  Couldn't find any version of QtMobility.
Call Stack (most recent call first):
  cockatrice/CMakeLists.txt:197 (FIND_PACKAGE)


-- Configuring incomplete, errors occurred!
canfield@canfield-laptop:~/Cockatrice/build$

---

### Post by oldos2er on 2013-01-22
Like the instructions say, you need the QtMobility development package. Have you update your sources recently? ```
sudo apt-get update && sudo apt-get install qtmobility-dev
```

---

### Post by joshcanfield on 2013-01-23
ok so here is what i got back from that code

canfield@canfield-laptop:~$ sudo apt-get update && sudo apt-get install qtmobility-dev
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg                    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                       
Ign [http://ppa.launchpad.net/gma500/ppa/ubuntu/](http://ppa.launchpad.net/gma500/ppa/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qtmobility-dev
canfield@canfield-laptop:~$ 


I have a folder named qtmobility in my home folder that i downloaded, but it has a symbol of a lock on it. could this be significant?

also thanks for all the help so far.

---

### Post by mikewhatever on 2013-01-23
Qtmobility-dev is not avalable for 10.04. 
[http://packages.ubuntu.com/quantal/qtmobility-dev](http://packages.ubuntu.com/quantal/qtmobility-dev)

Upgrade to 12.04 if you want to install it.

---

### Post by joshcanfield on 2013-01-24
I figured that might be what i would have to do, thanks for all the help.

---

