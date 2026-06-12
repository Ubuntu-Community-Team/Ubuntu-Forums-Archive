---
title: "cannot install software from the software center untrusted sources warning"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by send2 on 2013-11-01
Hi all, I am running Ubuntu Precise 12.04 and today when I tried to download Xsane for scanning (it did not download successfully), everytime now I tried to download software from the software center, I get the untrusted sources warning. How can I get rid of this error plus the errors I am getting when I run apt-get update? 

Here is the result from the command line:

```
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Release
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Release
Err cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Translation-en
Err cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Translation-en
Err http://extras.ubuntu.com precise Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Get:1 https://private-ppa.launchpad.net precise Release.gpg [316 B]            
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:2 https://private-ppa.launchpad.net precise/main TranslationIndex [364 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:3 https://private-ppa.launchpad.net precise/main TranslationIndex [362 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Hit http://extras.ubuntu.com precise Release                                   
Ign http://extras.ubuntu.com precise/main Sources/DiffIndex                    
Ign http://extras.ubuntu.com precise/main amd64 Packages/DiffIndex             
Ign http://extras.ubuntu.com precise/main i386 Packages/DiffIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Err http://repository.spotify.com stable Release.gpg                           
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://deb.opera.com stable Release.gpg                                    
  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Err http://mirror.steadfast.net precise Release.gpg                            
  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable Release.gpg                                    
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://repo.steampowered.com precise Release.gpg                           
  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)
Err http://download.virtualbox.org precise Release.gpg                         
  Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Hit http://download.virtualbox.org precise Release                             
Ign http://download.virtualbox.org precise/contrib amd64 Packages/DiffIndex    
Ign http://download.virtualbox.org precise/contrib i386 Packages/DiffIndex     
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Hit http://download.virtualbox.org precise/contrib amd64 Packages              
Hit http://download.virtualbox.org precise/contrib i386 Packages               
Ign http://download.virtualbox.org precise/contrib Translation-en_US           
Ign http://download.virtualbox.org precise/contrib Translation-en              
Get:4 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:5 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:8 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:9 http://ppa.launchpad.net precise/main Sources [9,881 B]                  
Get:10 http://ppa.launchpad.net precise/main amd64 Packages [7,009 B]          
Get:11 http://ppa.launchpad.net precise/main i386 Packages [7,009 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:12 http://ppa.launchpad.net precise/main Sources [27.0 kB]                 
Get:13 http://ppa.launchpad.net precise/main amd64 Packages [16.6 kB]          
Get:14 http://ppa.launchpad.net precise/main i386 Packages [16.6 kB]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://repo.steampowered.com precise Release                               
Ign http://repo.steampowered.com precise/steam Sources/DiffIndex               
Ign http://repo.steampowered.com precise/steam amd64 Packages/DiffIndex        
Ign http://repo.steampowered.com precise/steam i386 Packages/DiffIndex         
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Err http://mirror.steadfast.net precise-updates Release.gpg                    
  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://mirror.steadfast.net precise-backports Release.gpg                  
Hit http://mirror.steadfast.net precise-security Release.gpg                   
Hit http://mirror.steadfast.net precise Release                                
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://mirror.steadfast.net precise-updates Release                        
Hit http://mirror.steadfast.net precise-backports Release                      
Hit http://mirror.steadfast.net precise-security Release                       
Ign http://mirror.steadfast.net precise/main Sources/DiffIndex                 
Ign http://mirror.steadfast.net precise/restricted Sources/DiffIndex           
Ign http://mirror.steadfast.net precise/multiverse Sources/DiffIndex           
Ign http://mirror.steadfast.net precise/universe Sources/DiffIndex             
Ign http://mirror.steadfast.net precise/main amd64 Packages/DiffIndex          
Ign http://mirror.steadfast.net precise/restricted amd64 Packages/DiffIndex    
Ign http://mirror.steadfast.net precise/multiverse amd64 Packages/DiffIndex    
Ign http://mirror.steadfast.net precise/universe amd64 Packages/DiffIndex      
Ign http://mirror.steadfast.net precise/main i386 Packages/DiffIndex           
Ign http://mirror.steadfast.net precise/restricted i386 Packages/DiffIndex     
Ign http://mirror.steadfast.net precise/multiverse i386 Packages/DiffIndex     
Ign http://mirror.steadfast.net precise/universe i386 Packages/DiffIndex       
Hit http://mirror.steadfast.net precise/main TranslationIndex                  
Hit http://mirror.steadfast.net precise/multiverse TranslationIndex            
Hit http://mirror.steadfast.net precise/restricted TranslationIndex            
Hit http://mirror.steadfast.net precise/universe TranslationIndex              
Ign http://mirror.steadfast.net precise-updates/main Sources/DiffIndex         
Ign http://mirror.steadfast.net precise-updates/restricted Sources/DiffIndex   
Ign http://mirror.steadfast.net precise-updates/multiverse Sources/DiffIndex   
Ign http://mirror.steadfast.net precise-updates/universe Sources/DiffIndex     
Ign http://mirror.steadfast.net precise-updates/main amd64 Packages/DiffIndex  
Ign http://mirror.steadfast.net precise-updates/restricted amd64 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/multiverse amd64 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/universe amd64 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/main i386 Packages/DiffIndex   
Ign http://mirror.steadfast.net precise-updates/restricted i386 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/multiverse i386 Packages/DiffIndex
Ign http://repository.spotify.com stable Release                               
Ign http://deb.opera.com stable Release                                        
Ign http://dl.google.com stable Release                                        
Ign http://mirror.steadfast.net precise-updates/universe i386 Packages/DiffIndex
Hit http://mirror.steadfast.net precise-updates/main TranslationIndex          
Hit http://mirror.steadfast.net precise-updates/multiverse TranslationIndex    
Hit http://mirror.steadfast.net precise-updates/restricted TranslationIndex    
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                  
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://mirror.steadfast.net precise-updates/universe TranslationIndex      
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://mirror.steadfast.net precise-backports/main Sources                 
Hit http://mirror.steadfast.net precise-backports/restricted Sources           
Hit http://mirror.steadfast.net precise-backports/universe Sources             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://mirror.steadfast.net precise-backports/multiverse Sources           
Hit http://mirror.steadfast.net precise-backports/main amd64 Packages          
Hit http://mirror.steadfast.net precise-backports/restricted amd64 Packages    
Hit http://mirror.steadfast.net precise-backports/universe amd64 Packages      
Hit http://mirror.steadfast.net precise-backports/multiverse amd64 Packages    
Hit http://mirror.steadfast.net precise-backports/main i386 Packages    
Hit http://mirror.steadfast.net precise-backports/restricted i386 Packages
Hit http://mirror.steadfast.net precise-backports/universe i386 Packages
Hit http://mirror.steadfast.net precise-backports/multiverse i386 Packages
Hit http://mirror.steadfast.net precise-backports/main TranslationIndex 
Hit http://mirror.steadfast.net precise-backports/multiverse TranslationIndex  
Hit http://mirror.steadfast.net precise-backports/restricted TranslationIndex  
Hit http://mirror.steadfast.net precise-backports/universe TranslationIndex    
Hit http://mirror.steadfast.net precise-security/main Sources                  
Hit http://mirror.steadfast.net precise-security/restricted Sources            
Hit http://mirror.steadfast.net precise-security/multiverse Sources            
Hit http://mirror.steadfast.net precise-security/universe Sources              
Hit http://mirror.steadfast.net precise-security/main amd64 Packages           
Hit http://mirror.steadfast.net precise-security/restricted amd64 Packages     
Hit http://mirror.steadfast.net precise-security/multiverse amd64 Packages     
Hit http://mirror.steadfast.net precise-security/universe amd64 Packages       
Hit http://mirror.steadfast.net precise-security/main i386 Packages            
Hit http://mirror.steadfast.net precise-security/restricted i386 Packages      
Hit http://mirror.steadfast.net precise-security/multiverse i386 Packages      
Hit http://mirror.steadfast.net precise-security/universe i386 Packages        
Hit http://mirror.steadfast.net precise-security/main TranslationIndex         
Hit http://mirror.steadfast.net precise-security/multiverse TranslationIndex   
Hit http://mirror.steadfast.net precise-security/restricted TranslationIndex   
Hit http://mirror.steadfast.net precise-security/universe TranslationIndex     
Hit http://mirror.steadfast.net precise/main Sources                           
Hit http://mirror.steadfast.net precise/restricted Sources                     
Hit http://mirror.steadfast.net precise/multiverse Sources                     
Hit http://mirror.steadfast.net precise/universe Sources                       
Hit http://mirror.steadfast.net precise/main amd64 Packages                    
Hit http://mirror.steadfast.net precise/restricted amd64 Packages              
Hit http://mirror.steadfast.net precise/multiverse amd64 Packages              
Hit http://mirror.steadfast.net precise/universe amd64 Packages                
Hit http://mirror.steadfast.net precise/main i386 Packages                     
Hit http://mirror.steadfast.net precise/restricted i386 Packages               
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Hit http://mirror.steadfast.net precise/multiverse i386 Packages
Hit http://mirror.steadfast.net precise/universe i386 Packages                 
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://mirror.steadfast.net precise/main Translation-en                    
Hit http://mirror.steadfast.net precise/multiverse Translation-en              
Hit http://mirror.steadfast.net precise/restricted Translation-en              
Hit http://mirror.steadfast.net precise/universe Translation-en                
Hit http://mirror.steadfast.net precise-updates/main Sources                   
Hit http://mirror.steadfast.net precise-updates/restricted Sources             
Hit http://mirror.steadfast.net precise-updates/multiverse Sources             
Hit http://mirror.steadfast.net precise-updates/universe Sources               
Hit http://mirror.steadfast.net precise-updates/main amd64 Packages            
Hit http://mirror.steadfast.net precise-updates/restricted amd64 Packages      
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://mirror.steadfast.net precise-updates/multiverse amd64 Packages      
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://mirror.steadfast.net precise-updates/universe amd64 Packages        
Hit http://mirror.steadfast.net precise-updates/main i386 Packages             
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://mirror.steadfast.net precise-updates/restricted i386 Packages       
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://mirror.steadfast.net precise-updates/multiverse i386 Packages       
Hit http://mirror.steadfast.net precise-updates/universe i386 Packages
Hit http://mirror.steadfast.net precise-updates/main Translation-en            
Hit http://mirror.steadfast.net precise-updates/multiverse Translation-en      
Hit http://mirror.steadfast.net precise-updates/restricted Translation-en      
Hit http://mirror.steadfast.net precise-updates/universe Translation-en        
Hit http://mirror.steadfast.net precise-backports/main Translation-en          
Hit http://mirror.steadfast.net precise-backports/multiverse Translation-en    
Hit http://mirror.steadfast.net precise-backports/restricted Translation-en    
Hit http://mirror.steadfast.net precise-backports/universe Translation-en      
Hit http://mirror.steadfast.net precise-security/main Translation-en
Hit http://mirror.steadfast.net precise-security/multiverse Translation-en
Hit http://mirror.steadfast.net precise-security/restricted Translation-en
Hit http://mirror.steadfast.net precise-security/universe Translation-en       
Ign http://repository.spotify.com stable/non-free Sources/DiffIndex            
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex
Ign http://repository.spotify.com stable/non-free TranslationIndex
Hit http://repository.spotify.com stable/non-free Sources
Hit http://repository.spotify.com stable/non-free amd64 Packages
Hit http://repository.spotify.com stable/non-free i386 Packages
Ign http://repository.spotify.com stable/non-free Translation-en_US
Ign http://repository.spotify.com stable/non-free Translation-en
Fetched 109 kB in 52s (2,096 B/s)
W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-updates/Release.gpg  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anupku/skull-wood-bones/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repo.steampowered.com/steam/dists/precise/Release.gpg  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/Release.gpg  Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)

W: Failed to fetch cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Sorry for the long paste, I was not sure what to cut out. I changed the server hoping that would help, I have been googling an answer to my problem, but everything I tried has not worked. 

thanks for looking at the errors...

Thanks to all of you who helped. I will mark this thread solved.

---

### Post by ibjsb4 on 2013-11-01
Its done like this :)

```
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Release.gpg
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Release.gpg
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Release
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Release
Err cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/main/binary-i386/ Translation-en
Err cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Translation-en_US
Ign cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018) dists/quantal/restricted/binary-i386/ Translation-en
Err http://extras.ubuntu.com precise Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Get:1 https://private-ppa.launchpad.net precise Release.gpg [316 B]            
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:2 https://private-ppa.launchpad.net precise/main TranslationIndex [364 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:3 https://private-ppa.launchpad.net precise/main TranslationIndex [362 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Hit http://extras.ubuntu.com precise Release                                   
Ign http://extras.ubuntu.com precise/main Sources/DiffIndex                    
Ign http://extras.ubuntu.com precise/main amd64 Packages/DiffIndex             
Ign http://extras.ubuntu.com precise/main i386 Packages/DiffIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Err http://repository.spotify.com stable Release.gpg                           
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Err http://deb.opera.com stable Release.gpg                                    
  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Err http://mirror.steadfast.net precise Release.gpg                            
  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable Release.gpg                                    
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Err http://repo.steampowered.com precise Release.gpg                           
  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)
