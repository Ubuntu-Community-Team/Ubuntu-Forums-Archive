---
title: "warning alert"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by amiralex32 on 2013-12-26
dear all
i have a problem that i have a warning on the updateauncher and when i launch it it cause this messge

Failed to load the package list

This is a serious problem. Try again later. If this problem appears again, please report an error to the developers.
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened

then i run this command

amiralex@amir-pc:~$ sudo apt-get update
[sudo] password for amiralex: 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release         
Get:3 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release
Get:4 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates Release.gpg [933 B]
Get:5 [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports Release.gpg [933 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources   
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources               
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports Release           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources             
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/main Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages   
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/universe Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/main i386 Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/universe i386 Packages
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/universe Translation-en               
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/main Sources                  
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/restricted Sources            
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/universe Sources              
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/multiverse Sources            
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/main i386 Packages            
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/restricted i386 Packages      
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/universe i386 Packages        
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/multiverse i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/main Translation-en           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/restricted Translation-en
Hit [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/universe Translation-en
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://eg.archive.ubuntu.com](http://eg.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Fetched 3,804 B in 24s (155 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

wha shall i do to solve this problem

---

### Post by newb85 on 2013-12-26
The files in /var/lib/apt/lists/ are automatically generated, and if you delete them, your machine should re-create them automatically with no problems.

From [http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err)

```
sudo rm -vf /var/lib/apt/lists/*
sudo apt-get update
```

---

