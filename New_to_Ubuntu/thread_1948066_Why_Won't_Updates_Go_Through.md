---
title: "Why Won't Updates Go Through"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by kizzyaggots on 2012-03-27
Hi guys, I'm using Ubuntu 11.04 and I am trying to get my updates to go through but i keep getting this message..............
Requires Installation from Untrusted Packages, the action would require the installation of packages from not authenticated sources.

Can somebody suggest how i get the updates through please?


        Cheers Kizzy.

---

### Post by PhantomTurtle on 2012-03-27
You can try to install updates through the terminal. The command is:
```
sudo apt-get upgrade
```

---

### Post by kizzyaggots on 2012-03-27
That seemed to work but some untrusted updates never went through.

---

### Post by loolooyyyy on 2012-03-27
what sources have you added? did you remember to add the proper "key"s when you added them?
check your software sources its in settings, for instance you have added google for google chrome search to see how to add google keys,
or you can simply disable them if you dont need them
and there is an option for installing software from untrusted sources (which means dont have the proper identification key, as in not added by user or fake!) but i can't remember, though it's totally not advised
good luck to you

---

### Post by d4m1r on 2012-03-27
Can you list us the name of the packages it won't install?

---

### Post by oldos2er on 2012-03-27
> **kizzyaggots said:**
> That seemed to work but some untrusted updates never went through.

Can you please post the output from ```
sudo apt-get update
``` ?

---

### Post by kizzyaggots on 2012-03-28
This is what the terminal says.......


The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E

---

### Post by loolooyyyy on 2012-03-28
> **kizzyaggots said:**
> This is what the terminal says.......


The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E

as i said , you've forgotten to add 'key' for some sources you've add,
can you give a screenshot from "souftware sources' window , 'other sources' tab, located in settings?

---

### Post by cortman on 2012-03-28
> **kizzyaggots said:**
> This is what the terminal says.......


The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E

For GPG problems the instructions in [this post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/") may solve it.

---

### Post by kizzyaggots on 2012-03-30
```
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E
chris@chris-KJ329AA-ABG-m9290a:~$ 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric InRelease                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick InRelease                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free i386 Packages                   
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free i386 Packages               
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,756 B]                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free TranslationIndex                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [708 B]                    
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [1,648 B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free TranslationIndex            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main TranslationIndex          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Translation-en                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/free Translation-en
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) oneiric/non-free Translation-en
Fetched 12.7 kB in 17s (728 B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E
chris@chris-KJ329AA-ABG-m929
```

---

### Post by Old_Grey_Wolf on 2012-03-31
To get the key enter these commands.```
gpg --keyserver keyserver.ubuntu.com --recv 6D975C4791E7EE5E

gpg --export --armor 6D975C4791E7EE5E | sudo apt-key add -
```

---

### Post by oldos2er on 2012-03-31
> **kizzyaggots said:**
> 
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316 B]                    

Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main TranslationIndex          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       

Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Translation-en_US                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Translation-en                      

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6D975C4791E7EE5E
chris@chris-KJ329AA-ABG-m929

If you're running 11.10 (Oneiric) you need to get rid of all these  maverick sources. Run ```
gksu software-properties-gtk
``` to do so.

---

### Post by Old_Grey_Wolf on 2012-03-31
> **oldos2er said:**
> If you're running 11.10 (Oneiric) you need to get rid of all these  maverick sources. Run ```
gksu software-properties-gtk
``` to do so.

Ops, I missed that :redface:

---

### Post by Frogs Hair on 2012-03-31
This may be of interest .[http://naveenubuntu.blogspot.com/2011/08/fixing-gpg-keys-in-ubuntu.html](http://naveenubuntu.blogspot.com/2011/08/fixing-gpg-keys-in-ubuntu.html)

---

### Post by kizzyaggots on 2012-04-02
> **PhantomTurtle said:**
> You can try to install updates through the terminal. The command is:
```
sudo apt-get upgrade
```

I used these commands and it seemed to work fine....

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by kizzyaggots on 2012-04-02
Problem solved, thanks guys and girls for all your help.

                  Cheers Chris.

---

