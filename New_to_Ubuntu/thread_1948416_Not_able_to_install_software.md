---
title: "Not able to install software"
date: 2012-03-28
forum: New to Ubuntu
---

### Post by medusa93 on 2012-03-28
I recently found that I cannot install any software package. The message comes back as "check your internet connection" and when I click OK on that I get the pop-up, "requires installation of unauthorized packages" There is nothing wrong with my internet connection (for example, I am posting using an internet connection that is non-existent according to the software centre) and I have tried two different internet connection and the software that I have tried are Record Desktop, streamer2 and Autokey. I am running Ubuntu and my laptop is fully updated. I have attached some screenshots.

---

### Post by cortman on 2012-03-28
Hi, please run

```
sudo apt-get update
```

and post the full results here. Thanks!

---

### Post by raja.genupula on 2012-03-28
Hi actually the issue is you're trying to install some third party software in Ubuntu . 

If you try to install the samething from terminal then it gonna ask you as Y/N , and you can do installation by giving as Y (yes) .

EDIT : from software center -> EDIT -> Software sources -> other software -> check the Canonical Check Boxes and then try again .

---

### Post by medusa93 on 2012-03-28
I wouldnt mind if one or two extrasoftware doesnt get installed, but I can install nothing. It wasnt like that before
Posting the results of sudo apt-get update
```
suneel@prs:~$ sudo apt-get update
[sudo] password for suneel: 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Get:3 http://archive.canonical.com oneiric Release.gpg [198 B]                 
Get:4 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:5 http://security.ubuntu.com oneiric-security Release [40.8 kB]            
Hit http://extras.ubuntu.com oneiric Release                                   
Ign http://www.geekconnection.org karmic/ InRelease                            
Get:6 http://archive.canonical.com oneiric Release [5,922 B]                   
Get:7 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://extras.ubuntu.com oneiric/main Sources                              
Get:8 http://archive.canonical.com oneiric/partner i386 Packages [4,329 B]     
Hit http://us.archive.ubuntu.com oneiric Release                               
Ign http://us.archive.ubuntu.com oneiric Release                               
Ign http://www.geekconnection.org karmic/ Release.gpg                          
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:9 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Ign http://www.geekconnection.org karmic/ Release                              
Get:10 http://security.ubuntu.com oneiric-security/main Sources [34.8 kB]      
Ign http://www.geekconnection.org karmic/ Packages/DiffIndex                   
Get:11 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]   
Get:12 http://security.ubuntu.com oneiric-security/universe Sources [13.3 kB]  
Get:13 http://security.ubuntu.com oneiric-security/multiverse Sources [1,654 B]
Get:14 http://security.ubuntu.com oneiric-security/main i386 Packages [93.2 kB]
Get:15 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:16 http://security.ubuntu.com oneiric-security/universe i386 Packages [31.1 kB]
Ign http://us.archive.ubuntu.com oneiric/main Sources/DiffIndex                
Ign http://us.archive.ubuntu.com oneiric/restricted Sources/DiffIndex          
Get:17 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,363 B]
Get:18 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:19 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]
Get:20 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:21 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Ign http://us.archive.ubuntu.com oneiric/universe Sources/DiffIndex            
Ign http://us.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex          
Ign http://us.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex          
Ign http://us.archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex    
Ign http://us.archive.ubuntu.com oneiric/universe i386 Packages/DiffIndex      
Ign http://us.archive.ubuntu.com oneiric/multiverse i386 Packages/DiffIndex    
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Get:22 http://security.ubuntu.com oneiric-security/main Translation-en [51.5 kB]
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:23 http://us.archive.ubuntu.com oneiric-updates/main Sources [132 kB]      
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://archive.canonical.com oneiric/partner Translation-en                
Get:24 http://security.ubuntu.com oneiric-security/universe Translation-en [21.9 kB]
Get:25 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:26 http://us.archive.ubuntu.com oneiric-updates/universe Sources [48.8 kB] 
Get:27 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]
Get:28 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [307 kB]
Hit http://www.geekconnection.org karmic/ Packages                             
Ign http://www.geekconnection.org karmic/ Translation-en_US                    
Ign http://www.geekconnection.org karmic/ Translation-en                       
Get:29 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:30 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [104 kB]
Get:31 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,367 B]
Get:32 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:33 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:34 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:35 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Get:36 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [142 kB]
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Get:37 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [62.9 kB]
Fetched 1,156 kB in 14s (77.7 kB/s)                                            
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
suneel@prs:~$ 

```