Err http://download.virtualbox.org precise Release.gpg                         
  Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Hit http://download.virtualbox.org precise Release                             
Ign http://download.virtualbox.org precise/contrib amd64 Packages/DiffIndex    
Ign http://download.virtualbox.org precise/contrib i386 Packages/DiffIndex     
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Hit http://download.virtualbox.org precise/contrib amd64 Packages              
Hit http://download.virtualbox.org precise/contrib i386 Packages               
Ign http://download.virtualbox.org precise/contrib Translation-en_US           
Ign http://download.virtualbox.org precise/contrib Translation-en              
Get:4 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:5 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:6 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:8 http://ppa.launchpad.net precise Release [11.9 kB]                       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:9 http://ppa.launchpad.net precise/main Sources [9,881 B]                  
Get:10 http://ppa.launchpad.net precise/main amd64 Packages [7,009 B]          
Get:11 http://ppa.launchpad.net precise/main i386 Packages [7,009 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:12 http://ppa.launchpad.net precise/main Sources [27.0 kB]                 
Get:13 http://ppa.launchpad.net precise/main amd64 Packages [16.6 kB]          
Get:14 http://ppa.launchpad.net precise/main i386 Packages [16.6 kB]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://repo.steampowered.com precise Release                               
Ign http://repo.steampowered.com precise/steam Sources/DiffIndex               
Ign http://repo.steampowered.com precise/steam amd64 Packages/DiffIndex        
Ign http://repo.steampowered.com precise/steam i386 Packages/DiffIndex         
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Err http://mirror.steadfast.net precise-updates Release.gpg                    
  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://mirror.steadfast.net precise-backports Release.gpg                  
