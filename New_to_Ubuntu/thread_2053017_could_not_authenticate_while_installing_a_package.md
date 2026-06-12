---
title: "could not authenticate while installing a package"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by syednasirraza on 2012-09-04
hi
i was trying to install one of the package/utility on my system,,, 
meanwhile it was displayed that........
** package could not be authenticated, should it be continued (y/n)**
what i m supposed to do here???? 
is it harmful to continue????
and why authentication could not be done???
plz guide in detail.............

---

### Post by Bachstelze on 2012-09-04
What are you trying to install?

---

### Post by syednasirraza on 2012-09-07
i was just trying to install build-essential

---

### Post by oldos2er on 2012-09-07
Can you post the output of ```
sudo apt-get update
``` ?

---

### Post by syednasirraza on 2012-09-08
i dont have it..........later i tried again , and i got it done,,, since a couple of minutes later,,, it did not sayanything about authentication...but why it was once,,,, and wt if i recieve some msg like this in  future while installing anything else,,, is it really risky to install without authentication????should i avoid or continue??plz guide on this

---

### Post by oldos2er on 2012-09-08
If you post the output from the command I gave in post#4 (it's just a matter of using copy and paste) we could see which repositories are missing their gpg keys. I can't really answer your questions until you provide the needed info.

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by syednasirraza on 2012-09-13
like this time i tried to install xchm,,, and i got same validation/authentication issue...so what to do now??should i install it,,,or avoid without authentication???can it b a serious issue???
plzz guide
fol is output where i found authentication issue while installing....

~$ sudo apt-get install xchm
sudo: unable to resolve host networks
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libchm1 libwxbase2.8-0 libwxgtk2.8-0
Suggested packages:
  libgnomeprintui2.2-0
The following NEW packages will be installed:
  libchm1 libwxbase2.8-0 libwxgtk2.8-0 xchm
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,047 kB of archives.
After this operation, 11.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libwxbase2.8-0 libwxgtk2.8-0 libchm1 xchm
Install these packages without verification [y/N]?

---

### Post by oldos2er on 2012-09-13
Please post text of ```
sudo apt-get update
```

---

### Post by syednasirraza on 2012-09-14
~$ sudo apt-get update 
sudo: unable to resolve host networks
[sudo] password for nasir: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                               
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                                                                    
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                                                    
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [7,338 B]                                                
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [9,651 B]                                                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                                           
Ign [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise InRelease
Ign [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates InRelease
Ign [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports InRelease          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B] 
Get:6 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise Release.gpg [198 B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                                                                                                                 
Get:8 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates Release.gpg [198 B]                                                                                                                                              
Get:9 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports Release.gpg [198 B]                                                                                                                                            
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise Release                                                                                                                                                                    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [42.8 kB]                                                                                                                                           
Get:11 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates Release [49.6 kB]                                                                                                                                               
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]                                                                                                                                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [13.5 kB]                                                                                                                                       
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B]                                                                                                                                     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [165 kB]                                                                                                                                      
Get:16 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports Release [49.6 kB]                                                                                                                                             
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/main Sources                                                                                                                                                               
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/restricted Sources                                                                                                                                                         
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/universe Sources                                                                                                                                                           
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/multiverse Sources                                                                                                                                                         
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/main i386 Packages                                                                                                                                                         
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/restricted i386 Packages                                                                                                                                                   
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/universe i386 Packages                                                                                                                                                     
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/multiverse i386 Packages                                                                                                                                                   
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/main TranslationIndex                                                                                                                                                      
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/multiverse TranslationIndex                                                                                                                                                
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/restricted TranslationIndex                                                                                                                                                
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/universe TranslationIndex                                                                                                                                                  
Get:17 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/main Sources [164 kB]                                                                                                                                           
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]                                                                                                                               
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [43.9 kB]                                                                                                                                 
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]                                                                                                                               
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]                                                                                                                                     
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]                                                                                                                               
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]                                                                                                                               
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]                                                                                                                                 
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [76.5 kB]                                                                                                                                    
Get:26 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]                                                                                                                                    
Get:27 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/universe Sources [51.8 kB]                                                                                                                                      
Get:28 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/multiverse Sources [4,241 B]                                                                                                                                    
Get:29 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/main i386 Packages [388 kB]                                                                                                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                                                                                                           
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [27.2 kB]                                                                                                                                
Get:31 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]                                                                                                                              
Get:32 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/universe i386 Packages [131 kB]                                                                                                                                 
Get:33 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,672 B]                                                                                                                              
Get:34 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                                                                                                                 
Get:35 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                                                                                                                           
Get:36 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                                                                                                                           
Get:37 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                                                                                                             
Get:38 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/main Sources [2,422 B]                                                                                                                                        
Get:39 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                                                                                                                     
Get:40 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/universe Sources [14.2 kB]                                                                                                                                    
Get:41 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]                                                                                                                                  
Get:42 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]                                                                                                                                  
Get:43 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                                                                                               
Get:44 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/universe i386 Packages [12.4 kB]                                                                                                                              
Get:45 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]                                                                                                                              
Get:46 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]                                                                                                                                  
Get:47 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [71 B]                                                                                                                            
Get:48 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]                                                                                                                            
Get:49 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/universe TranslationIndex [72 B]                                                                                                                              
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/main Translation-en                                                                                                                                                        
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/multiverse Translation-en                                                                                                                                                  
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/restricted Translation-en                                                                                                                                                  
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise/universe Translation-en                                                                                                                                                    
Get:50 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/main Translation-en [188 kB]                                                                                                                                    
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                                                                                                          
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                                                                          
Get:51 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-updates/universe Translation-en [77.7 kB]                                                                                                                               
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/main Translation-en                                                                                                                                              
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                                                                                                        
Hit [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                                                                                        
Get:52 [http://ci.archive.ubuntu.com](http://ci.archive.ubuntu.com) precise-backports/universe Translation-en [9,070 B]                                                                                                                             
Fetched 1,635 kB in 21s (75.5 kB/s)                                                                                                                                                                                 
Reading package lists... Done

---

### Post by oldos2er on 2012-09-14
There's nothing there about missing keys. How about ```
sudo apt-key update
```

---

### Post by NikTh on 2012-09-14
> **syednasirraza said:**
> ~$ sudo apt-get update 
**sudo: unable to resolve host networks**


Hi , 
also give the results of 
```
cat /etc/hostname 
cat /etc/hosts
``` 

Thanks

---

### Post by syednasirraza on 2012-09-14
here it is...by the way,,, what is apt-key update???why required???


$ sudo apt-key update
sudo: unable to resolve host networks
[sudo] password for nasir: 
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2

---