---

### Post by raja.genupula on 2012-03-28
ok open your terminal and do this
```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
```

all the best .

---

### Post by medusa93 on 2012-03-28
Thank you for taking the trouble

```
suneel@prs:~$ sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
[sudo] password for suneel: 
Ign http://security.ubuntu.com oneiric-security InRelease                       
Ign http://extras.ubuntu.com oneiric InRelease                                  
Ign http://us.archive.ubuntu.com oneiric InRelease                              
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                      
Ign http://archive.canonical.com oneiric InRelease                              
Hit http://security.ubuntu.com oneiric-security Release.gpg                     
Hit http://extras.ubuntu.com oneiric Release.gpg                                
Get: 1 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Hit http://archive.canonical.com oneiric Release.gpg                            
Hit http://security.ubuntu.com oneiric-security Release                         
Hit http://extras.ubuntu.com oneiric Release                                    
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                    
Hit http://archive.canonical.com oneiric Release                                
Hit http://extras.ubuntu.com oneiric/main Sources                               
Hit http://security.ubuntu.com oneiric-security/main Sources                    
Ign http://www.geekconnection.org karmic/ InRelease                  
Hit http://us.archive.ubuntu.com oneiric Release                                
Ign http://us.archive.ubuntu.com oneiric Release                                
Hit http://archive.canonical.com oneiric/partner i386 Packages                  
Hit http://extras.ubuntu.com oneiric/main i386 Packages                         
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                      
Ign http://archive.canonical.com oneiric/partner TranslationIndex               
Hit http://us.archive.ubuntu.com oneiric-updates Release                        
Ign http://www.geekconnection.org karmic/ Release.gpg                           
Ign http://us.archive.ubuntu.com oneiric/main Sources/DiffIndex                 
Ign http://us.archive.ubuntu.com oneiric/restricted Sources/DiffIndex           
Ign http://us.archive.ubuntu.com oneiric/universe Sources/DiffIndex             
Ign http://us.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex           
Ign http://us.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex           
Ign http://www.geekconnection.org karmic/ Release                               
Hit http://security.ubuntu.com oneiric-security/restricted Sources              
Hit http://security.ubuntu.com oneiric-security/universe Sources                
Hit http://security.ubuntu.com oneiric-security/multiverse Sources              
Ign http://us.archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex     
Ign http://us.archive.ubuntu.com oneiric/universe i386 Packages/DiffIndex       
Ign http://us.archive.ubuntu.com oneiric/multiverse i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                  
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex            
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex            
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex              
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources                   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources             
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources               
Hit http://security.ubuntu.com oneiric-security/main i386 Packages              
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages        
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex       
Ign http://www.geekconnection.org karmic/ Packages/DiffIndex                    
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages             
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main Translation-en             
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex          
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex    
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex    
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex      
Hit http://us.archive.ubuntu.com oneiric/main Sources                           
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                     
Hit http://us.archive.ubuntu.com oneiric/universe Sources                       
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                     
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                     
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages               
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                 
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                    
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en              
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en              
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en                
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en            
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en        
Ign http://archive.canonical.com oneiric/partner Translation-en_US              
Ign http://archive.canonical.com oneiric/partner Translation-en                 
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                     
Ign http://extras.ubuntu.com oneiric/main Translation-en
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Hit http://www.geekconnection.org karmic/ Packages
Ign http://www.geekconnection.org karmic/ Translation-en_US
Ign http://www.geekconnection.org karmic/ Translation-en
Fetched 198 B in 19s (10 B/s)
W: GPG error: http://us.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

suneel@prs:~$ 

```

---