Hit http://mirror.steadfast.net precise-security Release.gpg                   
Hit http://mirror.steadfast.net precise Release                                
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://mirror.steadfast.net precise-updates Release                        
Hit http://mirror.steadfast.net precise-backports Release                      
Hit http://mirror.steadfast.net precise-security Release                       
Ign http://mirror.steadfast.net precise/main Sources/DiffIndex                 
Ign http://mirror.steadfast.net precise/restricted Sources/DiffIndex           
Ign http://mirror.steadfast.net precise/multiverse Sources/DiffIndex           
Ign http://mirror.steadfast.net precise/universe Sources/DiffIndex             
Ign http://mirror.steadfast.net precise/main amd64 Packages/DiffIndex          
Ign http://mirror.steadfast.net precise/restricted amd64 Packages/DiffIndex    
Ign http://mirror.steadfast.net precise/multiverse amd64 Packages/DiffIndex    
Ign http://mirror.steadfast.net precise/universe amd64 Packages/DiffIndex      
Ign http://mirror.steadfast.net precise/main i386 Packages/DiffIndex           
Ign http://mirror.steadfast.net precise/restricted i386 Packages/DiffIndex     
Ign http://mirror.steadfast.net precise/multiverse i386 Packages/DiffIndex     
Ign http://mirror.steadfast.net precise/universe i386 Packages/DiffIndex       
Hit http://mirror.steadfast.net precise/main TranslationIndex                  
Hit http://mirror.steadfast.net precise/multiverse TranslationIndex            
Hit http://mirror.steadfast.net precise/restricted TranslationIndex            
Hit http://mirror.steadfast.net precise/universe TranslationIndex              
Ign http://mirror.steadfast.net precise-updates/main Sources/DiffIndex         
Ign http://mirror.steadfast.net precise-updates/restricted Sources/DiffIndex   
Ign http://mirror.steadfast.net precise-updates/multiverse Sources/DiffIndex   
Ign http://mirror.steadfast.net precise-updates/universe Sources/DiffIndex     
Ign http://mirror.steadfast.net precise-updates/main amd64 Packages/DiffIndex  
Ign http://mirror.steadfast.net precise-updates/restricted amd64 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/multiverse amd64 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/universe amd64 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/main i386 Packages/DiffIndex   
Ign http://mirror.steadfast.net precise-updates/restricted i386 Packages/DiffIndex
Ign http://mirror.steadfast.net precise-updates/multiverse i386 Packages/DiffIndex
Ign http://repository.spotify.com stable Release                               
Ign http://deb.opera.com stable Release                                        
Ign http://dl.google.com stable Release                                        
Ign http://mirror.steadfast.net precise-updates/universe i386 Packages/DiffIndex
Hit http://mirror.steadfast.net precise-updates/main TranslationIndex          
Hit http://mirror.steadfast.net precise-updates/multiverse TranslationIndex    
Hit http://mirror.steadfast.net precise-updates/restricted TranslationIndex    
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                  
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://mirror.steadfast.net precise-updates/universe TranslationIndex      
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://mirror.steadfast.net precise-backports/main Sources                 
Hit http://mirror.steadfast.net precise-backports/restricted Sources           
Hit http://mirror.steadfast.net precise-backports/universe Sources             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://mirror.steadfast.net precise-backports/multiverse Sources           
Hit http://mirror.steadfast.net precise-backports/main amd64 Packages          
Hit http://mirror.steadfast.net precise-backports/restricted amd64 Packages    
Hit http://mirror.steadfast.net precise-backports/universe amd64 Packages      
Hit http://mirror.steadfast.net precise-backports/multiverse amd64 Packages    
Hit http://mirror.steadfast.net precise-backports/main i386 Packages    
Hit http://mirror.steadfast.net precise-backports/restricted i386 Packages
Hit http://mirror.steadfast.net precise-backports/universe i386 Packages
Hit http://mirror.steadfast.net precise-backports/multiverse i386 Packages
Hit http://mirror.steadfast.net precise-backports/main TranslationIndex 
Hit http://mirror.steadfast.net precise-backports/multiverse TranslationIndex  
Hit http://mirror.steadfast.net precise-backports/restricted TranslationIndex  
Hit http://mirror.steadfast.net precise-backports/universe TranslationIndex    
Hit http://mirror.steadfast.net precise-security/main Sources                  
Hit http://mirror.steadfast.net precise-security/restricted Sources            
Hit http://mirror.steadfast.net precise-security/multiverse Sources            
Hit http://mirror.steadfast.net precise-security/universe Sources              
Hit http://mirror.steadfast.net precise-security/main amd64 Packages           
Hit http://mirror.steadfast.net precise-security/restricted amd64 Packages     
Hit http://mirror.steadfast.net precise-security/multiverse amd64 Packages     
Hit http://mirror.steadfast.net precise-security/universe amd64 Packages       
Hit http://mirror.steadfast.net precise-security/main i386 Packages            
Hit http://mirror.steadfast.net precise-security/restricted i386 Packages      
Hit http://mirror.steadfast.net precise-security/multiverse i386 Packages      
Hit http://mirror.steadfast.net precise-security/universe i386 Packages        
Hit http://mirror.steadfast.net precise-security/main TranslationIndex         
Hit http://mirror.steadfast.net precise-security/multiverse TranslationIndex   
Hit http://mirror.steadfast.net precise-security/restricted TranslationIndex   
Hit http://mirror.steadfast.net precise-security/universe TranslationIndex     
Hit http://mirror.steadfast.net precise/main Sources                           
Hit http://mirror.steadfast.net precise/restricted Sources                     
Hit http://mirror.steadfast.net precise/multiverse Sources                     
Hit http://mirror.steadfast.net precise/universe Sources                       
Hit http://mirror.steadfast.net precise/main amd64 Packages                    
Hit http://mirror.steadfast.net precise/restricted amd64 Packages              
Hit http://mirror.steadfast.net precise/multiverse amd64 Packages              
Hit http://mirror.steadfast.net precise/universe amd64 Packages                
Hit http://mirror.steadfast.net precise/main i386 Packages                     
Hit http://mirror.steadfast.net precise/restricted i386 Packages               
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Hit http://mirror.steadfast.net precise/multiverse i386 Packages
Hit http://mirror.steadfast.net precise/universe i386 Packages                 
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://mirror.steadfast.net precise/main Translation-en                    
Hit http://mirror.steadfast.net precise/multiverse Translation-en              
Hit http://mirror.steadfast.net precise/restricted Translation-en              
Hit http://mirror.steadfast.net precise/universe Translation-en                
Hit http://mirror.steadfast.net precise-updates/main Sources                   
Hit http://mirror.steadfast.net precise-updates/restricted Sources             
Hit http://mirror.steadfast.net precise-updates/multiverse Sources             
Hit http://mirror.steadfast.net precise-updates/universe Sources               
Hit http://mirror.steadfast.net precise-updates/main amd64 Packages            
Hit http://mirror.steadfast.net precise-updates/restricted amd64 Packages      
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://mirror.steadfast.net precise-updates/multiverse amd64 Packages      
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://mirror.steadfast.net precise-updates/universe amd64 Packages        
Hit http://mirror.steadfast.net precise-updates/main i386 Packages             
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://mirror.steadfast.net precise-updates/restricted i386 Packages       
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://mirror.steadfast.net precise-updates/multiverse i386 Packages       
Hit http://mirror.steadfast.net precise-updates/universe i386 Packages
Hit http://mirror.steadfast.net precise-updates/main Translation-en            
Hit http://mirror.steadfast.net precise-updates/multiverse Translation-en      
Hit http://mirror.steadfast.net precise-updates/restricted Translation-en      
Hit http://mirror.steadfast.net precise-updates/universe Translation-en        
Hit http://mirror.steadfast.net precise-backports/main Translation-en          
Hit http://mirror.steadfast.net precise-backports/multiverse Translation-en    
Hit http://mirror.steadfast.net precise-backports/restricted Translation-en    
Hit http://mirror.steadfast.net precise-backports/universe Translation-en      
Hit http://mirror.steadfast.net precise-security/main Translation-en
Hit http://mirror.steadfast.net precise-security/multiverse Translation-en
Hit http://mirror.steadfast.net precise-security/restricted Translation-en
Hit http://mirror.steadfast.net precise-security/universe Translation-en       
Ign http://repository.spotify.com stable/non-free Sources/DiffIndex            
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex
Ign http://repository.spotify.com stable/non-free TranslationIndex
Hit http://repository.spotify.com stable/non-free Sources
Hit http://repository.spotify.com stable/non-free amd64 Packages
Hit http://repository.spotify.com stable/non-free i386 Packages
Ign http://repository.spotify.com stable/non-free Translation-en_US
Ign http://repository.spotify.com stable/non-free Translation-en
Fetched 109 kB in 52s (2,096 B/s)
W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://mirror.steadfast.net/ubuntu/dists/precise-updates/Release.gpg  Something wicked happened resolving 'mirror.steadfast.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anupku/skull-wood-bones/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repo.steampowered.com/steam/dists/precise/Release.gpg  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/Release.gpg  Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)

