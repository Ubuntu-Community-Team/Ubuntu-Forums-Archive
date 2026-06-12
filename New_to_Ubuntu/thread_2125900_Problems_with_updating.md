---
title: "Problems with updating"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by MichaelFenlon on 2013-03-15
What is going on and how do I fix this? This is what the Terminal is saying. I believe this is what is preventing me from downloading/updating java also.
```

michae@michael-Inspiron-N5110:~$ sudo apt-get update
[sudo] password for michae: 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://dl.google.com stable Release.gpg                                    
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]  
Hit http://us.archive.ubuntu.com precise Release                               
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com precise-backports Release                     
Ign http://dl.google.com stable/main TranslationIndex                          
Get:5 http://security.ubuntu.com precise-security/main Sources [64.3 kB]       
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:6 http://us.archive.ubuntu.com precise-updates/main Sources [369 kB]
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [22.2 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [239 kB] 
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:11 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:12 http://security.ubuntu.com precise-security/universe i386 Packages [69.9 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,120 B]
Get:14 http://us.archive.ubuntu.com precise-updates/universe Sources [81.2 kB] 
Get:15 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:16 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,746 B]
Get:17 http://us.archive.ubuntu.com precise-updates/main i386 Packages [595 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:18 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [9,505 B]
Get:19 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [189 kB]
Get:20 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages   
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en            
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise/restricted Translation-en      
Hit http://us.archive.ubuntu.com precise/universe Translation-en        
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en    
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Err http://ppa.launchpad.net precise/main Sources 
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 1,769 kB in 1s (932 kB/s)
W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I do very much need help. Thank you all.

---

### Post by grahammechanical on 2013-03-15
This is the important bit

> [COLOR=#000000]Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [/COLOR]
[COLOR=#000000]404 Not Found[/COLOR]
[COLOR=#000000]Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages[/COLOR]
[COLOR=#000000]404 Not Found[/COLOR]
[COLOR=#000000]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#000000]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#000000]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#000000]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#000000]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US[/COLOR]
[COLOR=#000000]Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en[/COLOR]
[COLOR=#000000]Fetched 1,769 kB in 1s (932 kB/s)[/COLOR]
[COLOR=#000000]W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/precise/main/source/Sources) 404 Not Found[/COLOR]

[COLOR=#000000]W: Failed to fetch [http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/precise/main/binary-i386/Packages) 404 Not Found[/COLOR]

Remove those PPAs from Software Sources and then see if you can update with out errors. Update Manager is trying get check those PPAs for updates but it cannot access the site.

Regards.

---

### Post by deadflowr on 2013-03-15
Yep you'll need to disable that ppa for java.
You either do so manually, by editing/removing the ppa from /etc/apt/sources.list.d folder.
Or easier and safer is to open the software sources application folder
(Open up the update manager and go down to settings)
The ppa is listed in 'other software', just uncheck it.
If trying through terminal to remove ppa:
```
[FONT=Ubuntu Mono]sudo apt-add-repository --remove ppa name[/FONT] 
```

Then update again.

Sidenote: When posting outputs like post#1 please use the code tag (It's the # symbol in the toolbar of the reply box)

---

### Post by MichaelFenlon on 2013-03-15
Thank you very, very, very, very, very, very, very, very, very, very, very, very, very, very, very, very, very, much deadflowr.

---