### Post by raja.genupula on 2012-03-28
hmm ok do this in terminal 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update 
```

paste them in terminal one by one and try again .

---

### Post by cortman on 2012-03-28
If Raja's suggestion doesn't work for you, [this post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/") deals with fixing GPG errors in Ubuntu, which seems to be at least part of your problem.

---

### Post by medusa93 on 2012-03-28
This is the result of running those commands
```
suneel@prs:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for suneel: 
suneel@prs:~$ sudo rm -rf /var/lib/apt/lists/*
suneel@prs:~$ sudo apt-get update
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://archive.canonical.com oneiric InRelease                             
Get:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Get:2 http://archive.canonical.com oneiric Release.gpg [198 B]                 
Get:3 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Get:4 http://archive.canonical.com oneiric Release [5,922 B]                   
Get:5 http://archive.canonical.com oneiric/partner i386 Packages [4,329 B]     
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:6 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Get:7 http://security.ubuntu.com oneiric-security Release [40.8 kB]            
Ign http://www.geekconnection.org karmic/ InRelease                            
Ign http://www.geekconnection.org karmic/ Release.gpg                          
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Get:8 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                   
Get:9 http://security.ubuntu.com oneiric-security/main Sources [34.8 kB]       
Ign http://archive.canonical.com oneiric/partner Translation-en                
Get:10 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]   
Get:11 http://security.ubuntu.com oneiric-security/universe Sources [13.3 kB]  
Get:12 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]          
Get:13 http://security.ubuntu.com oneiric-security/multiverse Sources [1,638 B]
Ign http://www.geekconnection.org karmic/ Release                              
Get:14 http://security.ubuntu.com oneiric-security/main i386 Packages [93.2 kB]
Get:15 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:16 http://security.ubuntu.com oneiric-security/universe i386 Packages [31.1 kB]
Get:17 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,372 B]
Get:18 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:19 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]
Get:20 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:21 http://www.geekconnection.org karmic/ Packages [956 B]                  
Get:22 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Get:23 http://security.ubuntu.com oneiric-security/main Translation-en [51.5 kB]
Get:24 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Get:25 http://security.ubuntu.com oneiric-security/multiverse Translation-en [1,494 B]
Get:26 http://security.ubuntu.com oneiric-security/restricted Translation-en [14 B]
Ign http://www.geekconnection.org karmic/ Translation-en_US                    
Get:27 http://security.ubuntu.com oneiric-security/universe Translation-en [21.9 kB]
Get:28 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]       
Ign http://www.geekconnection.org karmic/ Translation-en                       
Get:29 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Ign http://extras.ubuntu.com oneiric InRelease                            
Get:30 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Get:31 http://extras.ubuntu.com oneiric Release [9,759 B]       
Get:32 http://extras.ubuntu.com oneiric/main Sources [2,260 B]   
Get:33 http://extras.ubuntu.com oneiric/main i386 Packages [3,711 B]         
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                    
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:34 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]        
Get:35 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
Get:36 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B] 
Get:37 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]  
Get:38 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Get:39 http://us.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]
Get:40 http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:41 http://us.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:42 http://us.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]
Get:43 http://us.archive.ubuntu.com oneiric-updates/main Sources [132 kB]      
Get:44 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:45 http://us.archive.ubuntu.com oneiric-updates/universe Sources [48.8 kB] 
Get:46 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,661 B]
Get:47 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [307 kB]
Get:48 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:49 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [104 kB]
Get:50 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,356 B]
Get:51 http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:52 http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:53 http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:54 http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Get:55 http://us.archive.ubuntu.com oneiric/main Translation-en [701 kB]       
Get:56 http://us.archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]
Get:57 http://us.archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]
Get:58 http://us.archive.ubuntu.com oneiric/universe Translation-en [3,165 kB] 
Get:59 http://us.archive.ubuntu.com oneiric-updates/main Translation-en [142 kB]
Get:60 http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,524 B]
Get:61 http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en [508 B]
Get:62 http://us.archive.ubuntu.com oneiric-updates/universe Translation-en [62.9 kB]
Fetched 16.7 MB in 1min 32s (181 kB/s)    
Reading package lists... Done
suneel@prs:~$ 
```

---

### Post by cortman on 2012-03-28
This looks perfect! Try installing whatever you were trying before.

---

### Post by medusa93 on 2012-03-28
Thank you raja and cortman. I was able to install autokey and work with autokey. Thank you all. I wish I could understand the process by which this glitch got corrected. But not blessed with enough grey cells for that in this innings.
Regards

---

### Post by raja.genupula on 2012-03-29
> But not blessed with enough grey cells for that in this innings.

any other issue on your Ubuntu ?

---