W: Failed to fetch cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Check to make sure CDrom is **not** checked in 'Software Sources'

.[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by send2 on 2013-11-01
sorry ibjsb4, i used the wrong tags....any ideas on the solution to my query?

---

### Post by fantab on 2013-11-01
EDIT:Is your Precise regular Ubuntu or some Remix?

Post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by send2 on 2013-11-02
thanks for replying fantab. It is a regular version of precise. Here is the output of your command:

```
 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb cdrom:[Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)]/ dists/quantal/main/binary-i386/
deb cdrom:[Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)]/ dists/quantal/restricted/binary-i386/
deb http://archive.ubuntu.com/ubuntu precise main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu precise main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted multiverse
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://repository.spotify.com stable non-free
deb-src http://repository.spotify.com stable non-free

```

thanks for looking at it.

---

### Post by oldos2er on 2013-11-02
There are some suggestions on fixing the "something wicked happened" problem here: [http://askubuntu.com/questions/199541/solving-the-ubuntu-12-04-update-error-5-no-address-associated-with-hostname](http://askubuntu.com/questions/199541/solving-the-ubuntu-12-04-update-error-5-no-address-associated-with-hostname)

---

### Post by fantab on 2013-11-02
You will have to delete the following lines from /etc/apt/sources.list

> deb cdrom:[Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)]/ dists/quantal/main/binary-i386/
deb cdrom:[Ubuntu GNOME Remix 12.10 _Quantal Quetzal_ - Release i386(20121018)]/ dists/quantal/restricted/binary-i386/

You can open /etc/apt/sources.list with Gedit [Text-Editor] as root, like this:
```
gksu gedit /etc/apt/sources.list
```

Now find and DELETE the above lines. Save the file and close gedit.

Run
```
sudo apt-get update
```

If you still get errors, then post them here. But before you do that try to change the DNS and run 'apt-get update', see instructions on how to do it from the link in the above post.

---

### Post by send2 on 2013-11-02
Hi fantab and oldos2er: thanks for your help. I am still getting errors. Here is what came up after running sudo apt-get update as the final step:

```

Hit http://download.virtualbox.org precise Release.gpg
Hit http://download.virtualbox.org precise Release                             
Hit http://download.virtualbox.org precise/contrib amd64 Packages              
Hit http://download.virtualbox.org precise/contrib i386 Packages               
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Ign http://download.virtualbox.org precise/contrib Translation-en_US           
Ign http://download.virtualbox.org precise/contrib Translation-en              
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Get:2 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Err http://archive.ubuntu.com precise Release.gpg                              
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Hit http://archive.ubuntu.com precise-updates Release.gpg                      
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Hit http://archive.ubuntu.com precise-security Release.gpg                     
Hit http://archive.ubuntu.com precise Release                                  
Hit http://archive.ubuntu.com precise-updates Release                          
Hit http://archive.ubuntu.com precise-backports Release                        
Hit http://archive.ubuntu.com precise-security Release                         
Ign http://archive.ubuntu.com precise/main Sources/DiffIndex                   
Ign http://archive.ubuntu.com precise/restricted Sources/DiffIndex             
Ign http://archive.ubuntu.com precise/multiverse Sources/DiffIndex             
Ign http://archive.ubuntu.com precise/universe Sources/DiffIndex               
Ign http://archive.ubuntu.com precise/main amd64 Packages/DiffIndex            
Ign http://archive.ubuntu.com precise/restricted amd64 Packages/DiffIndex      
Ign http://archive.ubuntu.com precise/multiverse amd64 Packages/DiffIndex      
Ign http://archive.ubuntu.com precise/universe amd64 Packages/DiffIndex        
Ign http://archive.ubuntu.com precise/main i386 Packages/DiffIndex             
Ign http://archive.ubuntu.com precise/restricted i386 Packages/DiffIndex       
Ign http://archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex       
Ign http://archive.ubuntu.com precise/universe i386 Packages/DiffIndex         
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Hit http://archive.ubuntu.com precise-updates/main Sources                     
Hit http://archive.ubuntu.com precise-updates/restricted Sources               
Hit http://archive.ubuntu.com precise-updates/multiverse Sources               
Hit http://archive.ubuntu.com precise-updates/universe Sources                 
Hit http://archive.ubuntu.com precise-updates/main amd64 Packages              
Hit http://archive.ubuntu.com precise-updates/restricted amd64 Packages        
Hit http://archive.ubuntu.com precise-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com precise-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com precise-updates/main i386 Packages               
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages           
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages            
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages      
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages        
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages      
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise-security/main Sources                    
Hit http://archive.ubuntu.com precise-security/restricted Sources              
Hit http://archive.ubuntu.com precise-security/multiverse Sources              
Hit http://archive.ubuntu.com precise-security/universe Sources                
Hit http://archive.ubuntu.com precise-security/main amd64 Packages             
Hit http://archive.ubuntu.com precise-security/restricted amd64 Packages       
Hit http://archive.ubuntu.com precise-security/multiverse amd64 Packages       
Hit http://archive.ubuntu.com precise-security/universe amd64 Packages         
Hit http://archive.ubuntu.com precise-security/main i386 Packages              
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages        
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise-security/universe i386 Packages          
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Err http://repo.steampowered.com precise Release.gpg                           
  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)
Hit http://repo.steampowered.com precise Release                               
Ign http://repo.steampowered.com precise/steam Sources/DiffIndex               
Ign http://repo.steampowered.com precise/steam amd64 Packages/DiffIndex        
Ign http://repo.steampowered.com precise/steam i386 Packages/DiffIndex         
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Err http://repository.spotify.com stable Release.gpg                           
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://deb.opera.com stable Release.gpg                                    
  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com precise Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://dl.google.com stable Release.gpg                                    
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Hit http://dl.google.com stable Release                                        
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                  
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:3 https://private-ppa.launchpad.net precise/main TranslationIndex [364 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:4 https://private-ppa.launchpad.net precise/main TranslationIndex [362 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Ign http://extras.ubuntu.com precise Release                                   
Ign http://extras.ubuntu.com precise/main Sources/DiffIndex                    
Ign http://extras.ubuntu.com precise/main amd64 Packages/DiffIndex      
Ign http://extras.ubuntu.com precise/main i386 Packages/DiffIndex       
Ign http://extras.ubuntu.com precise/main TranslationIndex              
Hit http://extras.ubuntu.com precise/main Sources                       
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://repository.spotify.com stable Release                        
Ign http://repository.spotify.com stable/non-free Sources/DiffIndex     
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex
Ign http://repository.spotify.com stable/non-free TranslationIndex
Hit http://repository.spotify.com stable/non-free Sources
Hit http://repository.spotify.com stable/non-free amd64 Packages
Hit http://repository.spotify.com stable/non-free i386 Packages
Ign http://repository.spotify.com stable/non-free Translation-en_US
Ign http://repository.spotify.com stable/non-free Translation-en
Ign http://deb.opera.com stable Release
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex
Ign http://deb.opera.com stable/non-free TranslationIndex
Hit http://deb.opera.com stable/non-free amd64 Packages
Hit http://deb.opera.com stable/non-free i386 Packages
Ign http://deb.opera.com stable/non-free Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Fetched 632 B in 41s (15 B/s)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repo.steampowered.com/steam/dists/precise/Release.gpg  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

thanks again for looking at the code. I changed the DNS to google address 8.8.8.8, 8.8.4.4 and deleted the above lines from the sources.list

In addition to the above errors, I still can't download anything from the Ubuntu software center. The untrusted sources warning shows up every time I try to download something.

---

### Post by fantab on 2013-11-02
Try [OpenDNS]("http://www.opendns.com/home-solutions/"). Try change server in the 'software sources'. I have checked those addresses and they work on my side.

Try opening the links in the browser and see what happens.
> 
[http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)
[http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)
[http://repository.spotify.com/dists/stable/Release.gpg](http://repository.spotify.com/dists/stable/Release.gpg)
[http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)
[http://deb.opera.com/opera/dists/stable/Release.gpg](http://deb.opera.com/opera/dists/stable/Release.gpg)

---

### Post by send2 on 2013-11-02
Well looks like we are progressing somewhat. I used the OpenDNS address of 208.67.222.222, 208.67.220.220 in the settings and connected to the links that you gave me. Before, I could not connect to anything. Here is what I get when I ran sudo apt-get upgrade:

```
Get:1 http://download.virtualbox.org precise Release.gpg [198 B]               
Hit http://download.virtualbox.org precise Release                             
Hit http://download.virtualbox.org precise/contrib amd64 Packages              
Hit http://download.virtualbox.org precise/contrib i386 Packages               
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Ign http://download.virtualbox.org precise/contrib Translation-en_US           
Ign http://download.virtualbox.org precise/contrib Translation-en              
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:2 https://private-ppa.launchpad.net precise/main TranslationIndex [364 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Get:3 https://private-ppa.launchpad.net precise/main TranslationIndex [362 B]  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Err http://archive.ubuntu.com precise Release.gpg                              
  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
Get:4 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Hit http://archive.ubuntu.com precise-security Release.gpg                     
Hit http://archive.ubuntu.com precise Release                                  
Get:5 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Hit http://archive.ubuntu.com precise-backports Release                        
Hit http://archive.ubuntu.com precise-security Release                         
Ign http://archive.ubuntu.com precise/main Sources/DiffIndex                   
Ign http://archive.ubuntu.com precise/restricted Sources/DiffIndex             
Ign http://archive.ubuntu.com precise/multiverse Sources/DiffIndex             
Ign http://archive.ubuntu.com precise/universe Sources/DiffIndex               
Ign http://archive.ubuntu.com precise/main amd64 Packages/DiffIndex            
Ign http://archive.ubuntu.com precise/restricted amd64 Packages/DiffIndex      
Ign http://archive.ubuntu.com precise/multiverse amd64 Packages/DiffIndex      
Ign http://archive.ubuntu.com precise/universe amd64 Packages/DiffIndex        
Ign http://archive.ubuntu.com precise/main i386 Packages/DiffIndex             
Ign http://archive.ubuntu.com precise/restricted i386 Packages/DiffIndex       
Ign http://archive.ubuntu.com precise/multiverse i386 Packages/DiffIndex       
Ign http://archive.ubuntu.com precise/universe i386 Packages/DiffIndex         
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:6 http://archive.ubuntu.com precise-updates/main Sources [423 kB]          
Get:7 http://archive.ubuntu.com precise-updates/restricted Sources [7,006 B]   
Get:8 http://archive.ubuntu.com precise-updates/multiverse Sources [8,354 B]   
Get:9 http://archive.ubuntu.com precise-updates/universe Sources [98.8 kB]     
Get:10 http://archive.ubuntu.com precise-updates/main amd64 Packages [702 kB]  
Get:11 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [11.5 kB]
Get:12 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [14.0 kB]
Get:13 http://archive.ubuntu.com precise-updates/universe amd64 Packages [221 kB]
Get:14 http://archive.ubuntu.com precise-updates/main i386 Packages [722 kB]   
Get:15 http://archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]
Get:16 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [14.2 kB]
Get:17 http://archive.ubuntu.com precise-updates/universe i386 Packages [225 kB]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages            
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages      
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages        
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages      
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Hit http://archive.ubuntu.com precise-security/main Sources                    
Hit http://archive.ubuntu.com precise-security/restricted Sources              
Hit http://archive.ubuntu.com precise-security/multiverse Sources              
Hit http://archive.ubuntu.com precise-security/universe Sources                
Hit http://archive.ubuntu.com precise-security/main amd64 Packages             
Hit http://archive.ubuntu.com precise-security/restricted amd64 Packages       
Hit http://archive.ubuntu.com precise-security/multiverse amd64 Packages       
Hit http://archive.ubuntu.com precise-security/universe amd64 Packages         
Hit http://archive.ubuntu.com precise-security/main i386 Packages              
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages        
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com precise-security/universe i386 Packages          
Hit http://archive.ubuntu.com precise-security/main TranslationIndex           
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex       
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/main amd64 Packages                      
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                
Hit http://archive.ubuntu.com precise/universe amd64 Packages                  
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Hit http://archive.ubuntu.com precise-backports/main Translation-en            
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en      
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en      
Hit http://archive.ubuntu.com precise-backports/universe Translation-en        
Hit http://archive.ubuntu.com precise-security/main Translation-en             
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en       
Hit http://archive.ubuntu.com precise-security/restricted Translation-en       
Hit http://archive.ubuntu.com precise-security/universe Translation-en         
Err http://dl.google.com stable Release.gpg                                    
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Hit http://dl.google.com stable Release                                        
Ign http://dl.google.com stable/main amd64 Packages/DiffIndex                  
Ign http://dl.google.com stable/main i386 Packages/DiffIndex                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Err http://deb.opera.com stable Release.gpg                                    
  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Err http://repo.steampowered.com precise Release.gpg                           
  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)
