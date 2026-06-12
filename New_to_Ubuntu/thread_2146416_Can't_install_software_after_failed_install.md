---
title: "Can't install software after failed install"
date: 2013-05-18
forum: New to Ubuntu
---

### Post by JohntheChristian on 2013-05-18
I attempted to install visual boy advance from ubuntu software center, it failed, and now I can't install anything. Attempt to repair fails.

---

### Post by ibjsb4 on 2013-05-18
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post the output using code tags.

[ATTACH=CONFIG]242727[/ATTACH]

---

### Post by JohntheChristian on 2013-05-18
```
tommy@tommy-Presario-CQ62-Notebook-PC:~$ sudo apt-get updates
[sudo] password for tommy: 
E: Invalid operation updates
tommy@tommy-Presario-CQ62-Notebook-PC:~$ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release.gpg                            
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release.gpg                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources                    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources              
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main amd64 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted amd64 Packages       
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe amd64 Packages         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Sources                     
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main amd64 Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe amd64 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages          
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Sources                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Sources             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Sources             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main amd64 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted amd64 Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe amd64 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_US    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main i386 Packages   
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) raring-backports/universe Translation-en_US
Error: Timeout was reached
Reading package lists... Done
```

---

### Post by ibjsb4 on 2013-05-19
Im not finding much on this, but here is something to try.

[http://docs.opsview.com/doku.php?id=reporting-latest:installation#debian_ubuntu_timeout_while_downloading](http://docs.opsview.com/doku.php?id=reporting-latest:installation#debian_ubuntu_timeout_while_downloading)

---

