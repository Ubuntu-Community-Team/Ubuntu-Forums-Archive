---
title: "File missing &amp; lock problem"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by 007riky on 2013-04-05
Hi Again,

While uploading few more components I'm getting these problems.

[IMG]http://i.imgur.com/QfFgVtZ.png[/IMG]

[IMG]http://i.imgur.com/7D9WvTJ.jpg[/IMG]

Kindly help me

---

### Post by Bashing-om on 2013-04-05
007riky; Hi !

The lock condition generally indicates other instances of package management is open.
Close out all instances (USC. or synaptic, or dpkg, or apt-get ect ect): Reboot.
Then run terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
``` and see if the package manager generates any errors.[INDENT=2]
hope all is fine

[/INDENT]

---

### Post by 007riky on 2013-04-06
> **Bashing-om said:**
> 007riky; Hi !

The lock condition generally indicates other instances of package management is open.
Close out all instances (USC. or synaptic, or dpkg, or apt-get ect ect): Reboot.
Then run terminal commands:
```
sudo apt-get update
sudo apt-get upgrade
``` and see if the package manager generates any errors.[INDENT=2]
hope all is fine

[/INDENT]


has this been done??

#> -K53U:~$ sudo apt-get update
[sudo] password for : 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted amd64 Packages   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe amd64 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse amd64 Packages   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main amd64 Packages           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted amd64 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe amd64 Packages       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse amd64 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Fetched 72 B in 6s (11 B/s)                                                    
Reading package lists... Done
K53U:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
-K53U:~$ 



---

### Post by ibjsb4 on 2013-04-06
```
sudo lsof /var/lib/dpkg/lock
```

Should tell you whats locking dpkg. 
Also could you post /var/log/jockey.log

Also I wonder if jockey is hung up.  Open your system monitor>processes and kill jockey if it appears there.

---

### Post by deadflowr on 2013-04-06
As far as jockey goes, you could probably post what the log file that you where pointed to says.

/var/log/jockey.log

---

