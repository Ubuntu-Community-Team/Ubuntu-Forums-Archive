---
title: "can't install apps"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by markellejk on 2014-01-29
When I open my software center, it displays a message that my software center has closed unexpectedly which is immediately followed by an error message telling me something about the package or package header, or there are no messages at all.  I was taught to use sudo apt-get in the command line, so I tried that and this is what I get:
 [ATTACH=CONFIG]249893[/ATTACH]
 I can't install anything, and I need some kind of flash player and several codecs. I think the problem may have been caused by installing a program, but I can't uninstall the program now.  How do I fix this?  Also I am new to forums, so if I am posting wrong, please inform me and I will try to correct it.  Thanks for helping!

---

### Post by deadflowr on 2014-01-29
could you try
```
sudo apt-get clean
```
then 
```
sudo apt-get update
```
then try
```
sudo apt-get upgrade
```
post any problems.

And try copy and paste the output into [code tags.]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

Not sure this will help, but think of it as a first step.

---

### Post by claracc on 2014-01-29
Also, as this thread adresses: [http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err) , you can remove the contents in the lists folder and regenerate them again:

In a xterm: ```
CTRL+alt+T
``` 

you can run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
```

and then, regenerate the contents in the forementioned folder by means of:

```
sudo apt-get update
```

---

### Post by markellejk on 2014-01-29
this is what I get in terminal:
```
storywriter@storywriter-Inspiron-N5030:~$ sudo apt-get clean
[sudo] password for storywriter: 
storywriter@storywriter-Inspiron-N5030:~$ sudo aptget update
sudo: aptget: command not found
storywriter@storywriter-Inspiron-N5030:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
storywriter@storywriter-Inspiron-N5030:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:3 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]  
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:9 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [4,878 B]  
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release [49.6 kB]          
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [357 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:12 [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages [7,897 B]   
Get:13 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [8,948 B]    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex             
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main amd64 Packages [745 kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [90.4 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,454 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [377 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [94.7 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,650 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_CA                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [168 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_CA             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB             
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [56.3 kB]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe amd64 Packages [231 kB]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [14.2 kB]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages [769 kB]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages [236 kB]
Get:30 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.4 kB]
Get:31 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:32 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:33 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA                
Get:34 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_GB [96.4 kB]   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en             
Get:35 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en_GB [79.8 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA            
Get:36 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_GB [5,492 B]
Get:37 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main amd64 Packages [4,806 B]
Get:38 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe amd64 Packages [37.9 kB]
Get:39 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [5,206 B]
Get:40 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main i386 Packages [4,811 B]
Get:41 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]
Get:42 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Get:43 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:44 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:45 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe TranslationIndex [73 B]
Get:46 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en [334 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA        
Get:47 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_GB [96.4 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Get:48 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB [79.8 kB]
Get:49 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en [135 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA    
Get:50 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_GB [5,492 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Get:51 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Translation-en [27.7 kB]
Fetched 4,302 kB in 28s (153 kB/s)                                             
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
storywriter@storywriter-Inspiron-N5030:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
storywriter@storywriter-Inspiron-N5030:~$
``` 

did I do that right?

---

### Post by deadflowr on 2014-01-29
Now do post #3's advice.

---

