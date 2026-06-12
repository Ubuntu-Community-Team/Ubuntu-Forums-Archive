---
title: "Software Update Problem"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by 7Starphy on 2013-01-15
Ok ,I seem to be getting some problem or another every two days :D ,anyways I tried to get software updates ,but then came this "require installation of untrusted packages " . I know this is a very common error and did a lot of googling ,but I couldnt find any solution . In cmd when I type ```
sudo apt-get update 
``` . I get this 
```


Ign http://archive.canonical.com precise InRelease                                                                                              
Ign http://security.ubuntu.com precise-security InRelease                                                                                       
Ign http://dl.google.com stable InRelease                                                                                                      
Ign http://in.archive.ubuntu.com precise InRelease                                                                                              
Ign http://extras.ubuntu.com precise InRelease                                                                                                  
Err http://extras.ubuntu.com precise Release.gpg                                                                                                
  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out)
Ign http://extras.ubuntu.com precise Release                                                                                                    
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                      
Err http://extras.ubuntu.com precise/main Sources                                                                                               
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main amd64 Packages                                                                                        
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main i386 Packages                                                                                         
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main Translation-en_IN                                                                                     
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main Translation-en                                                                                        
  Unable to connect to extras.ubuntu.com:http:
Err http://archive.canonical.com precise Release.gpg                           t
  Could not connect to archive.canonical.com:80 (91.189.92.150). - connect (110: Connection timed out) [IP: 91.189.92.150 80]
Err http://security.ubuntu.com precise-security Release.gpg                    
  Could not connect to security.ubuntu.com:80 (91.189.92.190). - connect (110: Connection timed out) [IP: 91.189.92.190 80]
Ign http://archive.canonical.com precise Release                               
Ign http://security.ubuntu.com precise-security Release                        
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://security.ubuntu.com precise-security/main TranslationIndex          
Ign http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Ign http://security.ubuntu.com precise-security/restricted TranslationIndex    
Ign http://security.ubuntu.com precise-security/universe TranslationIndex      
Err http://archive.canonical.com precise/partner Sources  
Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]
Err http://archive.canonical.com precise/partner amd64 Packages                
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]
Err http://archive.canonical.com precise/partner i386 Packages                 
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]
Err http://archive.canonical.com precise/partner Translation-en_IN             
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]
Err http://archive.canonical.com precise/partner Translation-en                
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.150 80]
Err http://security.ubuntu.com precise-security/main Sources                   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/restricted Sources             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/universe Sources               
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/multiverse Sources             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/main amd64 Packages            
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/restricted amd64 Packages      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/universe amd64 Packages        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/multiverse amd64 Packages      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/main i386 Packages             
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/restricted i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/universe i386 Packages         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/multiverse i386 Packages       
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/main Translation-en_IN         
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/main Translation-en            
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/multiverse Translation-en_IN   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/multiverse Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/restricted Translation-en_IN   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/restricted Translation-en      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/universe Translation-en_IN     
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/universe Translation-en        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Err http://in.archive.ubuntu.com precise Release.gpg                           
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates Release.gpg
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports Release.gpg
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Ign http://in.archive.ubuntu.com precise Release 
Ign http://in.archive.ubuntu.com precise-updates Release
Ign http://in.archive.ubuntu.com precise-backports Release
Ign http://in.archive.ubuntu.com precise/main TranslationIndex
Ign http://in.archive.ubuntu.com precise/multiverse TranslationIndex
Ign http://in.archive.ubuntu.com precise/restricted TranslationIndex
Ign http://in.archive.ubuntu.com precise/universe TranslationIndex
Ign http://in.archive.ubuntu.com precise-updates/main TranslationIndex
Ign http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Ign http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex
Ign http://in.archive.ubuntu.com precise-updates/universe TranslationIndex
Ign http://in.archive.ubuntu.com precise-backports/main TranslationIndex
Ign http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Ign http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex
Ign http://in.archive.ubuntu.com precise-backports/universe TranslationIndex
Err http://in.archive.ubuntu.com precise/main Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/universe Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/multiverse Sources                    
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/main amd64 Packages                   
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/restricted amd64 Packages             
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/universe amd64 Packages               
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/multiverse amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/universe Sources              
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/multiverse Sources            
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/main amd64 Packages           
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages     
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/universe amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/main Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/universe Sources            
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/multiverse Sources          
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/main amd64 Packages         
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/restricted amd64 Packages   
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/universe amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/multiverse amd64 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/restricted i386 Packages    
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/universe i386 Packages      
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages    
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/main Translation-en_IN                
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/main Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/multiverse Translation-en_IN          
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/multiverse Translation-en             
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/restricted Translation-en_IN          
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/restricted Translation-en             
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise/universe Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/main Translation-en           
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/multiverse Translation-en_IN  
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/multiverse Translation-en     
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/restricted Translation-en_IN  
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-updates/universe Translation-en       
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/main Translation-en_IN      
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/main Translation-en         
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/multiverse Translation-en   
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.92.156 80]
Err http://in.archive.ubuntu.com precise-backports/universe Translation-en

```

