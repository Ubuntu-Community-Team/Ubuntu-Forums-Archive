---
title: "updates fail a lot. sometimes always"
date: 2014-09-12
forum: New to Ubuntu
---

### Post by gnowair on 2014-09-12
via the red road "stop/no entry" loga on panel, i get this epic fail:

```
"W:GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139, W:GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366, W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs, W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead"

and via terminal:

"root@paul-home:/home/paul# apt-get update
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty InRelease
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty Release.gpg
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty Release
Err cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted amd64 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-en_GB
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-en_GB
Ign cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417) trusty/restricted Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease                              
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main amd64 Packages                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main i386 Packages                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed InRelease                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable InRelease                           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg                            
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) trusty InRelease [5,637 B]                
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty InRelease                                 
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable Release.gpg                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed Release.gpg                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable Release                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release                        
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main amd64 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Ign [http://download.virtualbox.org](http://download.virtualbox.org) trusty InRelease                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable/free amd64 Packages                 
Hit [http://deb.torproject.org](http://deb.torproject.org) trusty/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid InRelease                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources                           
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en_GB                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid InRelease                                   
Ign [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib amd64 Packages/DiffIndex     
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Sources                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                     
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable/non-free amd64 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Get:2 [https://download.01.org](https://download.01.org) trusty InRelease                                 
Ign [https://download.01.org](https://download.01.org) trusty InRelease                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main amd64 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid InRelease                                   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Ign [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib i386 Packages/DiffIndex      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable/free i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe amd64 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable/non-free i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Get:3 [https://download.01.org](https://download.01.org) trusty/main amd64 Packages/DiffIndex             
Ign [https://download.01.org](https://download.01.org) trusty/main amd64 Packages/DiffIndex               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable/free Translation-en                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe i386 Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en_GB                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [https://download.01.org](https://download.01.org) trusty/main i386 Packages/DiffIndex                
Hit [http://kxstudio.sourceforge.net](http://kxstudio.sourceforge.net) stable/non-free Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib amd64 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en_GB           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en_GB           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en_GB             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en_GB                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Ign [http://deb.torproject.org](http://deb.torproject.org) trusty/main Translation-en                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib Translation-en_GB  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://download.virtualbox.org](http://download.virtualbox.org) trusty/contrib Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main i386 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/main Translation-en 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/main amd64 Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/restricted amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/universe amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/multiverse amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/main i386 Packages   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/restricted i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/main Translation-en  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/restricted Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/restricted Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/universe Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-proposed/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [https://download.01.org](https://download.01.org) trusty/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [https://download.01.org](https://download.01.org) trusty/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:4 [https://download.01.org](https://download.01.org) trusty/main Translation-en_GB                    
Ign [https://download.01.org](https://download.01.org) trusty/main Translation-en_GB                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [https://download.01.org](https://download.01.org) trusty/main Translation-en                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Fetched 9,306 B in 17s (540 B/s)
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
W: GPG error: [https://download.01.org](https://download.01.org) trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead." 
```

does this mean i have to make or virtualize a disc?

 i've had many notifications the past few days to upgrade flash, but it fails, and a few other packages that seem to update around same time/session which likewise fail.

any advice?
thanks muchilly!

---

### Post by gnowair on 2014-09-12
further:
when prompted to update today
i was advised to switch off untrusted packages, and run apt-get install f (was in regards to a tor package in particular)

paul@paul-home:~$ sudo apt-get install -f
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libjreen1 libqtweetlib1.0 linux-image-3.13.0-32-lowlatency
  linux-image-3.13.0-34-generic linux-image-3.13.0-34-lowlatency
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-34-generic
  linux-image-extra-3.13.0-35-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tor
Suggested packages:
  mixmaster xul-ext-torbutton socat tor-arm apparmor-utils
The following NEW packages will be installed
  tor
