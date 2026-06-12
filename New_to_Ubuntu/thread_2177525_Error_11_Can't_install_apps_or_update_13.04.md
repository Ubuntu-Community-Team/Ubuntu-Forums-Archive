---
title: "Error 11: Can't install apps or update 13.04"
date: 2013-09-29
forum: New to Ubuntu
---

### Post by courtney2 on 2013-09-29
Hey guys! So I got 13.04 running on a dual boot..the dual boot (2 HDDs) is working great! Now..I can't really do a bloody thing on this OS! Ubuntu is failing to install or update anything I throw at it via Terminal or Software Centre. I ALWAYS hang up on Error 11 or there's a lock. Even then, I'll remove the lock and I still have failed updates and installs. The only thing I've been able to successfully install is Google Chrome and the most recent Nvidia drivers...even then, I'm not sure if that's working right. Anyways, I need help with this Error 11! I can't update or install anything :mad:

---

### Post by carl4926 on 2013-09-29
Did you shutdown and try again

---

### Post by Bucky Ball on 2013-09-29
Hi. I have taken the liberty of giving your thread a descriptive title to give you more chance of getting help. Generic titles like 'need help' or 'terrible trouble' say nothing about the issue you're having. Most people post a thread here because they need help or have troubles. ;)

If you're trying to update in a terminal with Software Centre or Synaptics open at the same time, that's your lock problem. Close everything, open a terminal and run 'sudo apt-get update'. Shouldn't be a lock. 

Now that should be fixed, run 'sudo apt-get update' in a terminal, copy/paste the output in a post here. Thanks. 

Good luck. 

PS: If you'd like the thread title changed to something else and you've run out of time to change it yourself (30 minutes after posting from memory), PM me with a couple of suggestions and will change for you.

PPS: Although the other posts in the thread have the old title, the one that people see when searching is the new one. ;)

---

### Post by courtney2 on 2013-09-29
Here is what I get virtually every time so far:

Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports Release.gpg                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring Release                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main amd64 Packages                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release.gpg                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/main Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring Release                           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/restricted Sources                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main amd64 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/universe Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main i386 Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/multiverse Sources                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/main amd64 Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/restricted amd64 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/universe amd64 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/multiverse amd64 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_CA                     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/main i386 Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/restricted i386 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main amd64 Packages                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/main Translation-en  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/main Sources 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/multiverse Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/restricted Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/restricted Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en_CA   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/universe Sources
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en_CA
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Translation-en                        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/universe amd64 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) raring/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) raring-backports/universe Translation-en_CA
98% [Connecting to security.ubuntu.com]
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)



Also yes, I have shut down and tried again a million times with no luck...I can't try to update Ubuntu either because it fails and I get what I just pasted

---

### Post by oldos2er on 2013-09-29
There are some suggestions here: [http://askubuntu.com/questions/111597/how-can-i-work-around-something-wicked-happened-resolving-mirror-errors](http://askubuntu.com/questions/111597/how-can-i-work-around-something-wicked-happened-resolving-mirror-errors)

---

### Post by courtney2 on 2013-09-29
> **oldos2er said:**
> There are some suggestions here: [http://askubuntu.com/questions/111597/how-can-i-work-around-something-wicked-happened-resolving-mirror-errors](http://askubuntu.com/questions/111597/how-can-i-work-around-something-wicked-happened-resolving-mirror-errors)

This one is the winner. I followed one of the suggestions saying to connect to the main server. I was set to Canada by default.

---

### Post by martin118 on 2014-08-26
Hey Guys,

I followed your instructons and read the possiblities on the linked page. But I think i've got the real reason for that...

While I had the problem, that the hostnames aren't reachable I saw, that something like a IPv6-Adress  is in brackets.
Rememering problems between ipv4 and ipv6 i switched off ipv6 on my routers web interface - and now: the adress is reachable after a few seconds.

Don't know how to disable ipv6 in ubuntu or if your router can disable this feature, too - but in my case it was the solution.

(Surfin with Telekom FTTH)

Best,

Martin

---