---

### Post by papibe on 2013-01-15
Hi 7Starphy.

Sometimes repositories are down for maintenance. If it is urgent, wait a couple of hours and then try again.

There's an alternative: set the repositories download server that is closer (in terms of pings). Take a look at this [tutorial]("https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server"), specially the sub section called 'Best Server'.

Hope it helps. Let us know how it goes.
Regards.

Note: to get to the 'Software Sources' in 12.04 open the Software Center, and select Edit->Software Sources.

---

### Post by MrsUser on 2013-01-15
Same here. Seems the servers are down. Fresh install of Ubuntu 12.10 today. Added the usual software. Sources list seems fine:

```

# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu quantal universe
deb http://archive.ubuntu.com/ubuntu quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu quantal multiverse
deb http://archive.ubuntu.com/ubuntu quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu quantal-security main restricted
deb http://archive.ubuntu.com/ubuntu quantal-security universe
deb http://archive.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu quantal partner
deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb http://www.bunkus.org/ubuntu/quantal/ ./
deb-src http://www.bunkus.org/ubuntu/quantal/ ./
deb-src http://extras.ubuntu.com/ubuntu quantal main
deb http://download.virtualbox.org/virtualbox/debian quantal contrib
``````

Ign http://ppa.launchpad.net quantal InRelease
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://archive.canonical.com quantal InRelease                             
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://extras.ubuntu.com quantal Release.gpg                               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://archive.canonical.com quantal Release                               
Hit http://download.virtualbox.org quantal InRelease                           
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal Release                                   
Ign http://linux.dropbox.com precise InRelease                                 
Hit http://archive.canonical.com quantal/partner Sources                       
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://archive.ubuntu.com quantal InRelease                                
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Hit http://download.virtualbox.org quantal/contrib amd64 Packages              
Ign http://archive.ubuntu.com quantal-updates InRelease                        
Get:1 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://download.virtualbox.org quantal/contrib i386 Packages               
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://archive.ubuntu.com quantal-backports InRelease                      
Hit http://ppa.launchpad.net quantal Release.gpg                               
Ign http://archive.ubuntu.com quantal-security InRelease                       
Hit http://archive.ubuntu.com quantal Release.gpg                              
Get:2 http://archive.ubuntu.com quantal-updates Release.gpg [933 B]            
Hit http://archive.ubuntu.com quantal-backports Release.gpg                    
Ign http://www.bunkus.org ./ InRelease                                         
Hit http://ppa.launchpad.net quantal Release.gpg                               
Get:3 http://archive.ubuntu.com quantal-security Release.gpg [933 B]           
Hit http://www.bunkus.org ./ Release.gpg                                       
Get:4 http://linux.dropbox.com precise Release [2.603 B]                       
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release.gpg                               
Get:5 http://linux.dropbox.com precise/main amd64 Packages [1.029 B]           
Hit http://www.bunkus.org ./ Release                                           
Hit http://www.bunkus.org ./ Sources                                           
Hit http://archive.ubuntu.com quantal Release                                  
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://www.bunkus.org ./ Packages                                          
Get:6 http://archive.ubuntu.com quantal-updates Release [49,6 kB]              
Hit http://ppa.launchpad.net quantal Release                                   
Get:7 http://linux.dropbox.com precise/main i386 Packages [1.029 B]            
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://archive.canonical.com quantal/partner Translation-en                
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://www.bunkus.org ./ Translation-en_US                                 
Hit http://ppa.launchpad.net quantal Release                                   
Ign http://www.bunkus.org ./ Translation-en                                    
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://archive.ubuntu.com quantal-backports Release                        
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Get:8 http://archive.ubuntu.com quantal-security Release [49,6 kB]             
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://archive.ubuntu.com quantal/main amd64 Packages                      
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages                
Hit http://archive.ubuntu.com quantal/universe amd64 Packages         
Hit http://ppa.launchpad.net quantal/main Sources                     
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages       
Hit http://ppa.launchpad.net quantal/main amd64 Packages              
Hit http://archive.ubuntu.com quantal/main i386 Packages              
Hit http://ppa.launchpad.net quantal/main i386 Packages               
Hit http://archive.ubuntu.com quantal/restricted i386 Packages        
Hit http://ppa.launchpad.net quantal/main Sources                     
Hit http://archive.ubuntu.com quantal/universe i386 Packages          
Hit http://ppa.launchpad.net quantal/main amd64 Packages              
Hit http://archive.ubuntu.com quantal/multiverse i386 Packages        
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://archive.ubuntu.com quantal/main Translation-en                      
Hit http://ppa.launchpad.net quantal/main Sources                     
Hit http://archive.ubuntu.com quantal/multiverse Translation-en       
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://archive.ubuntu.com quantal/restricted Translation-en       
Ign http://download.virtualbox.org quantal/contrib Translation-en_US  
Hit http://archive.ubuntu.com quantal/universe Translation-en         
Get:9 http://archive.ubuntu.com quantal-updates/main amd64 Packages [169 kB]   
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Hit http://ppa.launchpad.net quantal/main Sources                              
Ign http://download.virtualbox.org quantal/contrib Translation-en             
Hit http://ppa.launchpad.net quantal/main amd64 Packages                      
Hit http://ppa.launchpad.net quantal/main i386 Packages                       
Ign http://linux.dropbox.com precise/main Translation-en 
Hit http://ppa.launchpad.net quantal/main Sources        
Hit http://ppa.launchpad.net quantal/main amd64 Packages 
Hit http://ppa.launchpad.net quantal/main i386 Packages  
Hit http://ppa.launchpad.net quantal/main Sources        
Hit http://ppa.launchpad.net quantal/main amd64 Packages 
Hit http://ppa.launchpad.net quantal/main i386 Packages 
Get:10 http://archive.ubuntu.com quantal-updates/restricted amd64 Packages [1.970 B]
Get:11 http://archive.ubuntu.com quantal-updates/universe amd64 Packages [144 kB]
Hit http://ppa.launchpad.net quantal/main Sources        
Hit http://ppa.launchpad.net quantal/main amd64 Packages 
Hit http://ppa.launchpad.net quantal/main i386 Packages
Get:12 http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages [7.957 B]
Get:13 http://archive.ubuntu.com quantal-updates/main i386 Packages [169 kB]  
Get:14 http://archive.ubuntu.com quantal-updates/restricted i386 Packages [1.979 B]
Get:15 http://archive.ubuntu.com quantal-updates/universe i386 Packages [145 kB]
Get:16 http://archive.ubuntu.com quantal-updates/multiverse i386 Packages [8.112 B]
Hit http://archive.ubuntu.com quantal-updates/main Translation-en              
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en        
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en          
Hit http://archive.ubuntu.com quantal-backports/main amd64 Packages            
Hit http://archive.ubuntu.com quantal-backports/restricted amd64 Packages      
Hit http://archive.ubuntu.com quantal-backports/universe amd64 Packages        
Hit http://archive.ubuntu.com quantal-backports/multiverse amd64 Packages      
Hit http://archive.ubuntu.com quantal-backports/main i386 Packages             
Hit http://archive.ubuntu.com quantal-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com quantal-backports/universe i386 Packages         
Hit http://archive.ubuntu.com quantal-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com quantal-backports/main Translation-en            
Hit http://archive.ubuntu.com quantal-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com quantal-backports/restricted Translation-en      
Hit http://archive.ubuntu.com quantal-backports/universe Translation-en        
Get:17 http://archive.ubuntu.com quantal-security/main amd64 Packages [65,9 kB]
Get:18 http://archive.ubuntu.com quantal-security/restricted amd64 Packages [14 B]
Get:19 http://archive.ubuntu.com quantal-security/universe amd64 Packages [27,7 kB]
Get:20 http://archive.ubuntu.com quantal-security/multiverse amd64 Packages [1.144 B]
Get:21 http://archive.ubuntu.com quantal-security/main i386 Packages [65,8 kB] 
Get:22 http://archive.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Get:23 http://archive.ubuntu.com quantal-security/universe i386 Packages [28,3 kB]
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Get:24 http://archive.ubuntu.com quantal-security/multiverse i386 Packages [1.385 B]
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://archive.ubuntu.com quantal-security/main Translation-en             
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://archive.ubuntu.com quantal-security/multiverse Translation-en       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://archive.ubuntu.com quantal-security/restricted Translation-en       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Hit http://archive.ubuntu.com quantal-security/universe Translation-en         
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Ign http://archive.ubuntu.com quantal/main Translation-en_US                   
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US             
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US             
Ign http://archive.ubuntu.com quantal/universe Translation-en_US               
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US           
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US       
Ign http://archive.ubuntu.com quantal-backports/main Translation-en_US         
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en_US   
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en_US   
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en_US     
Ign http://archive.ubuntu.com quantal-security/main Translation-en_US          
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en_US    
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en_US    
Ign http://archive.ubuntu.com quantal-security/universe Translation-en_US      
Fetched 943 kB in 11s (78,6 kB/s)                                              
Reading package lists... Done

```

