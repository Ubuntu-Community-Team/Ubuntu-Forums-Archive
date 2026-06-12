---
title: "update icon always asks for checking packages"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by imgkg on 2008-09-15
my update icon is always on asking for checking  packages even tho i have checked it 3 times and there are no updates available

---

### Post by jken146 on 2008-09-15
Try opening a terminal (Applications -> Accessories -> Terminal) and typing ```
sudo apt-get update && sudo apt-get upgrade
```  Type in your password and press Enter when prompted.

---

### Post by imgkg on 2008-09-15
i have updated my repositories still it asks me for updating and showing packages are checked 7 days old infact i checked them 3 times and 4 th time with your command  > Err [http://ubuntu.geole.info](http://ubuntu.geole.info) hardy-backports/multiverse Sources                
  404 Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://phoebe.fiz.uni-lj.si](http://phoebe.fiz.uni-lj.si) hardy/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://mundogeek.net](http://mundogeek.net) ubuntu/all Packages                                   
Get:42 [ftp://ftp.berlios.de](ftp://ftp.berlios.de) ./ Translation-en_IN                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://debian.scribus.net](http://debian.scribus.net) hardy/main Sources                               
Hit [http://debian.scribus.net](http://debian.scribus.net) hardy/non-free Packages                          
Hit [http://debian.scribus.net](http://debian.scribus.net) hardy/non-free Sources                           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Hit [http://phoebe.fiz.uni-lj.si](http://phoebe.fiz.uni-lj.si) hardy/main Packages                            
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_IN               
Ign [ftp://ftp.berlios.de](ftp://ftp.berlios.de) ./ Translation-en_IN                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_IN                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/restricted Translation-en_IN                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Translation-en_IN                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/multiverse Translation-en_IN                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_IN                      
Err [http://www.bashterritory.com](http://www.bashterritory.com)  Release.gpg                                  
  Could not resolve 'www.bashterritory.com'
Err [http://www.bashterritory.com](http://www.bashterritory.com)  Translation-en_IN                            
  Could not resolve 'www.bashterritory.com'
Get:43 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://phoebe.fiz.uni-lj.si](http://phoebe.fiz.uni-lj.si) hardy/main Sources                             
Err [http://mundogeek.net](http://mundogeek.net) ubuntu/all Packages                                   
  404 Not Found
Get:45 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:47 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Get:48 [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy Release.gpg [189B]                     
Ign [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/main Translation-en_IN                    
Hit [http://debian.zaubberer.net](http://debian.zaubberer.net) ./ Release.gpg                                 
Ign [http://www.vollstreckernet.de](http://www.vollstreckernet.de) testing/amule Packages                       
Hit [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy Release.gpg                     
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Release.gpg           
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Get:49 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:50 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [ftp://ftp.berlios.de](ftp://ftp.berlios.de) ./ Release                                            
Get:51 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Hit [http://deb.opera.com](http://deb.opera.com) unstable/non-free Packages                            
Get:52 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:53 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                      
Get:54 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:55 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:56 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/restricted Translation-en_IN    
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy Release                                  
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates Release                          
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports Release                        
Get:57 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/universe Translation-en_IN                
Ign [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/multiverse Translation-en_IN              
Ign [http://debian.zaubberer.net](http://debian.zaubberer.net) ./ Translation-en_IN                           
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_IN                
Ign [http://download.skype.com](http://download.skype.com) stable Release                                   
Get:58 [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/blueman Sources [1109B]             
Get:59 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:60 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/multiverse Translation-en_IN            
Get:61 [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy Release [17.0kB]                       
Ign [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy Release                                   
Hit [ftp://ftp.berlios.de](ftp://ftp.berlios.de) ./ Packages                                           
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/main Packages                             
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/universe Translation-en_IN              
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/universe Packages                         
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/multiverse Packages                       
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/universe Translation-en_IN          
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/main Sources                              
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/universe Sources                          
Hit [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy/multiverse Sources                        
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages                         
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates Release.gpg                     
Get:62 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/multiverse Translation-en_IN        
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security Release.gpg                         
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/main Translation-en_IN              
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/restricted Translation-en_IN        
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/main Translation-en_IN          
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/universe Translation-en_IN          
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/multiverse Translation-en_IN        
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy Release                                      
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates Release                              
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed Release                             
Hit [http://www.vollstreckernet.de](http://www.vollstreckernet.de) testing/amule Packages                       
Ign [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy/pirate Translation-en_IN        
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Translation-en_IN     
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN    
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security Release                             
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Translation-en_IN                               
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/main Packages                                
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/restricted Packages                          
Get:63 [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release.gpg [189B]                      
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Translation-en_IN                     
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN    
Hit [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy Release                         
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Release               
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/universe Packages                            
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/multiverse Packages                          
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/main Packages                        
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/restricted Packages                  
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/universe Packages                    
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/multiverse Packages                  
Get:64 [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release [1929B]                         
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release                                    
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/main Packages                       
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/restricted Packages                 
Ign [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy/pirate Packages                 
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/universe Packages                   
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/multiverse Packages                 
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/main Packages                       
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security Release                         
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/universe Translation-en_IN      
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Release                                         
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Packages                              
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/restricted Packages                 
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/universe Packages                   
Ign [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/multiverse Packages                 
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/main Packages                                
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/restricted Packages                          
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/universe Packages                            
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/main Packages                            
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Sources                               
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/universe Packages                        
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy/multiverse Packages                          
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/main Packages                        
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/restricted Packages                  
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/universe Packages                    
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-updates/multiverse Packages                  
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed Release.gpg                    
Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Packages                              
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/multiverse Packages                      
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/restricted Packages                      
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/main Sources                             
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/universe Sources                         
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/multiverse Sources                       
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy/restricted Sources                       
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/main Packages                    
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/universe Packages                
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/multiverse Packages              
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/restricted Packages              
Ign [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Packages                                        
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/main Packages                       
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/restricted Packages                 
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/universe Packages                   
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-proposed/multiverse Packages                 
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/main Packages                       
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/restricted Packages                 
Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Sources                               
Hit [http://repository.cinnamonpirate.com](http://repository.cinnamonpirate.com) hardy/pirate Packages                 
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/main Sources                     
Get:65 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:66 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/main Translation-en_IN         
Get:67 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:68 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:69 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:70 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                         
Get:71 [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release [27.6kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/universe Packages                   
Hit [http://ddebs.ubuntu.com](http://ddebs.ubuntu.com) hardy-security/multiverse Packages                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/universe Sources                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/multiverse Sources               
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-updates/restricted Sources               
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/main Packages                  
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/universe Packages              
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/multiverse Packages            
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/restricted Packages            
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/main Sources                   
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/universe Sources               
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/multiverse Sources             
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-backports/restricted Sources             
Err [http://hydr0g3n.free.fr](http://hydr0g3n.free.fr) ./ Packages                                        
  404 Not Found
Get:72 [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/ Packages [9135B]                   
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/main Packages                   
Get:73 [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy/ Sources [2446B]                    
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/universe Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Get:74 [http://download.tuxfamily.org](http://download.tuxfamily.org) hardyTestBack/ Packages [1091B]           
Ign [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Packages              
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/multiverse Packages             
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/restricted Packages             
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/main Sources                    
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/universe Sources                
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/multiverse Sources              
Hit [http://ubuntu.uni-klu.ac.at](http://ubuntu.uni-klu.ac.at) hardy-security/restricted Sources              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/restricted Packages                         
Hit [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com) remastersys/ Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/multiverse Packages                         
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/restricted Translation-en_IN   
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_IN   
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/universe Translation-en_IN     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports Release.gpg                   
Ign [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) getdeb/ Release.gpg                              
Ign [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) getdeb/ Translation-en_IN                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/main Translation-en_IN        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/restricted Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/universe Packages                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/multiverse Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://debian.zaubberer.net](http://debian.zaubberer.net) ./ Release                                     
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/restricted Translation-en_IN  
Ign [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) getdeb/ Release                                  
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/universe Translation-en_IN    
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/multiverse Translation-en_IN  
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy Release                                 
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates Release                         
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed Release                        
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports Release                       
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/main Packages                           
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/multiverse Packages                     
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/universe Packages                       
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/main Sources                            
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/restricted Sources                      
Ign [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) getdeb/ Packages                                 
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/multiverse Sources                      
Err [http://mirrors.dotsrc.org](http://mirrors.dotsrc.org) getdeb/ Packages                                 
  404 Not Found
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy/universe Sources                        
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/multiverse Packages             
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/universe Packages               
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/multiverse Sources              
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-updates/universe Sources                
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/main Packages                  
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/restricted Packages            
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/multiverse Packages            
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/universe Packages              
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/main Sources                   
Err [http://www.ansemreport.com](http://www.ansemreport.com) hardy Release.gpg                               
  Could not resolve 'www.ansemreport.com'
Err [http://www.ansemreport.com](http://www.ansemreport.com) hardy/ports Translation-en_IN                   
  Could not resolve 'www.ansemreport.com'
Err [http://www.ansemreport.com](http://www.ansemreport.com) hardy/backports Translation-en_IN               
  Could not resolve 'www.ansemreport.com'
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/restricted Sources             
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/multiverse Sources             
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-proposed/universe Sources               
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/main Packages                 
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/restricted Packages           
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/universe Packages             
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/multiverse Packages           
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/main Sources                  
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/restricted Sources            
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/universe Sources              
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hardy-backports/multiverse Sources            
Hit [http://debian.zaubberer.net](http://debian.zaubberer.net) ./ Packages                                    
Hit [http://morgoth.free.fr](http://morgoth.free.fr) hardy-backports Release                             
Hit [http://morgoth.free.fr](http://morgoth.free.fr) hardy-backports/main Packages                       
Hit [http://morgoth.free.fr](http://morgoth.free.fr) hardy-backports/main Sources                        
Err [http://ubuntusatanic.org](http://ubuntusatanic.org) hardy Release.gpg                                 
  Could not connect to ubuntusatanic.org:80 (212.13.194.131), connection timed out
Err [http://ubuntusatanic.org](http://ubuntusatanic.org) hardy/main Translation-en_IN                      
  Unable to connect to ubuntusatanic.org http:
Err [http://uk.weeklybuilds.mythbuntu.org](http://uk.weeklybuilds.mythbuntu.org) hardy Release.gpg                     
  Could not connect to uk.weeklybuilds.mythbuntu.org:80 (212.13.194.26), connection timed out
Err [http://uk.weeklybuilds.mythbuntu.org](http://uk.weeklybuilds.mythbuntu.org) hardy/main Translation-en_IN
  Unable to connect to uk.weeklybuilds.mythbuntu.org http:
Fetched 28.5kB in 2min0s (236B/s)                                
Reading package lists... Done
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 050C2FB3F9E78789
W: GPG error: [http://cl.naist.jp](http://cl.naist.jp) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B8F0E6C98ABD1965
W: GPG error: [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB70C672B219D801
W: GPG error: [http://e17.dunnewind.net](http://e17.dunnewind.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 223020C2A7C6F0DF
W: GPG error: [http://ubuntu.jbbr.net](http://ubuntu.jbbr.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DEA651F25BB8FD99
W: GPG error: [http://debian.vakevainen.fi](http://debian.vakevainen.fi) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2BFAFC26585DECB0
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://moblock-deb.sourceforge.net](http://moblock-deb.sourceforge.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CB53C4079072870B
W: GPG error: [http://apt.wxwidgets.org](http://apt.wxwidgets.org) hardy-wx Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E0BCE7F53B087BC
W: GPG error: [http://debian.scribus.net](http://debian.scribus.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5BC4CFB8EEF818CF
W: GPG error: [http://phoebe.fiz.uni-lj.si](http://phoebe.fiz.uni-lj.si) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7C6E8805B6F22FBC
W: GPG error: [http://www.vollstreckernet.de](http://www.vollstreckernet.de) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D63913EF50D0AE60
W: GPG error: [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) hardy-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5
W: GPG error: [ftp://ftp.berlios.de](ftp://ftp.berlios.de) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 074D737EED75F599
W: GPG error: [http://apt.schmidtke-hb.de](http://apt.schmidtke-hb.de) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5B638EFECEAE2DE7
W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: Failed to fetch [http://ubuntusatanic.org/hell/dists/hardy/Release.gpg](http://ubuntusatanic.org/hell/dists/hardy/Release.gpg)  Could not connect to ubuntusatanic.org:80 (212.13.194.131), connection timed out

W: Failed to fetch [http://ubuntusatanic.org/hell/dists/hardy/main/i18n/Translation-en_IN.bz2](http://ubuntusatanic.org/hell/dists/hardy/main/i18n/Translation-en_IN.bz2)  Unable to connect to ubuntusatanic.org http:

W: Failed to fetch [http://www.bashterritory.com/pytube/releases/Release.gpg](http://www.bashterritory.com/pytube/releases/Release.gpg)  Could not resolve 'www.bashterritory.com'

W: Failed to fetch [http://www.bashterritory.com/pytube/releases/en_IN.bz2](http://www.bashterritory.com/pytube/releases/en_IN.bz2)  Could not resolve 'www.bashterritory.com'

W: Failed to fetch [http://www.ansemreport.com/uubp/dists/hardy/Release.gpg](http://www.ansemreport.com/uubp/dists/hardy/Release.gpg)  Could not resolve 'www.ansemreport.com'

W: Failed to fetch [http://www.ansemreport.com/uubp/dists/hardy/ports/i18n/Translation-en_IN.bz2](http://www.ansemreport.com/uubp/dists/hardy/ports/i18n/Translation-en_IN.bz2)  Could not resolve 'www.ansemreport.com'

W: Failed to fetch [http://www.ansemreport.com/uubp/dists/hardy/backports/i18n/Translation-en_IN.bz2](http://www.ansemreport.com/uubp/dists/hardy/backports/i18n/Translation-en_IN.bz2)  Could not resolve 'www.ansemreport.com'

W: Failed to fetch [http://uk.weeklybuilds.mythbuntu.org/mythbuntu/ubuntu/dists/hardy/Release.gpg](http://uk.weeklybuilds.mythbuntu.org/mythbuntu/ubuntu/dists/hardy/Release.gpg)  Could not connect to uk.weeklybuilds.mythbuntu.org:80 (212.13.194.26), connection timed out

W: Failed to fetch [http://uk.weeklybuilds.mythbuntu.org/mythbuntu/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2](http://uk.weeklybuilds.mythbuntu.org/mythbuntu/ubuntu/dists/hardy/main/i18n/Translation-en_IN.bz2)  Unable to connect to uk.weeklybuilds.mythbuntu.org http:

W: Failed to fetch [http://ubuntu.iuculano.it/dists/hardy/all/binary-i386/Packages.gz](http://ubuntu.iuculano.it/dists/hardy/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.iuculano.it/dists/hardy/all/source/Sources.gz](http://ubuntu.iuculano.it/dists/hardy/all/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://mirror.ubuntulinux.nl/dists/hardy-seveas/all/binary-i386/Packages.gz](http://mirror.ubuntulinux.nl/dists/hardy-seveas/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/Packages.gz](http://getswiftfox.com/builds/debian/dists/unstable/non-free/binary-i386/Packages.gz)  Error reading from server - read (104 Connection reset by peer)

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://mirror.ubuntulinux.nl/dists/hardy-seveas/all/source/Sources.gz](http://mirror.ubuntulinux.nl/dists/hardy-seveas/all/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy/universe/source/Sources.gz](http://ubuntu.geole.info/dists/hardy/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy/multiverse/source/Sources.gz](http://ubuntu.geole.info/dists/hardy/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/main/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/main/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/restricted/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/universe/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://ubuntu.geole.info/dists/hardy-backports/multiverse/source/Sources.gz](http://ubuntu.geole.info/dists/hardy-backports/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://www.logubuntu.it/M0rF3uS/dists/hardy/binary/binary-i386/Packages.gz](http://www.logubuntu.it/M0rF3uS/dists/hardy/binary/binary-i386/Packages.gz)  301 Moved Permanently

W: Failed to fetch [http://mundogeek.net/repo/dists/ubuntu/all/binary-i386/Packages.gz](http://mundogeek.net/repo/dists/ubuntu/all/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://hydr0g3n.free.fr/qbittorrent/hardy/./Packages.gz](http://hydr0g3n.free.fr/qbittorrent/hardy/./Packages.gz)  404 Not Found

W: Failed to fetch [http://mirrors.dotsrc.org/getdeb/Packages.gz](http://mirrors.dotsrc.org/getdeb/Packages.gz)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages (/var/lib/apt/lists/ppa.launchpad.net_stemp_ubuntu_dists_gutsy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:~$ 


---

### Post by imgkg on 2008-09-15
[IMG]http://i239.photobucket.com/albums/ff182/imgkg/Screenshot-UpdateManager.png[/IMG] in that screenshot it says i have checked it 7 days ago and a icon appears on my system tray to check package update infact i just checked all the packages still icon doesnt disappears and it doesnt says removes that i have checked it 7 days

---

### Post by philinux on 2008-09-15
Your sources list has a lot of weird stuff. Here's mine

 ```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://ubuntu.p2p-next.org/ hardy main
deb http://archive.ubuntu.com/ubuntu/ hardy-backports restricted main multiverse universe
```

---

### Post by imgkg on 2008-09-15
> #deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

####### Security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


####### Medibuntu
# wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

####### Wine
# gpg --keyserver subkeys.pgp.net --recv 387EE263
# gpg --export --armor 387EE263 | sudo apt-key add -
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main



####### Deluge
deb [http://ppa.launchpad.net/zachtib/ubuntu](http://ppa.launchpad.net/zachtib/ubuntu) hardy main universe
deb-src [http://ppa.launchpad.net/zachtib/ubuntu](http://ppa.launchpad.net/zachtib/ubuntu) hardy main universe

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

####### Dell
deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) hardy main

##### Amarok Nightly #####
deb [http://ppa.launchpad.net/maarten-fonville/ubuntu](http://ppa.launchpad.net/maarten-fonville/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/maarten-fonville/ubuntu](http://ppa.launchpad.net/maarten-fonville/ubuntu) hardy main

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free 

deb [http://ppa.launchpad.net/exaile-devel/ubuntu](http://ppa.launchpad.net/exaile-devel/ubuntu) hardy main




this is my actual source list its whatever there on internet 85% i guess keys can be updated but still its showing information checked 7 days ago

---

### Post by philinux on 2008-09-15
When you open the Update Manager it looks like it's checking for an update. The truth is you have to click check then enter your password for it to do a check.

---

