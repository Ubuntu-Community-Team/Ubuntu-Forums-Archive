---
title: "Problem with MergeList"
date: 2016-02-01
forum: New to Ubuntu
---

### Post by david484 on 2016-02-01
i need help i am haveing the same problem but i keep getting a errors
  
```
david@david-MacBook:~$ sudo apt-get update && sudo apt-get upgrade -s
[sudo] password for david: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg [933 B]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 933 B in 8s (114 B/s)                                                  
Reading package lists... Error!
W:  GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
david@david-MacBook:~$
```

---

### Post by oldos2er on 2016-02-01
I've moved your post to its own thread; please don't "hijack" other people's threads, it's considered rude.

Open a terminal (Ctrl-Alt-t) and run these two commands. Let us know if there's still a problem afterwards. ```
sudo rm -vf /var/lib/apt/lists/*

sudo apt-get update
```

---