Err http://extras.ubuntu.com precise Release.gpg                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://repository.spotify.com stable Release.gpg                           
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Hit http://repository.spotify.com stable Release                               
Ign http://repository.spotify.com stable/non-free Sources/DiffIndex            
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex     
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex      
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://repository.spotify.com stable/non-free Sources                      
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:18 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:19 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:20 http://ppa.launchpad.net precise Release [11.9 kB]                      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:21 http://ppa.launchpad.net precise Release [11.9 kB]                      
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:22 http://ppa.launchpad.net precise/main Sources [9,942 B]                 
Get:23 http://ppa.launchpad.net precise/main amd64 Packages [7,007 B]          
Get:24 http://ppa.launchpad.net precise/main i386 Packages [7,007 B]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:25 http://ppa.launchpad.net precise/main Sources [27.0 kB]                 
Get:26 http://ppa.launchpad.net precise/main amd64 Packages [16.6 kB]          
Get:27 http://ppa.launchpad.net precise/main i386 Packages [16.6 kB]           
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise Release                                   
Ign http://extras.ubuntu.com precise/main Sources/DiffIndex                    
Ign http://extras.ubuntu.com precise/main amd64 Packages/DiffIndex             
Ign http://extras.ubuntu.com precise/main i386 Packages/DiffIndex              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                
Ign http://deb.opera.com stable Release                                 
Ign http://deb.opera.com stable/non-free amd64 Packages/DiffIndex              
Ign http://deb.opera.com stable/non-free i386 Packages/DiffIndex               
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://repo.steampowered.com precise Release                               
Ign http://repo.steampowered.com precise/steam Sources/DiffIndex
Ign http://repo.steampowered.com precise/steam amd64 Packages/DiffIndex
Ign http://repo.steampowered.com precise/steam i386 Packages/DiffIndex
Ign http://repo.steampowered.com precise/steam TranslationIndex
Hit http://repo.steampowered.com precise/steam Sources
Hit http://repo.steampowered.com precise/steam amd64 Packages
Hit http://repo.steampowered.com precise/steam i386 Packages
Ign http://repo.steampowered.com precise/steam Translation-en_US
Ign http://repo.steampowered.com precise/steam Translation-en
Fetched 2,617 kB in 44s (58.7 kB/s)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anupku/skull-wood-bones/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repo.steampowered.com/steam/dists/precise/Release.gpg  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