---

### Post by 7Starphy on 2013-01-16
Sorry ,but I dont think there is any problem with server or something ,it has been like this for two days. I think there is something wrong with the network configuration or something similar . Can you please help with this issue ?
```


Ign http://extras.ubuntu.com precise InRelease                                                                                                  
Err http://extras.ubuntu.com precise Release.gpg                                                                                                
  Unable to connect to extras.ubuntu.com:http:
Ign http://extras.ubuntu.com precise Release                                                                                                    
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                      
Err http://extras.ubuntu.com precise/main Sources                                                                                               
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main amd64 Packages                                                                                        
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main i386 Packages                                                                                         
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main Translation-en_IN                                                                                     
  Unable to connect to extras.ubuntu.com:http:
Err http://extras.ubuntu.com precise/main Translation-en                                                                                        
  Unable to connect to extras.ubuntu.com:http:
Ign http://security.ubuntu.com precise-security InRelease                                                                                       
Ign http://archive.canonical.com precise InRelease                                                                                              
Err http://archive.canonical.com precise Release.gpg                                                                                            
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err http://security.ubuntu.com precise-security Release.gpg                                                                                     
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Ign http://archive.canonical.com precise Release                                                                                                
Ign http://security.ubuntu.com precise-security Release                                                
Ign http://archive.canonical.com precise/partner TranslationIndex                                      
Ign http://security.ubuntu.com precise-security/main TranslationIndex                                  
Ign http://security.ubuntu.com precise-security/multiverse TranslationIndex                            
Ign http://security.ubuntu.com precise-security/restricted TranslationIndex                            
Ign http://security.ubuntu.com precise-security/universe TranslationIndex                              
Err http://archive.canonical.com precise/partner Sources                                               
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err http://archive.canonical.com precise/partner amd64 Packages                                        
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err http://archive.canonical.com precise/partner i386 Packages                                         
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err http://archive.canonical.com precise/partner Translation-en_IN                                                                              
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err http://archive.canonical.com precise/partner Translation-en                                                                                 
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Err http://security.ubuntu.com precise-security/main Sources                                                                                    
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/restricted Sources                                                                              
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]
Err http://security.ubuntu.com precise-security/universe Sources                                                                                
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.190 80]

```

---

### Post by Demonarc on 2013-01-16
I had a similar problem. if you look at your /etc/resolv.conf make sure you have a nameserver 192.168.1.1.    if your resolv.conf is being over written you have to sudo nano /etc/resolv.conf.d/head and put nameserver 192.168.1.1 .. replace 192.168.1.1 with dns server. it will reset every time you restart unless you do that. :)

---

### Post by 7Starphy on 2013-01-16
Sorry ,I dont understand ,can you explain a bit more detailed . I remember meddling with resolv.conf file long time ago ,but I dont know what I did.I gave my nameserver as 10.1.1.61 (which is my DNS server )because I was manually assigning my IP . Now I shifted to DHCP and I am getting some problems with the update manager

---

### Post by papibe on 2013-01-16
If you are able to browse the Internet normally, **do not** change the file /etc/resolv.conf

Did you try to change your download servers using the linked tutorial?

Regards.

---

