---
title: "Ubuntu 14.04 LTS - Package Operation Fails on update."
date: 2014-11-01
forum: New to Ubuntu
---

### Post by Ash1403 on 2014-11-01
Hi All,
Hope someone can help me.
Whenever I update, I get a Package Operation Failed message. I'm unsure why.

I've done:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
```

Outputs below.

Can anyone help, please?

Thanks
Ash1403

```
**sudo apt-get update**
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://download.videolan.org](http://download.videolan.org)  InRelease                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://download.videolan.org](http://download.videolan.org)  Release.gpg                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://download.videolan.org](http://download.videolan.org)  Release                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main amd64 Packages                       
Hit [http://download.videolan.org](http://download.videolan.org)  Sources                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:1 [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid InRelease [2,146 B]                     
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid InRelease                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Hit [http://download.videolan.org](http://download.videolan.org)  Packages                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main i386 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://apt.sourcefabric.org](http://apt.sourcefabric.org) trusty InRelease                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy InRelease                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty InRelease                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release.gpg                        
Ign [http://download.videolan.org](http://download.videolan.org)  Translation-en_GB                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://download.videolan.org](http://download.videolan.org)  Translation-en                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB                 
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release                            
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en                       
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main amd64 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb InRelease                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main amd64 Packages               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main i386 Packages                
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main amd64 Packages/DiffIndex             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Translation-en      
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main i386 Packages/DiffIndex              
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main amd64 Packages                   
Hit [http://apt.sourcefabric.org](http://apt.sourcefabric.org) trusty/main amd64 Packages                     
Hit [http://apt.sourcefabric.org](http://apt.sourcefabric.org) trusty/main i386 Packages                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_GB
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en          
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en_GB           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en_GB         
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) trusty/main Translation-en         
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages            
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en             
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps amd64 Packages              
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games amd64 Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps i386 Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Hit [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main amd64 Packages                       
Hit [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main i386 Packages                        
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main Translation-en_GB                    
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main Translation-en                       
Ign [http://apt.sourcefabric.org](http://apt.sourcefabric.org) trusty/main Translation-en_GB                  
Ign [http://apt.sourcefabric.org](http://apt.sourcefabric.org) trusty/main Translation-en                     
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_GB               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en_GB             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/apps Translation-en                
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games Translation-en_GB            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) trusty-getdeb/games Translation-en               
Fetched 2,146 B in 13s (164 B/s)                                               
Reading package lists... Done
W: GPG error: [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 43525C28E533491A
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/)  Packages (/var/lib/apt/lists/download.videolan.org_pub_debian_stable_Packages)
```


```
**sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up airtime (2.5.1-3) ...
Setting up apache2...
Site airtime-vhost already disabled
Apache 2.4 detected, using newer access configuration...
sed: can't read /etc/airtime/apache24.vhost.tpl: No such file or directory
dpkg: error processing package airtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 airtime
E: Sub-process /usr/bin/dpkg returned an error code (1)
ashley@ashley-MS-7721:~$
```

---

### Post by Alireza_Zamani on 2014-11-01
what is "airtime" ?
you can remove it;

```
$ apt-get remove airtime
```

---

### Post by Bucky Ball on 2014-11-01
```
**sudo** apt-get remove airtime
```

If you don't need 'sudo' you are running as root and that is not good (unless it's temporarily in a terminal).

In Software Sources (Software Updater>Settings>Other Software) locate this repo and disable it:

```
W: GPG error: http://plex.r.worldssl.net lucid 
```

It is for Lucid and you are using Trusty. For the other three:

```
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_b inary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_b inary-i386_Packages)
W: Duplicate sources.list entry http://download.videolan.org/pub/debian/stable/ Packages (/var/lib/apt/lists/download.videolan.org_pub_debian_stable_Packages)
```

You have them in your software sources twice by the looks. Find the dulicates and disable or remove them in Software Sources. Then:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

The last command doesn't upgrade you to a newer OS, it upgrades the software in the release you are currently running, if required.

Report back any errors.

PS: And please use [code] tags. The last link in my signature shows you how. Neater, space-saving and easier to read. Thanks. I have done them in your first post as an example.

---

