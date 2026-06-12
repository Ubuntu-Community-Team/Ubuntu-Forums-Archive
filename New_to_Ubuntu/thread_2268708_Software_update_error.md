---
title: "Software update error"
date: 2015-03-10
forum: New to Ubuntu
---

### Post by anbu-s on 2015-03-10
In the software updater, I get the following error msg:

Unkown error <class keyeoror> The cache has no package named 'wine-staging-i386'. This usually means your untrusted packages have unmet dependencies

I did have wine installed - since i dont use it, i've removed it already. Even then this message keeps popping up during softawre upgrade.
How can i correct this?

sudo apt-get update displayes the following errors:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 3,389 kB in 20s (162 kB/s)                                             
W: GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: Failed to fetch [http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by v3.xx on 2015-03-10
[http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/](http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/)

[http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/](http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/)

Those are old PPAs and no longer supported.  The other 404s are dead.

Is this a upgrade to 14.04, maybe from 10.04?

You need to remove all those old PPAs.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9)

---

### Post by anbu-s on 2015-03-10
> **v3.xx said:**
> [http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/](http://ppa.launchpad.net/kklimonda/evo232/ubuntu/dists/)

[http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/](http://ppa.launchpad.net/upubuntu-com/mobile/ubuntu/dists/)

Those are old PPAs and no longer supported.  The other 404s are dead.

Is this a upgrade to 14.04, maybe from 10.04?

You need to remove all those old PPAs.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa&sa=Search&cof=FORID:9)

Thanks. I removed the old PPAs as per the instruction and still get this error when i do the sudo apt-get update command
```

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg                                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty InRelease                              
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy InRelease                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release                                    
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat InRelease          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy/main amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy/main i386 Packages                 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main amd64 Packages                        
Get:1 [https://download.01.org](https://download.01.org) trusty InRelease                                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed InRelease                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Ign [https://download.01.org](https://download.01.org) trusty InRelease                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release.gpg                            
Get:2 [https://download.01.org](https://download.01.org) trusty/main amd64 Packages/DiffIndex             
Ign [https://download.01.org](https://download.01.org) trusty/main amd64 Packages/DiffIndex               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Ign [https://download.01.org](https://download.01.org) trusty/main i386 Packages/DiffIndex                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                        
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed Release.gpg                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_CA                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_CA                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages     
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                    
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy/main Translation-en_CA 
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy/main Translation-en    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en  
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en  
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Sources  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Sources    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main amd64 Packages 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [https://download.01.org](https://download.01.org) trusty/main amd64 Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                        
Hit [https://download.01.org](https://download.01.org) trusty/main i386 Packages                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                        
Get:6 [https://download.01.org](https://download.01.org) trusty/main Translation-en_CA                    
Ign [https://download.01.org](https://download.01.org) trusty/main Translation-en_CA                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-updates/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex        
Ign [https://download.01.org](https://download.01.org) trusty/main Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Sources     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/restricted Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/main Sources                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/multiverse Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/universe Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/restricted amd64 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/main amd64 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/multiverse amd64 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/universe amd64 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/restricted i386 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/main i386 Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/universe i386 Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/main Translation-en_CA        
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [13.1 kB]            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/main Translation-en           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/multiverse Translation-en     
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [13.1 kB]             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/restricted Translation-en     
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [4,637 B]            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty-proposed/universe Translation-en       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_CA                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Fetched 50.3 kB in 24s (2,078 B/s)                                             
Reading package lists... Done
W: GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B70731143DD9F856

```

---

### Post by anbu-s on 2015-03-10
Solved it by getting the public keys from the server...google helps!! thanks

---

### Post by Bashing-om on 2015-03-10
anbu-s; Nope;

Not done yet, that latest still has something(s) calling for precise.
Post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
if you want, we can take a look and see what we can find.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by anbu-s on 2015-03-11
> **Bashing-om said:**
> anbu-s; Nope;

Not done yet, that latest still has something(s) calling for precise.
Post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
if you want, we can take a look and see what we can find.[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]



Here is the output of the commands. Please let me know

cat -n /etc/apt/sources.list
```
1    # deb cdrom:[Ubuntu-GNOME 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe
     2    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main multiverse restricted universe #Added by software-properties
     3    
     4    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     5    # newer versions of the distribution.
     6    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty main restricted
     7    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty restricted main multiverse universe #Added by software-properties
     8    
     9    ## Major bug fix updates produced after the final release of the
    10    ## distribution.
    11    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates restricted main multiverse universe #Added by software-properties
    13    
    14    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15    ## team. Also, please note that software in universe WILL NOT receive any
    16    ## review or updates from the Ubuntu security team.
    17    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty universe
    18    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty multiverse
    26    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    27    
    28    ## N.B. software from this repository may not have been tested as
    29    ## extensively as that contained in the main release, although it includes
    30    ## newer versions of some applications which may provide useful features.
    31    ## Also, please note that software in backports WILL NOT receive any review
    32    ## or updates from the Ubuntu security team.
    33    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    34    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse #Added by software-properties
    35    
    36    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    37    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security restricted main multiverse universe #Added by software-properties
    38    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    39    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    46    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    47    
    48    ## Uncomment the following two lines to add software from Ubuntu's
    49    ## 'extras' repository.
    50    ## This software is not part of Ubuntu, but is offered by third-party
    51    ## developers who want to ship their latest software.
    52    # deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    53    # deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    54    # deb [http://ppa.launchpad.net/natecarlson/maven3/ubuntu](http://ppa.launchpad.net/natecarlson/maven3/ubuntu) precise main
    55    deb-src [http://ppa.launchpad.net/natecarlson/maven3/ubuntu](http://ppa.launchpad.net/natecarlson/maven3/ubuntu) precise main
    56    # deb-src [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main
    57    deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-proposed restricted main multiverse universe
    58    deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) trusty-proposed restricted main multiverse universe #Added by software-properties
```
anbu@Terminatore:~$ tail -v -n +1 /etc/apt/sources.list.d/*
```
==> /etc/apt/sources.list.d/dropbox.list <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main

==> /etc/apt/sources.list.d/dropbox.list.save <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main

==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list <==
deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) trusty main

==> /etc/apt/sources.list.d/fingerprint-fingerprint-gui-trusty.list.save <==
deb [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu](http://ppa.launchpad.net/fingerprint/fingerprint-gui/ubuntu) trusty main

==> /etc/apt/sources.list.d/fingerprint-fprint-trusty.list <==
deb [http://ppa.launchpad.net/fingerprint/fprint/ubuntu](http://ppa.launchpad.net/fingerprint/fprint/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fingerprint/fprint/ubuntu](http://ppa.launchpad.net/fingerprint/fprint/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fingerprint/fprint/ubuntu](http://ppa.launchpad.net/fingerprint/fprint/ubuntu) trusty main

==> /etc/apt/sources.list.d/fingerprint-fprint-trusty.list.save <==
deb [http://ppa.launchpad.net/fingerprint/fprint/ubuntu](http://ppa.launchpad.net/fingerprint/fprint/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fingerprint/fprint/ubuntu](http://ppa.launchpad.net/fingerprint/fprint/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fingerprint/fprint/ubuntu](http://ppa.launchpad.net/fingerprint/fprint/ubuntu) trusty main

==> /etc/apt/sources.list.d/fta-gnome3-trusty.list <==
# deb [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/fta-gnome3-trusty.list.save <==
# deb [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/fta/gnome3/ubuntu](http://ppa.launchpad.net/fta/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-staging-trusty.list <==
# deb [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-staging-trusty.list.save <==
# deb [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-trusty.list <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/gnome3-team-gnome3-trusty.list.save <==
deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) trusty main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

==> /etc/apt/sources.list.d/google-talkplugin.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

==> /etc/apt/sources.list.d/google-talkplugin.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

==> /etc/apt/sources.list.d/intellinuxgraphics.list <==
deb [https://download.01.org/gfx/ubuntu/14.04/main](https://download.01.org/gfx/ubuntu/14.04/main) trusty main #Intel Graphics drivers

==> /etc/apt/sources.list.d/intellinuxgraphics.list.save <==
deb [https://download.01.org/gfx/ubuntu/14.04/main](https://download.01.org/gfx/ubuntu/14.04/main) trusty main #Intel Graphics drivers

==> /etc/apt/sources.list.d/jon-hedgerows-get-iplayer-trusty.list <==
# deb [http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu](http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu](http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu) trusty main

==> /etc/apt/sources.list.d/jon-hedgerows-get-iplayer-trusty.list.save <==
# deb [http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu](http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu](http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu) trusty main

==> /etc/apt/sources.list.d/kklimonda-evo232-trusty.list <==

==> /etc/apt/sources.list.d/kklimonda-evo232-trusty.list.save <==

==> /etc/apt/sources.list.d/light-locker-release-trusty.list <==
deb [http://ppa.launchpad.net/light-locker/release/ubuntu](http://ppa.launchpad.net/light-locker/release/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/light-locker/release/ubuntu](http://ppa.launchpad.net/light-locker/release/ubuntu) trusty main

==> /etc/apt/sources.list.d/light-locker-release-trusty.list.save <==
deb [http://ppa.launchpad.net/light-locker/release/ubuntu](http://ppa.launchpad.net/light-locker/release/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/light-locker/release/ubuntu](http://ppa.launchpad.net/light-locker/release/ubuntu) trusty main

==> /etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list <==
deb [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu) trusty main

==> /etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list.save <==
deb [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu) trusty main

==> /etc/apt/sources.list.d/mono-xamarin.list <==
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy main
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy-apache24-compat main

==> /etc/apt/sources.list.d/mono-xamarin.list.save <==
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy main
deb [http://download.mono-project.com/repo/debian](http://download.mono-project.com/repo/debian) wheezy-apache24-compat main

==> /etc/apt/sources.list.d/noobslab-themes-trusty.list <==
deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main

==> /etc/apt/sources.list.d/noobslab-themes-trusty.list.save <==
deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) trusty main

==> /etc/apt/sources.list.d/opera-stable.list <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb [http://deb.opera.com/opera-stable/](http://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)



==> /etc/apt/sources.list.d/opera-stable.list.save <==
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb [http://deb.opera.com/opera-stable/](http://deb.opera.com/opera-stable/) stable non-free #Opera Browser (final releases)



==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==
deb [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==
deb [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/pi-rho-security-trusty.list <==
deb [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main

==> /etc/apt/sources.list.d/pi-rho-security-trusty.list.save <==
deb [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pi-rho/security/ubuntu](http://ppa.launchpad.net/pi-rho/security/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julia-deps-trusty.list <==
# deb [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julia-deps-trusty.list.save <==
# deb [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu](http://ppa.launchpad.net/staticfloat/julia-deps/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julianightlies-trusty.list <==
# deb [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main

==> /etc/apt/sources.list.d/staticfloat-julianightlies-trusty.list.save <==
# deb [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu](http://ppa.launchpad.net/staticfloat/julianightlies/ubuntu) trusty main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list <==
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/upubuntu-com-mobile-trusty.list <==

==> /etc/apt/sources.list.d/upubuntu-com-mobile-trusty.list.save <==
anbu@Terminatore:~$
```

---

### Post by v3.xx on 2015-03-11
One thing that pops out is:
> deb-src [http://ppa.launchpad.net/natecarlson/maven3/ubuntu](http://ppa.launchpad.net/natecarlson/maven3/ubuntu) precise main
Do another update after you edit that and see if your good.

@Bashing
```
tail -v -n +1 /etc/apt/sources.list.d/*
```
Nice command :)


Edit:
Check this out :)
```
tail -v -n +1 /etc/apt/sources.list.d/*.list
```

---

### Post by anbu-s on 2015-03-11
What do u mean by edit the PPA? should i remove it?
Sorry I'm relatively new to ubuntu..

---

### Post by deadflowr on 2015-03-11
> **anbu-s said:**
> What do u mean by edit the PPA? should i remove it?
Sorry I'm relatively new to ubuntu..

You can edit out a ppa by opening the program called Software and Updates.
Then go to the section "Other Software" and locate the ppa listed above and uncheck it, or even highlight it and click on remove.
It'll ask for your password when you do this.
Then press the Close button, and exit the Software and updates window and it should start a reload/refresh.
If it does not start to reload, go to software updater and this will run the reload/refresh.

If an error pops up after trying this, perhaps it will be a matter of honing in on the problematic ppa. Or something...

---

### Post by Bashing-om on 2015-03-11
@ anbu-s; Hey, hey;

+1 to all .. that one is all I see presently, will see what the situation is when 'update/upgrade' is run.
As always, deadflowr is spot on .

> **v3.xx said:**
> One thing that pops out is:

Do another update after you edit that and see if your good.

@Bashing
```
tail -v -n +1 /etc/apt/sources.list.d/*
```
Nice command :)
@v3.xx :)
I am learning bash, a long process and a long way to go . Your mod is the more concise .

Edit:
Check this out :)
```
tail -v -n +1 /etc/apt/sources.list.d/*.list
```


It takes a village to raise a child
[INDENT][INDENT]it takes the world to raise 'buntu
[/INDENT][/INDENT]

---

### Post by v3.xx on 2015-03-11
Why not take it one step further and just disable all 'deb-scr'.  These are for the source packages that would be used to alter package code and not anything that should be needed by you.

Open your software sources and uncheck 'source code'.
```
software-properties-gtk
```
[ATTACH=CONFIG]260570[/ATTACH]

---