0 to upgrade, 1 to newly install, 0 to remove and 34 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/807 kB of archives.
After this operation, 2,573 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 559886 files and directories currently installed.)
Preparing to unpack .../tor_0.2.4.23-2~trusty+1_amd64.deb ...
Unpacking tor (0.2.4.23-2~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Frogs Hair on 2014-09-12
The PPA listed at the top of the output has no packages  for 14.04.

[https://launchpad.net/~fyrmir/+archive/ubuntu/livewallpaper-stable](https://launchpad.net/~fyrmir/+archive/ubuntu/livewallpaper-stable)
```
 W:Failed to fetch [http://ppa.launchpad.net/fyrmir/live...source/Sources]("http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/source/Sources")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/fyrmir/live...amd64/Packages]("http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-amd64/Packages")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/fyrmir/live...-i386/Packages]("http://ppa.launchpad.net/fyrmir/livewallpaper-stable/ubuntu/dists/trusty/main/binary-i386/Packages")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audi...source/Sources]("http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/source/Sources")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audi...amd64/Packages]("http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages")  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-audi...-i386/Packages]("http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages")  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead"[COLOR=#222222][FONT=Verdana]
``` 
Removing the source from Software & Updates > Other Software should remove that error.[/FONT][/COLOR]

---

### Post by Elfy on 2014-09-12
disable the cd in the same place and the ubuntu-audio-dev/ppa - that's not got anything newer than raring

---

### Post by gnowair on 2014-09-12
> **Elfy said:**
> disable the cd in the same place and the ubuntu-audio-dev/ppa - that's not got anything newer than raring

> **Elfy said:**
> disable the cd in the same place and the ubuntu-audio-dev/ppa - that's not got anything newer than raring

hey elfy!! i love the "pot-head-pixie" there! guess you've been "gong a long time|"!

i'm not toio sure what any of this means guys.
i'm still a bit wet behind the ears with ubuntu.

oh!

it may not be related, (although i do understand when frogs hair says that thjose thing-ummies dont exist, so i'm perhaps now on a slightly different tack,but today i keep getting a notification asking to click "repair" for a broken package (tor-geopdn?), which auto loads the software centre, asks me to input password, (as u would expect), then i get this result:

"nstallArchives() failed: (Reading database ... (Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 559886 files and directories currently installed.)
Preparing to unpack .../tor_0.2.4.23-2~trusty+1_amd64.deb ...
Unpacking tor (0.2.4.23-2~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb
Error in function: 
dpkg: dependency problems prevent configuration of tor-geoipdb:
 tor-geoipdb depends on tor (>= 0.2.4.23-2~trusty+1); however:
  Package tor is not installed.


dpkg: error processing package tor-geoipdb (--configure):
 dependency problems - leaving unconfigured"

i've another thread posted today, and i've a more than niggling feeling it is very connected to this particular part of my update/install hassle here. (altho the above reply by frog hair would not be related at all,i guess?)

(p.s. i've a bit of an adult hyper-activity "disorder" so i can be prone to unintended rants, and very rushed spelling/writing. it's best not to take offense, just gently ask me to stick to the point, i promise i'll "get it", thank you all very kindly!!!!)

---

### Post by Frogs Hair on 2014-09-12
Post the output of the following command. ```
cat /etc/apt/sources.list
```

---

### Post by claracc on 2014-09-13
Also, you have lucid repositories in your /etc/apt/sources.list as the errors indicate:

```
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages            
```

You have to remove this repository ppa.launchpad.net lucid in your /etc/apt/sources.list file or write a # sign in the beginning of the line.

---

### Post by gnowair on 2014-09-15
> **Frogs Hair said:**
> Post the output of the following command. ```
cat /etc/apt/sources.list
```

thanks for the help!
the output of the above command is:

~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) trusty contrib
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-proposed main restricted universe multiverse
deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) trusty main
# deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) trusty main
# deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) trusty main

---

### Post by gnowair on 2014-09-15
> **claracc said:**
> Also, you have lucid repositories in your /etc/apt/sources.list as the errors indicate:

```
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main amd64 Packages                         
Hit http://ppa.launchpad.net lucid/main i386 Packages            
```

You have to remove this repository ppa.launchpad.net lucid in your /etc/apt/sources.list file or write a # sign in the beginning of the line.


i understand exactly what your meaning here. however i dont know how to perform this task.
u mean in my usr bin folder? each line like the ones above? and/or rename as they are but with "#" at beginning of each line?
thank you kindly

---

### Post by grahammechanical on 2014-09-15
Go to System Settings>Software and Updates>Other Software tab and there you will find lines for those PPAs. Untick the boxes or select them and click Remove and then run Check or Update as requested.

Regards

---

### Post by gnowair on 2014-09-24
yep. i seem to be running updates extremely well now.
all of the advice above both educated and fixed the issue.
and grahamechanicals suggestion directly above this comment solved the remainer.
fantastic.
a big SOLVED!!

---

