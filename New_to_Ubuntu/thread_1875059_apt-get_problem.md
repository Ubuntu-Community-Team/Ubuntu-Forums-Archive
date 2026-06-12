---
title: "apt-get problem"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by eklikeroomys on 2011-11-04
Halo,

I'm having trouble getting my apt-get to work. When I try to update my package list, I keep getting errors from (it seems like) the same repositories. I am using Ubuntu 10.10 at work and would like to keep my system updated. We currently have no firewall or proxy server, which I thought could have been blocking access to the repositories. Also, I have no problem with internet browsing via firefox. The last thing that I think may be a problem is that I have to specify my IP and Gateway, and two DNS servers in the network manager. do I somehow have to specify these for apt-get as well?

I dont really have any knowledge of servers so help would be appreciated. Below is the output when I run sudo apt-get update:

```
Err ftp://extras.ubuntu.com maverick Release.gpg                                                                                                                                                              
  Server closed the connection
Hit http://ubuntu.mirror.ac.za maverick Release.gpg                                                                                                                                                           
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/main Translation-en                                                                                                                                   
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/main Translation-en_ZA                                                                                                                                
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/multiverse Translation-en                                                                                                                             
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/multiverse Translation-en_ZA                                                                                                                          
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/restricted Translation-en                                                                                                                             
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/restricted Translation-en_ZA                                                                                                                          
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/universe Translation-en                                                                                                                               
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick/universe Translation-en_ZA                                                                                                                            
Hit http://ubuntu.mirror.ac.za maverick-security Release.gpg                                                                                                                                                  
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/main Translation-en                                                                                                                          
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/main Translation-en_ZA                                                                                                                       
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/multiverse Translation-en                                                                                                                    
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/multiverse Translation-en_ZA                                                                                                                 
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/restricted Translation-en                                                                                                                    
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/restricted Translation-en_ZA                                                                                                                 
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/universe Translation-en                                                                                                                      
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-security/universe Translation-en_ZA                                                                                                                   
Hit http://ubuntu.mirror.ac.za maverick-updates Release.gpg                                                                                                                                                   
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/main Translation-en                                                                                                                           
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/main Translation-en_ZA                                                                                                                        
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/multiverse Translation-en                                                                                                                     
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/multiverse Translation-en_ZA                                                                                                                  
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/restricted Translation-en                                                                                                                     
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/restricted Translation-en_ZA                                                                                                                  
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/universe Translation-en                                                                                                                       
Ign http://ubuntu.mirror.ac.za/ubuntu-archive/ maverick-updates/universe Translation-en_ZA                                                                                                                    
Hit http://ubuntu.mirror.ac.za maverick Release                                                                                                                                                               
Hit http://ubuntu.mirror.ac.za maverick-security Release                                                                                                                                                      
Hit http://ubuntu.mirror.ac.za maverick-updates Release                                                                                                                                                       
Hit http://ubuntu.mirror.ac.za maverick/main i386 Packages                                                                                                                                                    
Err ftp://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                                                                              
  Server closed the connection
Hit http://ubuntu.mirror.ac.za maverick/universe i386 Packages                                                                                                                                                
Hit http://ubuntu.mirror.ac.za maverick/restricted i386 Packages                                                                                                                                  
Hit http://ubuntu.mirror.ac.za maverick/multiverse i386 Packages                                                                                                                
Hit http://ubuntu.mirror.ac.za maverick-security/universe i386 Packages                                                                                                         
Hit http://ubuntu.mirror.ac.za maverick-security/main i386 Packages                                                                                                             
Hit http://ubuntu.mirror.ac.za maverick-security/multiverse i386 Packages                                                                                 
Hit http://ubuntu.mirror.ac.za maverick-security/restricted i386 Packages                                                                                 
Hit http://ubuntu.mirror.ac.za maverick-updates/universe i386 Packages                                                                                    
Hit http://ubuntu.mirror.ac.za maverick-updates/main i386 Packages                                                                                        
Hit http://ubuntu.mirror.ac.za maverick-updates/multiverse i386 Packages                                                                                  
Hit http://ubuntu.mirror.ac.za maverick-updates/restricted i386 Packages                                                                                  
Err ftp://archive.canonical.com maverick Release.gpg                                                                                                      
  Server closed the connection
Hit http://archive.canonical.com maverick Release.gpg                                                                                                     
Ign http://archive.canonical.com/ maverick/partner Translation-en                                                                            
Hit http://repos.knowledgetree.com knowledgetree-ce Release.gpg                                         
Ign http://repos.knowledgetree.com/deb/knowledgetree/ knowledgetree-ce/main Translation-en              
Ign http://repos.knowledgetree.com/deb/knowledgetree/ knowledgetree-ce/main Translation-en_ZA           
Err ftp://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_ZA                                     
  Server closed the connection
Ign http://archive.canonical.com/ maverick/partner Translation-en_ZA                                             
Hit http://archive.canonical.com maverick Release                                                                             
Err ftp://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                       
  Server closed the connection
Hit http://repos.knowledgetree.com knowledgetree-ce Release                                                      
Hit http://archive.canonical.com maverick/partner i386 Packages                                                               
Ign ftp://extras.ubuntu.com maverick Release                                                            
Err ftp://archive.canonical.com/ubuntu/ maverick/partner Translation-en_ZA                              
  Server closed the connection
Ign http://repos.knowledgetree.com knowledgetree-ce/main i386 Packages                     
Ign http://ppa.launchpad.net **DISTRIBUTION** Release.gpg                                  
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ **DISTRIBUTION**/main Translation-en
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ **DISTRIBUTION**/main Translation-en_ZA
Ign ftp://extras.ubuntu.com maverick/main Sources/DiffIndex                       
Ign http://repos.knowledgetree.com knowledgetree-ce/main i386 Packages                     
Ign ftp://archive.canonical.com maverick Release                                           
Ign ftp://extras.ubuntu.com maverick/main i386 Packages/DiffIndex                          
Hit http://repos.knowledgetree.com knowledgetree-ce/main i386 Packages                     
Ign ftp://archive.canonical.com maverick/partner Sources/DiffIndex                         
Ign ftp://extras.ubuntu.com maverick/main Sources                                 
Ign ftp://archive.canonical.com maverick/partner i386 Packages/DiffIndex
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_ZA
Hit http://ppa.launchpad.net maverick Release.gpg                    
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_ZA
Hit http://ppa.launchpad.net maverick Release.gpg           
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ maverick/main Translation-en   
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ maverick/main Translation-en_ZA
Hit http://ppa.launchpad.net maverick Release.gpg                                 
Ign ftp://extras.ubuntu.com maverick/main i386 Packages                           
Ign ftp://archive.canonical.com maverick/partner Sources                          
Ign ftp://extras.ubuntu.com maverick/main Sources                    
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_ZA
Ign http://ppa.launchpad.net **DISTRIBUTION** Release       
Hit http://ppa.launchpad.net maverick Release               
Hit http://ppa.launchpad.net maverick Release                                                           
Ign ftp://archive.canonical.com maverick/partner i386 Packages                                          
Ign ftp://extras.ubuntu.com maverick/main i386 Packages                                                 
Ign ftp://archive.canonical.com maverick/partner Sources                          
Hit http://ppa.launchpad.net maverick Release                        
Err ftp://extras.ubuntu.com maverick/main Sources                                                       
  Server closed the connection
Ign ftp://archive.canonical.com maverick/partner i386 Packages                    
Err ftp://extras.ubuntu.com maverick/main i386 Packages              
  Server closed the connection
Err ftp://archive.canonical.com maverick/partner Sources                            
  Server closed the connection
Hit http://ppa.launchpad.net maverick Release                                       
Ign http://ppa.launchpad.net **DISTRIBUTION**/main i386 Packages                  
Hit http://repos.zend.com server Release.gpg                                      
Ign http://repos.zend.com/zend-server/deb/ server/non-free Translation-en
Err ftp://archive.canonical.com maverick/partner i386 Packages
  Server closed the connection
Ign http://repos.zend.com/zend-server/deb/ server/non-free Translation-en_ZA
Hit http://repos.zend.com server Release       
Hit http://repos.zend.com server/non-free i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Ign http://ppa.launchpad.net **DISTRIBUTION**/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net **DISTRIBUTION**/main i386 Packages
  404  Not Found
W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_ZA.bz2  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_ZA.bz2  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  Server closed the connection

W: Failed to fetch http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/dists/**DISTRIBUTION**/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead. 
```

