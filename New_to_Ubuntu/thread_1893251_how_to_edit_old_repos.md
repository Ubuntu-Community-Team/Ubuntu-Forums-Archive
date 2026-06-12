---
title: "how to edit old repos"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by Sovereign Entity on 2011-12-09
I have a Ubuntu 10.04 install that will not update from update manager or terminal.The error is Size mismatch. I need to know how to tell which repository is old or outdated and how do I remove them. 
Here is my repository list [URL="http://paste.ubuntu.com/765080/"]

---

### Post by hansdown on 2011-12-09
Hi, Sovereign Entity.

```
sudo aptitude  clean
```

Then

```
sudo aptitude update
```

Hope this helps.

---

### Post by bluexrider on 2011-12-09
you would also get other updates if you uncomment

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse 
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner 
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner 

then 

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Sovereign Entity on 2011-12-09
I tried the clean command but to no avail. The system still can't     update.
bluexrider how do I uncomment?

---

### Post by wildmanne39 on 2011-12-10
Hi, please run this command:
```
sudo apt-get update
```
and post all the information here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by lolpenguin on 2011-12-10
Check [FONT="Courier New"]/etc/apt/sources.list[/FONT] for errors.

---

### Post by Sovereign Entity on 2011-12-10
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://hacktolive.org](http://hacktolive.org) lucid Release.gpg                                    
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/restricted Translation-en_US     
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/multiverse Translation-en_US     
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/universe Translation-en_US
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/partner Translation-en_US
Hit [http://hacktolive.org](http://hacktolive.org) lucid Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/main Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources    
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Ign [http://hacktolive.org](http://hacktolive.org) lucid/restricted Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/multiverse Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/universe Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/partner Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/main Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/restricted Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/multiverse Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/universe Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/partner Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/main Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/restricted Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/multiverse Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/universe Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/partner Packages
Reading package lists... Done

---

### Post by Sovereign Entity on 2011-12-10
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-en_US              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Hit [http://hacktolive.org](http://hacktolive.org) lucid Release.gpg                                    
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/restricted Translation-en_US     
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/multiverse Translation-en_US     
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/universe Translation-en_US
Ign [http://hacktolive.org/repo/archive/](http://hacktolive.org/repo/archive/) lucid/partner Translation-en_US
Hit [http://hacktolive.org](http://hacktolive.org) lucid Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/main Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources    
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                    
Ign [http://hacktolive.org](http://hacktolive.org) lucid/restricted Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/multiverse Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/universe Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/partner Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/main Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/restricted Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/multiverse Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/universe Packages
Ign [http://hacktolive.org](http://hacktolive.org) lucid/partner Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/main Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/restricted Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/multiverse Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/universe Packages
Hit [http://hacktolive.org](http://hacktolive.org) lucid/partner Packages
Reading package lists... Done

---

### Post by bluexrider on 2011-12-10
> **Sovereign Entity said:**
> I tried the clean command but to no avail. The system still can't     update.
bluexrider how do I uncomment?

in terminal

```
sudo gedit /etc/apt/sources.list
```remove the "#" at the beginning of each line which you want to use

save, then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by wildmanne39 on 2011-12-10
Hi, that looks good,run the command this way and post if you have any errors.
```
sudo apt-get update && sudo apt-get upgrade
```
Thank you

---