From reading other posts, I think part of the problem is that I don't have the keys needed for some packages but I don't know yet how to proceed. I have never found keys to validate the security of packages before. But, I will defer to others who are more experienced than I am for sure!

This is kind of driving me nuts ](*,)! Thanks again for the help.

---

### Post by fantab on 2013-11-02
Do you have a 'proxy' set up?

Your's is a server problem. Nothing more. There seems to be some sort of connectivity/name resloution error. If nothing else it should go away by itself. Restart the computer, re-connect and try again.

---

### Post by hnf a on 2013-11-03
sorry if this isn't helping but maybe you can change source of the software center

---

### Post by send2 on 2013-11-03
Hi hnf a, i did change the source to a server close to me, hitting the recomend best server  that was close to me. Thanks for your help :D.

Hi fantab, no, I don't have a proxy. It seem like now I am able to download software from the software center and get updates for the system. Finally, what do I need to do with the following 5 no address associated with hostname errors:

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/anupku/skull-wood-bones/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release.gpg  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://repo.steampowered.com/steam/dists/precise/Release.gpg  Something wicked happened resolving 'repo.steampowered.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/Release.gpg  Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)

```

I think hopefully we are close to finalizing this problem. Let me know if I need to submit the question above as a new thread. I ask it here since it was at the end of the output of sudo get-apt update. After all this is done I will mark the thread as solved.

---