---

### Post by BillyBoa on 2011-11-04
Try to change (from your software sources) your Ubuntu server. Maybe the main server is not working well.

---

### Post by eklikeroomys on 2011-11-04
BillyBoa, I have made Ubuntu automatically select the best server, but I still get the same results.

Thank you

---

### Post by eklikeroomys on 2011-11-04
There seems to be a lot of similar problems with apt-get, is there no fix for this?

---

### Post by sadaruwan12 on 2011-11-04
It's seems like the best server is refusing you did you tried to change the server to the canonical main what happens when you do that.

---

### Post by eklikeroomys on 2011-11-07
Halo, I changed the server to Main from USC --> Edit --> Software Sources, the problem still seems to be the same, this is the output that I get:

```
Err ftp://extras.ubuntu.com maverick Release.gpg
  Server closed the connection
Err ftp://archive.canonical.com maverick Release.gpg                                                                                                                                                         
  Server closed the connection
Hit http://archive.canonical.com maverick Release.gpg                                                                                                                                                        
Ign http://archive.canonical.com/ maverick/partner Translation-en                                                                                                                                            
Ign http://archive.canonical.com/ maverick/partner Translation-en_ZA                                                                                               
Err ftp://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                                   
  Server closed the connection
Err ftp://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                                                            
  Server closed the connection
Hit http://archive.ubuntu.com maverick Release.gpg                                                                           
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                           
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_ZA                                                                     
Ign http://ppa.launchpad.net **DISTRIBUTION** Release.gpg                                                                                 
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ **DISTRIBUTION**/main Translation-en                                                    
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ **DISTRIBUTION**/main Translation-en_ZA                                                 
Hit http://repos.knowledgetree.com knowledgetree-ce Release.gpg                                                                            
Ign http://repos.knowledgetree.com/deb/knowledgetree/ knowledgetree-ce/main Translation-en                                                 
Ign http://repos.knowledgetree.com/deb/knowledgetree/ knowledgetree-ce/main Translation-en_ZA                                              
Hit http://archive.canonical.com maverick Release                                                                                          
Err ftp://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_ZA                                                                        
  Server closed the connection
Err ftp://archive.canonical.com/ubuntu/ maverick/partner Translation-en_ZA                                                                 
  Server closed the connection
Hit http://repos.zend.com server Release.gpg                                                                                  
Ign http://repos.zend.com/zend-server/deb/ server/non-free Translation-en                                                                  
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                   
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_ZA                                          
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_ZA                                          
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                               
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_ZA                                            
Hit http://archive.ubuntu.com maverick-security Release.gpg                                                          
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                                
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_ZA                                                             
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                          
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                          
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en                                       
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_ZA                                    
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                          
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en                                        
Ign http://ppa.launchpad.net/flozz/flozz/ubuntu/ maverick/main Translation-en_ZA                                     
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                          
Ign http://repos.zend.com/zend-server/deb/ server/non-free Translation-en_ZA                                                               
Hit http://archive.canonical.com maverick/partner i386 Packages                                                                            
Ign ftp://extras.ubuntu.com maverick Release                                                                         
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ maverick/main Translation-en                                      
Ign ftp://archive.canonical.com maverick Release                                                                     
Ign http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/ maverick/main Translation-en_ZA                                   
Hit http://ppa.launchpad.net maverick Release.gpg                                                       
Hit http://repos.knowledgetree.com knowledgetree-ce Release                                                          
Hit http://repos.zend.com server Release                                                                             
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_ZA                                 
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en              
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_ZA           
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_ZA             
Hit http://archive.ubuntu.com maverick-updates Release.gpg                                     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                     
Ign ftp://extras.ubuntu.com maverick/main Sources/DiffIndex                                    
Ign ftp://archive.canonical.com maverick/partner Sources/DiffIndex                                      
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en                       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_ZA                                 
Ign http://ppa.launchpad.net **DISTRIBUTION** Release                                                                
Hit http://ppa.launchpad.net maverick Release                                                  
Hit http://ppa.launchpad.net maverick Release                                                                                              
Hit http://repos.zend.com server/non-free i386 Packages                                                                                    
Ign http://repos.knowledgetree.com knowledgetree-ce/main i386 Packages                                                                     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_ZA                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en               
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_ZA            
Ign ftp://extras.ubuntu.com maverick/main i386 Packages/DiffIndex                              
Ign ftp://archive.canonical.com maverick/partner i386 Packages/DiffIndex                       
Hit http://ppa.launchpad.net maverick Release                                     
Ign http://repos.knowledgetree.com knowledgetree-ce/main i386 Packages                                               
Ign ftp://extras.ubuntu.com maverick/main Sources                                              
Ign ftp://archive.canonical.com maverick/partner Sources                          
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_ZA            
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_ZA              
Hit http://archive.ubuntu.com maverick Release                                                 
Hit http://archive.ubuntu.com maverick-security Release                                                              
Hit http://archive.ubuntu.com maverick-updates Release                                                               
Hit http://ppa.launchpad.net maverick Release                                                                        
Ign http://ppa.launchpad.net **DISTRIBUTION**/main i386 Packages                                                     
Ign ftp://extras.ubuntu.com maverick/main i386 Packages                                                              
Ign ftp://archive.canonical.com maverick/partner i386 Packages                                 
Hit http://repos.knowledgetree.com knowledgetree-ce/main i386 Packages            
Hit http://archive.ubuntu.com maverick/main i386 Packages                         
Ign ftp://extras.ubuntu.com maverick/main Sources                        
Ign ftp://archive.canonical.com maverick/partner Sources    
Hit http://ppa.launchpad.net maverick/main Sources          
Hit http://ppa.launchpad.net maverick/main i386 Packages                 
Hit http://ppa.launchpad.net maverick/main Sources                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                 
Hit http://archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.ubuntu.com maverick/restricted i386 Packages
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages
Ign ftp://extras.ubuntu.com maverick/main i386 Packages
Hit http://archive.ubuntu.com maverick-security/main i386 Packages
Ign ftp://archive.canonical.com maverick/partner i386 Packages
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages 
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages    
Hit http://ppa.launchpad.net maverick/main Sources                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                 
Err ftp://extras.ubuntu.com maverick/main Sources  
  Server closed the connection
Err ftp://archive.canonical.com maverick/partner Sources    
  Server closed the connection
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages  
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages  
Ign http://ppa.launchpad.net **DISTRIBUTION**/main i386 Packages
Err ftp://extras.ubuntu.com maverick/main i386 Packages
  Server closed the connection
Err ftp://archive.canonical.com maverick/partner i386 Packages
  Server closed the connection
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Err http://ppa.launchpad.net **DISTRIBUTION**/main i386 Packages
  404  Not Found
W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/Release.gpg  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_ZA.bz2  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_ZA.bz2  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz  Server closed the connection

W: Failed to fetch ftp://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Server closed the connection

W: Failed to fetch ftp://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz  Server closed the connection

W: Failed to fetch http://ppa.launchpad.net/rabbitvcs/ppa/ubuntu/dists/**DISTRIBUTION**/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

