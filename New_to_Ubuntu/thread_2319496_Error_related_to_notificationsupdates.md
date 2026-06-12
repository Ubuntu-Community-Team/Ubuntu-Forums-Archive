---
title: "Error related to notifications/updates"
date: 2016-04-04
forum: New to Ubuntu
---

### Post by mishaal2 on 2016-04-04
Hi all,

I installed Ubuntu a few months ago, but have started using it more and more recently. I noticed when I turned my computer on today that the notifications symbol had some error, shown in the attached picture (with the error message)

I have tried clicking updates/etc. and the one probably-useful error message I have gotten is: 
[B]
W:Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

[/B]Can anyone explain what this means and how to fix this? 

Thank you very much!

---

### Post by mishaal2 on 2016-04-04
Also, if it helps, here is the output I get when I run "sudo apt-get update"

```
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [110 kB]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [35.2 kB]    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,750 B]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [450 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [126 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,991 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [423 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [126 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,175 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 1,380 kB in 7s (192 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by v3.xx on 2016-04-04
The 'claudiocn' ppa has not been updated since 2011.  This ppa is dead and you
need to remove or disable it.

[http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/](http://ppa.launchpad.net/claudiocn/slm/ubuntu/dists/)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

### Post by mishaal2 on 2016-04-04
Thank you [**[COLOR=#000000]v3.xx[/COLOR]**]("http://ubuntuforums.org/member.php?u=1937239"), I believe that has solved it!

---

### Post by Bucky Ball on 2016-04-05
It should have. Good news. If you are not getting any issues please mark the thread as solved (see link in my signature below). Thanks.

---

### Post by mishaal2 on 2016-04-09
Update: I noticed when I was starting my computer today (and this seems to happen every time I restart) it shows the error icon for a few minutes. I'd say about 2-3 minutes. Attached picture[ATTACH=CONFIG]268271[/ATTACH]. Is this typical behaviour/just the time it takes to load? Information about if this is "normal" would be greatly appreciated!

---

### Post by v3.xx on 2016-04-09
> **mishaal2 said:**
> Update: I noticed when I was starting my computer today (and this seems to happen every time I restart) it shows the error icon for a few minutes. I'd say about 2-3 minutes. Attached picture[ATTACH=CONFIG]268271[/ATTACH]. Is this typical behaviour/just the time it takes to load? Information about if this is "normal" would be greatly appreciated!
No this is not typical. 
Run another update in terminal and look for errors.

---

### Post by mishaal2 on 2016-04-09
> **v3.xx said:**
> No this is not typical. 
Run another update in terminal and look for errors.

Here is the output of sudo apt-get update; I don't see "Error" anywhere... This was run, however, just now - when the error icon was not there. I will see if I can run this when the error icon is present, and see if/how that gives a different output

```
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [110 kB]         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease [65.9 kB]        
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B]  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [35.2 kB]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,764 B]  
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [454 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [270 kB]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [126 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [152 kB]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,982 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [427 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5,928 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [750 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [126 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,172 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [358 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [716 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [359 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [374 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [7,227 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [187 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [8,904 B]    
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [34.5 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [9,967 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [41.5 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,571 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [9,986 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [41.5 kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 4,918 kB in 14s (346 kB/s)                                             
Reading package lists... Done


```

---

### Post by mishaal2 on 2016-04-09
**Update:** Just restarted my computer, the error symbol is still there, and I ran sudo apt-get update  and there are still no errors in the output

---

### Post by v3.xx on 2016-04-09
Try reinstalling update-manager.

```
sudo apt-get install --reinstall update-manager
```

---

### Post by mishaal2 on 2016-04-09
> **v3.xx said:**
> Try reinstalling update-manager.

```
sudo apt-get install --reinstall update-manager
```

Ran this and restarted my machine; the error symbol is still there, unfortunately...

---

### Post by v3.xx on 2016-04-09
Go to your file system and look at /var/log/apt/term.log for any errors.  No need to read the whole log (they are a mile long), scroll to the bottom and check todays events for clues.

To be honest with you.  Things that are broke, usually stay broke.  I'm not real sure what we are looking for, so I'm doing a bit of fishing. It may be better for you to start a new thread for this problem and pull in others that may of experience this.

---

### Post by mishaal2 on 2016-04-10
Thanks for helping to investigate, **v3.xx**. 

Unfortunately, I don't think I see any errors in the log file, either. 

I have noticed that when I turned on my laptop just now, it hasn't shown up (yet?) so maybe some update from earlier+restarting has taken care of it...or maybe it will show up in a few seconds. Either way, I will continue to investigate, but, as it is not hindering anything (to my knowledge), I won't waste too much time on trying to fix it.

---

