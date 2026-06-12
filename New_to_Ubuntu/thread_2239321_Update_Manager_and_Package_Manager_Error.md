---
title: "Update Manager and Package Manager Error"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by FRKiran on 2014-08-13
I have not used my Ubuntu 12.10 for a month. After that trying to pdate my system gives the following error and details( Here I used 'sudo apt-get update' command):

```

Ign http://us.archive.ubuntu.com quantal Release.gpg                                                                                        
Hit http://linux.dropbox.com precise Release.gpg                                                                                            
Hit http://ppa.launchpad.net quantal Release.gpg
Hit http://ppa.launchpad.net quantal Release.gpg
Ign http://us.archive.ubuntu.com quantal-updates Release.gpg
Hit http://linux.dropbox.com precise Release   
Hit http://ppa.launchpad.net quantal Release.gpg                      
Ign http://us.archive.ubuntu.com quantal-backports Release.gpg
Hit http://ppa.launchpad.net quantal Release   
Hit http://linux.dropbox.com precise/main amd64 Packages                                    
Ign http://us.archive.ubuntu.com quantal-security Release.gpg        
Hit http://ppa.launchpad.net quantal Release   
Hit http://ppa.launchpad.net quantal Release                                                
Hit http://linux.dropbox.com precise/main i386 Packages                                     
Ign http://us.archive.ubuntu.com quantal Release                     
Hit http://ppa.launchpad.net quantal/main Sources
Ign http://us.archive.ubuntu.com quantal-updates Release
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Ign http://us.archive.ubuntu.com quantal-backports Release
Hit http://ppa.launchpad.net quantal/main i386 Packages
Ign http://us.archive.ubuntu.com quantal-security Release
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://ppa.launchpad.net quantal/main Sources                    
Hit http://ppa.launchpad.net quantal/main amd64 Packages             
Hit http://ppa.launchpad.net quantal/main i386 Packages
Ign http://linux.dropbox.com precise/main Translation-en_US
Ign http://linux.dropbox.com precise/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://us.archive.ubuntu.com quantal/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal/main Translation-en
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en
Err http://us.archive.ubuntu.com quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Err http://us.archive.ubuntu.com quantal-backports/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en
Err http://us.archive.ubuntu.com quantal-security/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com quantal-security/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/main Translation-en
Ign http://us.archive.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-security/universe Translation-en
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.



```
Ttrying to install something using package manager gives this results( Here I tried to install gfortran):
```
gfortran

:~$ sudo apt-get install gfortran
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gfortran


```

How should I solve this problem. I already tried to change my mirror (software center>software sources , I chosed the main server)

---

### Post by kc1di on 2014-08-13
You will have to upgrade to a newer version Ubuntu 12.10 reached end of life May 16 2014 -- and the repositories were archived and no longer updated. 
I would suggest doing a fresh install of 14.04.1 LTS   (But you could also go back to 12.04 lts which will be supported until April 2017)
good luck which ever way you decide to go.

---

