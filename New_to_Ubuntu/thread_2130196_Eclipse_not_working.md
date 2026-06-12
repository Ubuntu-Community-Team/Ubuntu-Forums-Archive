---
title: "Eclipse not working"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2013-03-28
Hi, i need to have my ecliplse Indigo working running on Ubutnu 12.04. As i run the HelloWord example project, i have problems
with iostrean and include std..I am used to use Visual studio in Windows so i m sure is a problem of libraries importing..
can you help e please? i have installe something called gcc or something like that at the latest version, but how can i use it?
thank you

---

### Post by r.stiltskin on 2013-03-28
What sort of problems?  Can you be more specific?  Error messages?

Did you install eclipse-cdt and eclipse-cdt-pkg-config?

---

### Post by SchrodingerCat on 2013-03-28
ok..i have.. symbol cout could not be solved... and i am not sure i installed cdt and cdt-pkg-config..should i? can u plase write the code to install it?? i am new both to ubutnu and eclipse

---

### Post by r.stiltskin on 2013-03-28
Did you download Eclipse directly from eclipse.org?  You can probably make things easier by uninstalling that one and installing it directly from the ubuntu repository.

```
sudo apt-get update && sudo apt-get install eclipse eclipse-cdt eclipse-cdt-pkg-config
```

---

### Post by SchrodingerCat on 2013-03-29
ok...now it says...launch failed bynary not found..

---

### Post by r.stiltskin on 2013-03-29
It sounds like you're trying to use a launcher (panel button) left over from a previous, deleted, program.  But I can't be sure without knowing exactly what your situation is.  Please list the exact steps that you have done.  What, if anything, did you uninstall (and how)?  What did you install (and how)?

Also describe exactly how you are now trying to start Eclipse -- are you clicking on a panel icon?  on a desktop icon? or on a line in the application menu?

What happens if you type alt+f2 then type eclipse and press enter?  (Or select "run command" on the application menu, then type eclipse and press enter?)

---

### Post by SchrodingerCat on 2013-03-30
Well, i installed ubuntu again, and i just wrote the code you told me..

this is my output:

Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:3 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise Release                               
Get:4 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:5 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                      
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/main Sources                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/universe Sources                      
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/main amd64 Packages          
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/multiverse amd64 Packages    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/restricted i386 Packages              
Get:7 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,210 B]                
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/multiverse TranslationIndex  
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/universe TranslationIndex    
Get:8 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/main Sources [373 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                   
Get:9 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,213 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:11 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/restricted Sources [5,494 B]
Get:12 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/universe Sources [82.7 kB] 
Get:13 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/multiverse Sources [4,746 B]
Get:14 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/main amd64 Packages [592 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [64.7 kB]      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:16 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:17 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/universe amd64 Packages [190 kB]
Get:18 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [9,418 B]
Get:19 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/main i386 Packages [603 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [22.6 kB]  
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,380 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [233 kB]
Get:24 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.1 kB]
Get:25 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/universe i386 Packages [192 kB]
Get:26 [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/multiverse i386 Packages [10.4 kB]
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/main Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/multiverse amd64 Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) precise-backports/universe Translation-en     
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [68.6 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,186 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [243 kB]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [70.5 kB]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Fetched 2,905 kB in 2s (1,069 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package eclipse-cdt-pkg-config





as u can see at the end it says Unable to locate package eclipse-cdt-pkg-config

---

### Post by r.stiltskin on 2013-03-30
OK.  It seems that there is no eclipse-cdt-pkg-config in 12.04.  It would have been good to have, but you can do without it.  But you should still install eclipse-cdt which definitely is in the 12.04 repository, so run
```
sudo apt-get install eclipse-cdt
```
and then you should be able to compile and run C++ programs.  Install that and then do File/New/C++ project and see if you can create and run the "Hello World C++ Project".

---

### Post by SchrodingerCat on 2013-04-01
Taht works thanks.

---

