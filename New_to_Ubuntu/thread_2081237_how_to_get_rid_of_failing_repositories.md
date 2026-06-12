---
title: "how to get rid of failing repositories"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by aravind4j on 2012-11-06
hey
 i'm using ubuntu 12.10 
i'm having trouble updating my system 
i'm seeing the following error when i check for updates 

```
W:Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/universe/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/universe/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]
, W:Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/main/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/main/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]
, W:Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]
, W:Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

i have tried disabling the maverick updates and then even removed all the mentioned maverick  update address from the sources but even then i'm getting the above  errors

when i use terminal to check for updates it shows the following 
```

Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/main Translation-en
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2) quantal/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports InRelease                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release                    
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates InRelease                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Sources               
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Sources         
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages                                                                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Sources                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Sources                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Sources                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Sources                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages                                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_US                                              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages [25.0 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en                           
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages [14 B]                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en                                                                                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en                                                                                                                                         
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Sources [14 B]                                                                                                                                    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Sources [7,679 B]                                                                                                                                       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Sources [14 B]                                                                                                                                    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Sources [1,457 B]                                                                                                                                   
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main i386 Packages [31.0 kB]                                                                                                                                 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted i386 Packages [14 B]                                                                                                                              
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe i386 Packages [6,137 B]                                                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Translation-en_US                                                                                                                                    
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse i386 Packages [14 B]                                                                                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Translation-en                                                                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Translation-en_US                                                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en                                                                                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Translation-en                                                                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Translation-en_US                                                                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en                                                                                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Translation-en                                                                                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Translation-en_US                                                                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en                                                                                                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Translation-en                                                                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en                                                                                                                                        
Err [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/universe i386 Packages                                                                                                                                        
  404  Not Found [IP: 203.34.118.132 80]
Err [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/main i386 Packages                                                                                                                                            
  404  Not Found [IP: 203.34.118.132 80]
Err [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/multiverse i386 Packages                                                                                                                                      
  404  Not Found [IP: 203.34.118.132 80]
Err [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/restricted i386 Packages                                                                                                                                      
  404  Not Found [IP: 203.34.118.132 80]
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/main Translation-en_US                                                                                                                                        
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/main Translation-en                                                                                                                                           
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/multiverse Translation-en_US                                                                                                                                  
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/multiverse Translation-en                                                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Translation-en_US                                                                                                                                       
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/restricted Translation-en_US                                                                                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Translation-en                                                                                                                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Translation-en_US                                                                                                                                 
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/restricted Translation-en                                                                                                                                     
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/universe Translation-en_US                                                                                                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Translation-en                                                                                                                                    
Ign [http://ubuntu.idrepo.or.id](http://ubuntu.idrepo.or.id) maverick-updates/universe Translation-en                                                                                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Translation-en_US                                                                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Translation-en                                                                                                                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Translation-en_US                                                                                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Translation-en                                                                                                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US                                                                                                                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US                                                                                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US                                                                                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US                                                                                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US                                                                                                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en_US
Fetched 71.3 kB in 31s (2,231 B/s)
W: Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/universe/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/universe/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]

W: Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/main/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/main/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]

W: Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]

W: Failed to fetch [http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages](http://ubuntu.idrepo.or.id/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 203.34.118.132 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

HELP NEEDED :(
i'm just starting to use linux so please state "how to do's" elaborately
i'd be thankful if someway i could get rid of the above error :)

---

### Post by PowerBarry43 on 2012-11-06
Hi
 
You can edit repositories by changing the /etc/apt/sources.list file.
 
to do so run
 
```
gksu gedit /etc/apt/sources.list
```
 
remove the lines containing the failed repos and run apt-get update again. they should be gone
 
Hope this helps!!
 
Barry

---

### Post by black veils on 2012-11-06
or you could delete the contents of that file and paste in the results from creating your own **[here]("http://repogen.simplylinux.ch/")**

---

### Post by aravind4j on 2012-11-06
> **PowerBarry43 said:**
> Hi
 
You can edit repositories by changing the /etc/apt/sources.list file.
 
to do so run
 
```
gksu gedit /etc/apt/sources.list
```remove the lines containing the failed repos and run apt-get update again. they should be gone
 
Hope this helps!!
 
Barry


hey thanks :)
i was able to remove maverick repos but i kind of run into some other problem 
here it goes 

[B]Reading package lists... Done
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-updates/restricted i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_quantal-updates_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

[/B]i did run the update from terminal again only to get the same result again :confused:

---

### Post by aravind4j on 2012-11-06
> **black veils said:**
> or you could delete the contents of that file and paste in the results from creating your own **[here]("http://repogen.simplylinux.ch/")**


Thanks :)
but it does get lengthy in the 3rd party repos:-k !! 
->is it necessary to fill it out fully ?
->i want to know whether i'll be able to update the list of selected repos again ?
-> will i be able to install them from ubuntu software store without having to update the repos again ?!

---

### Post by black veils on 2012-11-06
no you dont have to include every repository.

fill out:

all of **ubuntu branches**

all of **ubuntu updates**

all of **ubuntu partner repos**

**3rd parties repos**:

**medibuntu**

anything else you can get from the internet if you want it.

after you have edited the file to contain only the output of that repogen website, you need to refresh the repositories, and adjust you update manager settings.

---

### Post by aravind4j on 2012-11-06
finally i generated the list thanks for the help :) :KS

---