### Post by FRKiran on 2014-08-13
After swiching to the main server , I also went to ''Ubuntu Software Center" - Edit Menu --- "Software Sources'' >''Other Software'' tab and tried to disable all PPA repositories, which I think is to ucheck repositories with 'http://ppa.launchpad.net' on it. I closed Ubuntu Software Center and retyped the updare command. The result was:
```

Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal Release.gpg
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal Release                                                         
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main amd64 Packages                                             
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted amd64 Packages                                       
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main i386 Packages                                              
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted i386 Packages                                        
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en_US                                          
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en                                             
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en_US                                    
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en                                       
Hit http://archive.canonical.com quantal Release.gpg                                                                                            
Hit http://archive.canonical.com quantal Release                                                                                                
Ign http://archive.ubuntu.com quantal Release.gpg                                                                       
Hit http://linux.dropbox.com precise Release.gpg                                                                        
Ign http://archive.ubuntu.com quantal-updates Release.gpg                                        
Hit http://archive.canonical.com quantal/partner Sources                                         
Hit http://linux.dropbox.com precise Release                         
Hit http://extras.ubuntu.com quantal Release.gpg                                            
Ign http://archive.ubuntu.com quantal-backports Release.gpg          
Hit http://archive.canonical.com quantal/partner amd64 Packages      
Ign http://archive.ubuntu.com quantal-security Release.gpg           
Hit http://extras.ubuntu.com quantal Release                         
Hit http://linux.dropbox.com precise/main amd64 Packages                                    
Hit http://archive.canonical.com quantal/partner i386 Packages       
Ign http://archive.ubuntu.com quantal Release                        
Hit http://extras.ubuntu.com quantal/main Sources                    
Ign http://archive.ubuntu.com quantal-updates Release                
Hit http://linux.dropbox.com precise/main i386 Packages              
Ign http://archive.ubuntu.com quantal-backports Release              
Hit http://extras.ubuntu.com quantal/main amd64 Packages             
Ign http://archive.ubuntu.com quantal-security Release               
Hit http://extras.ubuntu.com quantal/main i386 Packages              
Ign http://archive.ubuntu.com quantal/restricted Sources/DiffIndex   
Ign http://archive.ubuntu.com quantal/main Sources/DiffIndex         
Ign http://archive.ubuntu.com quantal/multiverse Sources/DiffIndex   
Ign http://archive.ubuntu.com quantal/universe Sources/DiffIndex     
Ign http://archive.ubuntu.com quantal/main amd64 Packages/DiffIndex  
Ign http://archive.ubuntu.com quantal/restricted amd64 Packages/DiffIndex                  
Ign http://archive.ubuntu.com quantal/universe amd64 Packages/DiffIndex                    
Ign http://archive.ubuntu.com quantal/multiverse amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal/main i386 Packages/DiffIndex   
Ign http://archive.ubuntu.com quantal/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal/universe i386 Packages/DiffIndex                     
Ign http://extras.ubuntu.com quantal/main Translation-en_US                                
Ign http://archive.ubuntu.com quantal/multiverse i386 Packages/DiffIndex
Ign http://linux.dropbox.com precise/main Translation-en_US          
Ign http://linux.dropbox.com precise/main Translation-en             
Ign http://extras.ubuntu.com quantal/main Translation-en             
Ign http://archive.canonical.com quantal/partner Translation-en_US   
Ign http://archive.canonical.com quantal/partner Translation-en
Ign http://archive.ubuntu.com quantal-updates/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/main Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/universe Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/main amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/restricted amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/universe amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-updates/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/main Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/universe Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/main amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/restricted amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/universe amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/multiverse amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-backports/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/restricted Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-security/main Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-security/multiverse Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-security/universe Sources/DiffIndex
Ign http://archive.ubuntu.com quantal-security/main amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/restricted amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/universe amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/multiverse amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/main i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/restricted i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/universe i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal-security/multiverse i386 Packages/DiffIndex
Ign http://archive.ubuntu.com quantal/main Translation-en_US
Ign http://archive.ubuntu.com quantal/main Translation-en
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal/multiverse Translation-en
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal/restricted Translation-en
Ign http://archive.ubuntu.com quantal/universe Translation-en_US
Ign http://archive.ubuntu.com quantal/universe Translation-en
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/main Translation-en
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en
Ign http://archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/main Translation-en
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en
Ign http://archive.ubuntu.com quantal-security/main Translation-en_US
Ign http://archive.ubuntu.com quantal-security/main Translation-en
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en
Ign http://archive.ubuntu.com quantal-security/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-security/universe Translation-en
Err http://archive.ubuntu.com quantal/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com quantal-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.149 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```
Typing :ubuntu-support-status: gave me:
```
 
Traceback (most recent call last):
  File "/usr/bin/ubuntu-support-status", line 132, in <module>
    (still_supported, support_str) = get_maintenance_status(cache, pkg.name, support_tag)
  File "/usr/bin/ubuntu-support-status", line 49, in get_maintenance_status
    raise Exception("No date tag found")
Exception: No date tag found

```
I also tried some commands which I read [here ]("https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure")and results is:
```
usr@usr:~$ cat /etc/dpkg/dpkg.cfg.d/multiarch
cat: /etc/dpkg/dpkg.cfg.d/multiarch: No such file or directory
usr@usr:~$ dpkg --print-foreign-architectures
i386
:~$ sudo grep -R proxy /etc/apt/*
usr@usr:~$sudo grep -R proxy /etc/apt/*
usr@usr:~$~$ grep proxy  /etc/environment
usr@usr:~$~$ echo $http_proxy

usr@usr:~$ grep proxy /etc/bash.bashrc
usr@usr:~$grep proxy ~/.bashrc
usr@usr~$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory
~$ sudo fuser -vvv /var/lib/dpkg/lock
usr@usr~$ sudo fuser -vvv /var/cache/apt/archives/lock
usr@usr~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu-Secure-Remix 12.10 19oct2012"



```
Is this enough or should I continue?Because the other commands contains some remove and move commands.

---

### Post by FRKiran on 2014-08-13
> **kc1di said:**
> 
I would suggest doing a fresh install of 14.04.1 LTS   (But you could also go back to 12.04 lts which will be supported until April 2017)
good luck which ever way you decide to go.

