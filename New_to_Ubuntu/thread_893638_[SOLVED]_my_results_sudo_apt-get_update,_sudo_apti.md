---
title: "[SOLVED] my results sudo apt-get update, sudo aptitude update why different"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by brucegriffin on 2008-08-18
I'm new to ubuntu and wonder why the results when I do a sudo apt-get update seems not to be working as the results I get at the end of the update seems to have one e entry and two w entries, I get the same entries when I do a reload at synaptics. If I do a sudo aptitude update the entries seem ok. Is there something I can do to correct this. Below are the results of both.  Did the best I could trying to put codes to differentiate the text but don't know just how to do it properly yet sry.




```
[CODE][HTML][HTML]sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg  sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg          
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packagessudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg          
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg          
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update casudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg          
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead


____________________________________________________________________________



 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardnnot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.





 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardTranslation-en_US               
Ign http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_US         
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg          
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.





 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hard
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.





 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hard
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.





[CODE][CODE] sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardTranslation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg          
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.





 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hard        
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardTranslation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]             
Hit http://packages.medibuntu.org hardy Release.gpg                  
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg          
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.





 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hard        
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US     
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com hardy/partner Packages                        
Hit http://us.archive.ubuntu.com hardy Release                       
Hit http://us.archive.ubuntu.com hardy-updates Release               
Hit http://us.archive.ubuntu.com hardy-security Release                        
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Fetched 1B in 1s (1B/s)
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.




[/HTML][/HTML]
```[/CODE]
 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US          
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 1B in 3s (0B/s)  
Reading package lists... Done








____________________________________________________________________________


[/HTML][/HTML][/CODE][/CODE]
 sudo aptitude update
[sudo] password for dasleyefox: 
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                              
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release.gpg                     
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Translation-en_US          
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 1B in 3s (0B/s)  
Reading package lists... Done







[/CODE][/CODE]

---

### Post by philinux on 2008-08-18
Use this code.

cat /etc/apt/sources.list

Post the results.

---

### Post by Elfy on 2008-08-18
Try removing the cdrom from the sources - software sources in System > admin menu and try again. They should be more or less the same I think.

To put in a code box
[noparse]```
[/noparse] at beginning and [noparse]
```[/noparse] at the end.

To put in a quote box

[noparse]> [/noparse] at beginning and [noparse][/noparse] at the end.

There's more - [http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219) - look at BB code page

---

### Post by ibuclaw on 2008-08-18
eh?

What do you mean?

apt-get and aptitude are both slightly different apps, although they carry out pretty much the same jobs, don't expect them to do the exact same things/print the exact same output.

But, back to your real problem. You have the CD-ROM sources enabled. This should be commented out.

Regards
Iain

---

### Post by brucegriffin on 2008-08-18
Thanks for your replies, and answers about using the code and quote. tinivole, can you tell me how to disable the cd-rom sources or as you said commented out.

---

### Post by Elfy on 2008-08-18
Once you've opened software sources - near bottom there is a cdrom box, click to remove the tick.

---

### Post by brucegriffin on 2008-08-18
Thank You Pixie, problem solved.

---

