---
title: "untrusted package error on update"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by cabz on 2013-03-22
I got a notification about some updates on my laptop. when i went to install i got a message saying that this update was from an untrusted package? 
file:///home/cabz/Desktop/Screenshot%20-%2003222013%20-%2012:14:15%20PM.png

---

### Post by cabz on 2013-03-22
I got a notification about some updates on my laptop. when i went to install i got a message saying that this update was from an untrusted package? <br><img src="http://ubuntuforums.org/attachment.php?attachmentid=240437&amp;stc=1" attachmentid="240437" alt="" id="vbattach_240437" class="previewthumb"><br>
<br>
<br>

---

### Post by cabz on 2013-03-22
sorry for the screwy post ,I forgot how to post a screenshot:confused: . anyway I am running xubuntu 12.04 on a dell mini laptop if that helps .

---

### Post by oldos2er on 2013-03-22
Threads merged and moved to Absolute Beginners. Please don't open more than one thread per question or problem.

---

### Post by cabz on 2013-03-22
oops , i didnt realize i had done that.

---

### Post by cortman on 2013-03-22
Run (in a terminal)

```
sudo apt-get update
```

If it returns any errors, please post them. Otherwise, then try updating again.
Note: apt-get update just updates the repository information, not any software.

---

### Post by cabz on 2013-03-22
> **cortman said:**
> Run (in a terminal)

```
sudo apt-get update
```

If it returns any errors, please post them. Otherwise, then try updating again.
Note: apt-get update just updates the repository information, not any software.
heres the list, i got quite a few errors it seems

```
@ubuntu:~$ sudo apt-get update
[sudo] password for cabz: 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                                        
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                                                                
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                                            
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                                                        
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]                                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources/DiffIndex                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources/DiffIndex                                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources/DiffIndex                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources/DiffIndex                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources/DiffIndex                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex                                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                            
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [370 kB]                                                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,494 B]                                             
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]                                                 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                              
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [23.4 kB]                                             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]                                           
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]                                          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                       
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [23.2 kB]                                      
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                                
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [82.7 kB]                                              
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [4,746 B]                                            
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [600 kB]                                             
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.1 kB]                                      
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [191 kB]                                         
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [10.4 kB]                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                                  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                            
  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (110: Connection timed out)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                            
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                     
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                               
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                           
  Unable to connect to ppa.launchpad.net:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                              
  Unable to connect to ppa.launchpad.net:http:
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                           
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                
Hit [http://dl.google.com](http://dl.google.com) stable Release                     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex    
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [64.2 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [22.6 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,380 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [243 kB]     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en      
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [70.5 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Fetched 1,889 kB in 1min 15s (25.0 kB/s)          
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/Release.gpg)  Could not connect to ppa.launchpad.net:80 (91.189.95.83). - connect (110: Connection timed out)


W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/source/Sources)  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/binary-i386/Packages)  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/i18n/Translation-en_US](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/i18n/Translation-en_US)  Unable to connect to ppa.launchpad.net:http:


W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/i18n/Translation-en](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/i18n/Translation-en)  Unable to connect to ppa.launchpad.net:http:


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by cortman on 2013-03-22
Try changing your repository mirrors. You can do this by opening Ubuntu Software Center, and selecting Edit>Software Sources.

---

### Post by cabz on 2013-03-22
> **cortman said:**
> Try changing your repository mirrors. You can do this by opening Ubuntu Software Center, and selecting Edit>Software Sources.
change to what? and any ideas on why all of a sudden the ones i have arent working?

---

### Post by cortman on 2013-03-22
Change them to a server located near you.
It could be the connections to the old ones are down, or are overloaded.

---

### Post by cabz on 2013-03-22
got it, that fixed it. thanks

---

### Post by cortman on 2013-03-23
Great, glad it's working- please add [SOLVED] to the beginning of the thread title.
Good luck!

---