what should I do for going back to 12.04? Do I nead to do a fresh install?

---

### Post by kc1di on 2014-08-13
I'm afraid you will. Back up everything first. :)

---

### Post by kansasnoob on 2014-08-13
> **FRKiran said:**
> what should I do for going back to 12.04? Do I nead to do a fresh install?

Why not just try Trusty (14.04.1) first? It's supported longer:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Also the current Precise is 12.04.5 which uses the Trusty HWE anyway:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Kernel.2BAC8-Support.A12.04.x_Ubuntu_Kernel_Support)

So if 12.04.5 runs on your hardware so should 14.04.1 which provides 2 more years of support.

BTW, just in case the Trusty kernel or X-stack does not play well with your hardware you could use the archived 12.04.1 installation media which still has the 3.2 series kernel and is supported until April 2017:

[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

But that also shows the 12.04.2 and 12.04.3 media which you don't want to use to avoid HWE EOL:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

---

### Post by FRKiran on 2014-08-13
> **kansasnoob said:**
> Why not just try Trusty (14.04.1) first? It's supported longer:



I also want to try this version. regarding to your explaitions it seems a better chice for me.

> **kc1di said:**
> Back up everything first

There are some programs which I need to keep their information. In fact I need them to be exacly the same as they are now, but not all of them. For example I installed some programs manually and I happily will not reinstall or restore them after changing my system. Now waht about the ones I need to remain the same. How should I do it?

---

### Post by sotiris2 on 2014-08-13
I am thinking you are referring more to their configuration options (for example accounts and passwords for some internet program, browser histories and favourites) rather than minding to having to reinstall them and wait a bit for a download?. If so you need to save your /home folder. 

First lets check if it is in a different partition which will save us from a lot of work. Open a terminal and type
```
mount
```
Copy and paste the output in a reply here and I will tell you how you will proceed.

---

### Post by FRKiran on 2014-08-13
In fact I am refering to my Bittorent client-I was not sure if I was allowed to use the name here.

---

### Post by FRKiran on 2014-08-13
> **sotiris2 said:**
> I am thinking you are referring more to their configuration options (for example accounts and passwords for some internet program, browser histories and favourites) rather than minding to having to reinstall them and wait a bit for a download?. If so you need to save your /home folder. 

First lets check if it is in a different partition which will save us from a lot of work. Open a terminal and type
```
mount
```
Copy and paste the output in a reply here and I will tell you how you will proceed.

This is actually a good idea which performing it will teach me things I have not still experienced. The result of the command was:
```
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
/dev/sda3 on /boot type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/usr/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=usr)
/dev/sdc1 on /media/usr/usr type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
/dev/sdb1 on /media/usr/usr number type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/usr/C, pc-usr type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
```

---

### Post by sotiris2 on 2014-08-13
I wrote all this and then I saw you have a boot partition sda3 which may be unnecessary so if you'd like before you check the rest can you post me the output of 
```
sudo parted -l
```?


Ok since it isn't mounted it means it' not in a different partition and we will have to save it. First let's find out how big your home folder is. Open your home folder and go up a level (ALT+UP arrow). You should see your folder as an icon (of a home ) with your name. Right click on it and select properties. Wait for it to finish counting and check its size.

 Now you have the following options.
Copy everything to an external media (hard drive) and after reinstalling ubuntu copying them back.
Or do some partitioning and saving them to a new partition on the same drive. That requires a bit more effort on your side and also your home folder to be smaller than the free space on the disk (since we will COPY it not move it.) In both cases I would copy them back to a distinct /home partition so that you can easily reinstall the os without losing your configurations and files in the future. 


Note that both procedures take time. If you decide that you don't mind not keeping some large files because you also have them elsewhere you could delete them now and spare yourself some time. 

COPY TO SAME DRIVE.
If you want to not use an external disk then you will have to [resize]("https://help.ubuntu.com/community/HowtoPartition/ResizingPartition") your partition. To be honest to shrink it to make free space on the disk. We can't do so from your installed system (can't shrink itself) so we will do so from a live cd. Since you want to installl 14.04 go ahead and make an installation media (either [dvd]("https://help.ubuntu.com/community/BurningIsoHowto") or [url=https://help.ubuntu.com/community/Installation/FromUSBStick]usb) and boot it up. But instead of selecting "Install Ubuntu Now" , select Try Ubuntu, and you will have a ubuntu system without installing. Then you can run Gparted (it's included on the live cd/usb) and follow the guide above on resizing.I 'm not sure how much space you have but the main / partition of ubuntu doesn't need more than say 30-40gb (and that's probably overkill) so you can push it that low. After its done (and you will NOT interrupt it) you can make a new partition on the unallocated space. Choose ext4 filesystem. Remember its size and name sdax where x will be a number, and maybe give it a label. 

Then we 'll copy your home folder to the new partition. There is a guide [here]("https://help.ubuntu.com/community/Partitioning/Home/Moving") but it requires you to reboot to your old system. You also shouldn't bother with sections related to fstab  or moving home to old since you will be reinstalling.

If you don't want to reboot, follow on.
Since we are on the live media opening home as you used to will show nothing. But at the bottom of the launcher you 'll have some hard-disk icons. One of them will be your installed system which will contain a folder name home and one of them will be empty. Do not copy the /home folder to the empty partition. Rather enter the home folder and copy the folder name after you. Paste it to the new partitions. After it's done check it's size and importantly check permissions tab. It must be the username you had (and will have) and not something else. 

INSTALL
Now you can reinstall ubuntu. It is important however that you do the following things:
Select manual/custom partitioning and not install ubuntu alon or install ubuntu alongside. MANUAL. 
You will get a list of paritions. Find the one you created and click on change. Select use as ext4 filesystem and  mount on /home. Doublecheck format is NOT selected. 
Select your old partition and set it to be mounted on /. For this partition select Format. Now continue with install. It's important that you pick the exact same username and password as you had. Otherwise you may face problems.

Now after you install you won't have your programs, say your bitorrent client. But after you install them, they won't be like brand new but already configured as you left them. Your bittorrent client will be configured as it was and it will even have your torrents as you left em.

EDIT: If you want to use an external drive just copy your home folder to your external drive.Unplug that drive. Then install ubuntu with manual partitioning and delete every partition. Then add a 30-40GB ext4 partition to be used as / , a couple gb swap partition (equal to your ram if it's a laptop and you want hibernate) , and the rest as an ext4 partition to be used as home. Install normally and boot to your new system. Copy everything (press ctrl +H to show hidden files, they start with a . and are what contains your configurations) to your new home folder. DO NOT REBOOT before running
```
sudo chown -R user:user ~/user
```
where user is your username. Do not run it with user, you will need another reinstall.

---

### Post by FRKiran on 2014-08-13
> **sotiris2 said:**
> I wrote all this and then I saw you have a boot partition sda3 which may be unnecessary so if you'd like before you check the rest can you post me the output of 
```
sudo parted -l
```?


The output is:
```
Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   269GB  268GB   primary   ntfs
 3      269GB   269GB  367MB   primary   ext4
 4      269GB   750GB  481GB   extended
 5      269GB   484GB  215GB   logical   ntfs
 6      484GB   645GB  161GB   logical   ntfs
 7      645GB   742GB  96.7GB  logical   ext4
 8      742GB   750GB  8513MB  logical   linux-swap(v1)


Model: WD My Passport 07A8 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs


Model: Multiple Card Reader (scsi)
Disk /dev/sdc: 4073MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4073MB  4073MB  primary  fat32        boot


```
Which I do not know the meaning.

And my home have the volum of 16.8 GB now.

---

### Post by sotiris2 on 2014-08-13
Do you have an external hard drive or usb stick of that size? Or are you willing to ditch some files? Do you also have a windows installation?

---

### Post by FRKiran on 2014-08-13
Yes I have an external usb device with enough space to save my home folder to. I am willing to get rid of some files. For examplie there is a file named '.texlive2012' highlighted with blue which seems to be connected to the 'texlive' I installed manually. I do not intend to reinstall that after chaging my system. This is the only thing in my home that I do not like. Any way is there a way I can understand which file was added after installing ubuntu and because of installing new programs? Something that helps me chose files I should keep, files I can keep, and files I can happily delet because I will reinstall their program anymore.
I also have a Windows .

---

### Post by sotiris2 on 2014-08-13
Other by name no not really. But you can omit .cache.
Now if you have backed up your home folder you can go on ahead and reinstall ubuntu. I would reccomend that you make a distinct /home partition this time though. To do so select manual partitioning/try something else in the installer. 

You will get a list of partitions. Do not touch anything that is of type ntfs (sda1,2,5,6). 
Delete partition sda7 of type ext4. In its place create two different partitions both ext4 with sizes 30gb for one and the rest for the other. Select the 25gb partition and have it be mounted on /. Have the other to be mounted on /home. Delete sda3 in my opinion since you don't need a /boot partition and can only cause you problems if it fill up (later you can extend the windows partition to cover the extra 300mb but only do so in windows operating system, not from ubuntu or install disk). Continue install as normal, pick your username (you can pick new).

 Reboot to your new system. and copy back your home folder's contents to your new home folder. Make sure you include hidden files (starting with .) After it is done DO NOT REBOOT/LOGOUT before you run this. 
```
sudo chown -R user:user /home/user
```
where user is your username. it will ask for your password, type it and press enter even though it won't show anything on screen like **** or ### . Check via right click properties that you are the owner of all files and folders before you reboot/shutdown/logout. Then reinstall any programs you had and when you run them it should be like you didn't even reinstall.

---

### Post by kc1di on 2014-08-13
I would be more selective about copying back your entire home folder.  there are some hidden config files you do not want on the new install They will need to be replaced by newer ones on the new install.  and if you copy them they may conflict of overwrite newer ones so be careful with that. 

Good Luck

---

### Post by FRKiran on 2014-08-14
> **kc1di said:**
> I would be more selective about copying back your entire home folder.  there are some hidden config files you do not want on the new install They will need to be replaced by newer ones on the new install.  and if you copy them they may conflict of overwrite newer ones so be careful with that. 

Good Luck

1) What config files exactlty? How should I chose the files I need to keep and the ones I need to throw away?
2) also,                         When I tried to copy my home, opening nautilus window through 'gksudo nautilus' command, there was some files could not be copied.
the massage was: some error occurred while copying ....' and the name instead of '....' were :"ifac_socket" and "command_socket".
Is this normal. Would it be OK if I continue without this files.( I just skipped these files)

3) In fact from the piles of programs I have now, I am only intrested in my torrent files and torrent client. Please lokk at this foder and it's contents:
```
usr@usr:~$ ls .config/transmission/
blocklists  dht.dat  resume  settings.json  stats.json  torrents

```

Is it OK if I keep only this file from my home and copy it back after installing 14.04. I used [this page]("https://trac.transmissionbt.com/wiki/ConfigFiles") to locate tansmission files.
Thank you

---

### Post by kc1di on 2014-08-14
Hi again,

I would only restore my personal files.  bookmarks , Documents , pictures stuff like that.  most of the config files are hidden any way and I would not restore most of them because it may create conflicts with newer versions of the same file if you restore them you would be in effect overwriting the newer file. 
The transmission files may be ok, but I've never tried it so not sure about that one.  
I for instance use Chrome Browser and it has the ability to sync all my bookmarks and other chrome settings because it has cloud storage.  I believe FireFox has something similar. I also use Dropbox or other cloud storage and export important e-mails documents there - they are easily restored when new install is complete.  Just my 2 cents worth :)

---

### Post by sotiris2 on 2014-08-14
Yes you can keep only these files. If you want to keep more configuration files but not have potential problems, you could chose try ubuntu , and use gparted to create the partitions before installing and copying your home folder to the one that you will select to be mounted as home. Note that the partition should have a folder with your username and not a folder named home or all your subfolders (such as documents and .transmision). 

 Then you will install the os and pick it to use this partition as home and you will NOT select to format it. If some config files must be changed for ubuntu to work they will be. But not essential program configurations (such as transmission ,firefox etc) will be left alone. I've personally upgraded via reinstalling this way from 10.10=>14.04 skipping maybe 4 versions at most with no issues. kc1di is right though that the way i described in the previous post could result is some problems. While its a bit of a hassle now, it will make system reinstallations (or upgrades via installing a new version which seems to work much better) much more easier in the future.

EDIT: Whatever you do make sure you have correct owner for the files you put back.

---

### Post by kc1di on 2014-08-14
> **sotiris2 said:**
> Yes you can keep only these files. If you want to keep more configuration files but not have potential problems, you could chose try ubuntu , and use gparted to create the partitions before installing and copying your home folder to the one that you will select to be mounted as home. Note that the partition should have a folder with your username and not a folder named home or all your subfolders (such as documents and .transmision). 

 Then you will install the os and pick it to use this partition as home and you will NOT select to format it. If some config files must be changed for ubuntu to work they will be. But not essential program configurations (such as transmission ,firefox etc) will be left alone. I've personally upgraded via reinstalling this way from 10.10=>14.04 skipping maybe 4 versions at most with no issues. kc1di is right though that the way i described in the previous post could result is some problems. While its a bit of a hassle now, it will make system reinstallations (or upgrades via installing a new version which seems to work much better) much more easier in the future.

EDIT: Whatever you do make sure you have correct owner for the files you put back.

+1 :)

---

