---
title: "Can't update my system."
date: 2013-02-24
forum: New to Ubuntu
---

### Post by whitefish10 on 2013-02-24
I cant update me system and I search google for solutions but it didnt work. Here:-

```
ahm@ahm-PH67A-UD3-B3:~$ sudo apt-get update
Get:1 [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease [2,840 B]
Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources [540 B]               
Get:3 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages [583 B]        
Get:4 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [725 B]         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                
Get:5 [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg [933 B]                 
Get:6 [http://archive.canonical.com](http://archive.canonical.com) quantal Release [7,078 B]                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Get:8 [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages [3,466 B]    
Get:9 [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages [4,234 B]     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease                        
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                    
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                    
Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release [11.9 kB]                      
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                      
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release [11.9 kB]                      
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [3,537 B]                 
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [7,467 B]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports InRelease                      
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [7,464 B]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security InRelease                       
Get:18 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources [2,422 B]                 
Get:19 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages [3,782 B]          
Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages [3,779 B]           
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg [933 B]                   
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources [9,701 B]                 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal InRelease                        
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg [933 B]           
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages [22.9 kB]          
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release.gpg [933 B]         
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release.gpg [933 B]          
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release [49.6 kB]                     
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages [22.9 kB]           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release [49.6 kB]             
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release [49.6 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security Release [49.6 kB]   
Get:32 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release.gpg [316 B]
Get:33 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release.gpg [316 B]           
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Sources [872 kB]                 
Get:35 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release [11.9 kB]            
Get:36 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release [11.9 kB]             
Get:37 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main amd64 Packages [525 B]   
Get:38 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main i386 Packages [521 B]    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Sources [5,646 B]  
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Sources [5,522 kB]           
Get:41 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main amd64 Packages [733 B]
Get:42 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main i386 Packages [973 B]
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en_US           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en              
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en_US           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en              
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Sources [166 kB]           
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages [1,137 kB]        
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages [8,369 B]   
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages [5,274 kB]    
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages [131 kB]    
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main i386 Packages [1,136 kB]         
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted i386 Packages [8,387 B]    
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe i386 Packages [5,285 kB]     
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse i386 Packages [133 kB]     
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en [660 kB]          
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en [100 kB]    
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en [2,575 B]   
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en [3,648 kB]    
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Sources [79.7 kB]        
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Sources [1,302 B]  
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Sources [78.9 kB]    
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Sources [2,941 B]  
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages [205 kB]  
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages [3,048 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages [168 kB]
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,948 B]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main i386 Packages [204 kB]   
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted i386 Packages [3,067 B]
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe i386 Packages [169 kB]
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,098 B]
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en [97.9 kB] 
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en [4,499 B]
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en [915 B]
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en [89.7 kB]
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Sources [14 B]         
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Sources [14 B]   
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Sources [7,732 B]  
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Sources [781 B]  
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main amd64 Packages [14 B]  
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted amd64 Packages [14 B]
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe amd64 Packages [11.3 kB]
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse amd64 Packages [1,118 B]
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]   
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Get:82 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe i386 Packages [12.1 kB]
Get:83 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse i386 Packages [1,118 B]
Get:84 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en [14 B]  
Get:85 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en [594 B]
Get:86 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en [14 B]
Get:87 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en [9,619 B]
Get:88 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Sources [32.6 kB]       
Get:89 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Sources [14 B]    
Get:90 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Sources [15.4 kB]   
Get:91 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Sources [691 B]   
Get:92 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main amd64 Packages [88.5 kB]
Get:93 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Get:94 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe amd64 Packages [41.6 kB]
Get:95 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse amd64 Packages [1,146 B]
Get:96 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main i386 Packages [88.0 kB] 
Get:97 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:98 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe i386 Packages [42.1 kB]
Get:99 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse i386 Packages [1,400 B]
Get:100 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en [46.7 kB]
Get:101 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en [587 B]
Get:102 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en [14 B]
Get:103 [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en [25.4 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-security/universe Translation-en_US
Fetched 26.0 MB in 1min 16s (338 kB/s)
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal-security_multiverse_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```


Please advise me. Thanks,

---

### Post by plucky on 2013-02-24
> W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal-security_multiverse_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

Open a terminal and run ```
sudo rm /var/lib/apt/lists/partial/* -vf
``` then run ```
sudo apt-get update
``` and see if you get the same error.

Good Luck

---

### Post by whitefish10 on 2013-02-25
> **plucky said:**
> Open a terminal and run ```
sudo rm /var/lib/apt/lists/partial/* -vf
``` then run ```
sudo apt-get update
``` and see if you get the same error.

Good Luck

I got the same error.

---

### Post by matt_symes on 2013-02-25
Hi

same command again

```
sudo rm /var/lib/apt/lists/partial/* -vrf
```

Then pick a different server using update manager and then

```
sudo apt-get update
```

Kind regards

---

### Post by whitefish10 on 2013-02-25
> **matt_symes said:**
> Hi

same command again

```
sudo rm /var/lib/apt/lists/partial/* -vrf
```Then pick a different server using update manager and then

```
sudo apt-get update
```Kind regards

```

ahm@ahm-PH67A-UD3-B3:~$ sudo rm /var/lib/apt/lists/partial/* -vrf
[sudo] password for ahm: 
removed `/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal-backports_Release.gpg.reverify'
removed `/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal_Release.gpg.reverify'
removed `/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_quantal-security_multiverse_source_Sources.decomp.FAILED'
removed `/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages'
removed `/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages.decomp.FAILED'
removed `/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages'
removed `/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages.decomp.FAILED'
removed `/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_source_Sources'
removed `/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_source_Sources.decomp.FAILED'
ahmed@ahmed-PH67A-UD3-B3:~$ sudo apt-get update
Ign http://ubuntu.qualitynet.net quantal InRelease
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://archive.canonical.com quantal InRelease                             
Hit http://extras.ubuntu.com quantal Release.gpg                               
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://archive.canonical.com quantal Release                               
Hit http://repo.steampowered.com precise InRelease                             
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Get:1 http://repo.steampowered.com precise/steam Sources [538 B]               
Ign http://ubuntu.qualitynet.net quantal-updates InRelease                     
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Ign http://ppa.launchpad.net quantal InRelease                                 
Get:2 http://repo.steampowered.com precise/steam amd64 Packages [594 B]        
Get:3 http://repo.steampowered.com precise/steam i386 Packages [737 B]         
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Ign http://ubuntu.qualitynet.net quantal-backports InRelease                   
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Ign http://ppa.launchpad.net quantal InRelease                                 
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://ppa.launchpad.net quantal/main Sources                              
Ign http://ubuntu.qualitynet.net quantal-security InRelease                    
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Get:4 http://ubuntu.qualitynet.net quantal Release.gpg [933 B]                 
Get:5 http://ubuntu.qualitynet.net quantal-updates Release.gpg [933 B]         
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Get:6 http://ubuntu.qualitynet.net quantal-backports Release.gpg [933 B]
Get:7 http://ubuntu.qualitynet.net quantal-security Release.gpg [198 B]        
Ign https://private-ppa.launchpad.net quantal InRelease                        
Get:8 http://ubuntu.qualitynet.net quantal Release [49.6 kB]                   
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Get:9 http://ubuntu.qualitynet.net quantal-updates Release [49.6 kB]           
Ign https://private-ppa.launchpad.net quantal InRelease                        
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://archive.canonical.com quantal/partner Translation-en                
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Get:10 http://ubuntu.qualitynet.net quantal-backports Release [49.6 kB]
Get:11 http://ubuntu.qualitynet.net quantal-security Release [49.6 kB]         
Hit https://private-ppa.launchpad.net quantal Release.gpg                      
Hit https://private-ppa.launchpad.net quantal Release.gpg                      
Hit https://private-ppa.launchpad.net quantal Release                          
Get:12 http://ubuntu.qualitynet.net quantal/main Sources [872 kB]     
Hit https://private-ppa.launchpad.net quantal Release                          
Get:13 http://ubuntu.qualitynet.net quantal/restricted Sources [5,646 B]       
Get:14 http://ubuntu.qualitynet.net quantal/universe Sources [5,522 kB]        
Hit https://private-ppa.launchpad.net quantal/main amd64 Packages              
Hit https://private-ppa.launchpad.net quantal/main i386 Packages               
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit https://private-ppa.launchpad.net quantal/main amd64 Packages              
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit https://private-ppa.launchpad.net quantal/main i386 Packages               
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Get:15 http://ubuntu.qualitynet.net quantal/multiverse Sources [166 kB]        
Get:16 http://ubuntu.qualitynet.net quantal/main amd64 Packages [1,137 kB]     
Get:17 http://ubuntu.qualitynet.net quantal/restricted amd64 Packages [8,369 B]
Get:18 http://ubuntu.qualitynet.net quantal/universe amd64 Packages [5,274 kB] 
Ign https://private-ppa.launchpad.net quantal/main Translation-en_US           
Ign https://private-ppa.launchpad.net quantal/main Translation-en              
Ign https://private-ppa.launchpad.net quantal/main Translation-en_US           
Ign https://private-ppa.launchpad.net quantal/main Translation-en              
Get:19 http://ubuntu.qualitynet.net quantal/multiverse amd64 Packages [131 kB] 
Get:20 http://ubuntu.qualitynet.net quantal/main i386 Packages [1,136 kB]      
Get:21 http://ubuntu.qualitynet.net quantal/restricted i386 Packages [8,387 B] 
Get:22 http://ubuntu.qualitynet.net quantal/universe i386 Packages [5,285 kB]  
Get:23 http://ubuntu.qualitynet.net quantal/multiverse i386 Packages [133 kB]  
Get:24 http://ubuntu.qualitynet.net quantal/main Translation-en [660 kB]       
Get:25 http://ubuntu.qualitynet.net quantal/multiverse Translation-en [100 kB] 
Get:26 http://ubuntu.qualitynet.net quantal/restricted Translation-en [2,575 B]
Get:27 http://ubuntu.qualitynet.net quantal/universe Translation-en [3,648 kB] 
Get:28 http://ubuntu.qualitynet.net quantal-updates/main Sources [2,378 B]     
Get:29 http://ubuntu.qualitynet.net quantal-updates/restricted Sources [14 B]  
Get:30 http://ubuntu.qualitynet.net quantal-updates/universe Sources [14 B]    
Get:31 http://ubuntu.qualitynet.net quantal-updates/multiverse Sources [14 B]  
Get:32 http://ubuntu.qualitynet.net quantal-updates/main amd64 Packages [4,876 B]
Get:33 http://ubuntu.qualitynet.net quantal-updates/restricted amd64 Packages [14 B]
Get:34 http://ubuntu.qualitynet.net quantal-updates/universe amd64 Packages [2,561 B]
Get:35 http://ubuntu.qualitynet.net quantal-updates/multiverse amd64 Packages [14 B]
Get:36 http://ubuntu.qualitynet.net quantal-updates/main i386 Packages [4,879 B]
Get:37 http://ubuntu.qualitynet.net quantal-updates/restricted i386 Packages [14 B]
Get:38 http://ubuntu.qualitynet.net quantal-updates/universe i386 Packages [2,571 B]
Get:39 http://ubuntu.qualitynet.net quantal-updates/multiverse i386 Packages [14 B]
Get:40 http://ubuntu.qualitynet.net quantal-updates/main Translation-en [97.9 kB]
Get:41 http://ubuntu.qualitynet.net quantal-updates/multiverse Translation-en [4,499 B]
Get:42 http://ubuntu.qualitynet.net quantal-updates/restricted Translation-en [915 B]
Get:43 http://ubuntu.qualitynet.net quantal-updates/universe Translation-en [89.7 kB]
Get:44 http://ubuntu.qualitynet.net quantal-backports/main Sources [14 B]      
Get:45 http://ubuntu.qualitynet.net quantal-backports/restricted Sources [14 B]
Get:46 http://ubuntu.qualitynet.net quantal-backports/universe Sources [2,244 B]
Get:47 http://ubuntu.qualitynet.net quantal-backports/multiverse Sources [14 B]
Get:48 http://ubuntu.qualitynet.net quantal-backports/main amd64 Packages [14 B]
Get:49 http://ubuntu.qualitynet.net quantal-backports/restricted amd64 Packages [14 B]
Get:50 http://ubuntu.qualitynet.net quantal-backports/universe amd64 Packages [1,066 B]
Get:51 http://ubuntu.qualitynet.net quantal-backports/multiverse amd64 Packages [14 B]
Get:52 http://ubuntu.qualitynet.net quantal-backports/main i386 Packages [14 B]
Get:53 http://ubuntu.qualitynet.net quantal-backports/restricted i386 Packages [14 B]
Get:54 http://ubuntu.qualitynet.net quantal-backports/universe i386 Packages [1,066 B]
Get:55 http://ubuntu.qualitynet.net quantal-backports/multiverse i386 Packages [14 B]
Get:56 http://ubuntu.qualitynet.net quantal-backports/main Translation-en [14 B]
Get:57 http://ubuntu.qualitynet.net quantal-backports/multiverse Translation-en [594 B]
Get:58 http://ubuntu.qualitynet.net quantal-backports/restricted Translation-en [14 B]
Get:59 http://ubuntu.qualitynet.net quantal-backports/universe Translation-en [9,619 B]
Get:60 http://ubuntu.qualitynet.net quantal-security/main Sources [14 B]       
Get:61 http://ubuntu.qualitynet.net quantal-security/restricted Sources [14 B] 
Get:62 http://ubuntu.qualitynet.net quantal-security/universe Sources [14 B]   
Get:63 http://ubuntu.qualitynet.net quantal-security/multiverse Sources [14 B] 
Get:64 http://ubuntu.qualitynet.net quantal-security/main amd64 Packages [14 B]
Get:65 http://ubuntu.qualitynet.net quantal-security/restricted amd64 Packages [14 B]
Get:66 http://ubuntu.qualitynet.net quantal-security/universe amd64 Packages [14 B]
Get:67 http://ubuntu.qualitynet.net quantal-security/multiverse amd64 Packages [14 B]
Get:68 http://ubuntu.qualitynet.net quantal-security/main i386 Packages [14 B] 
Get:69 http://ubuntu.qualitynet.net quantal-security/restricted i386 Packages [14 B]
Get:70 http://ubuntu.qualitynet.net quantal-security/universe i386 Packages [14 B]
Get:71 http://ubuntu.qualitynet.net quantal-security/multiverse i386 Packages [14 B]
Get:72 http://ubuntu.qualitynet.net quantal-security/main Translation-en [48.0 kB]
Get:73 http://ubuntu.qualitynet.net quantal-security/multiverse Translation-en [587 B]
Get:74 http://ubuntu.qualitynet.net quantal-security/restricted Translation-en [14 B]
Get:75 http://ubuntu.qualitynet.net quantal-security/universe Translation-en [25.5 kB]
Ign http://ubuntu.qualitynet.net quantal/main Translation-en_US                
Ign http://ubuntu.qualitynet.net quantal/multiverse Translation-en_US
Ign http://ubuntu.qualitynet.net quantal/restricted Translation-en_US
Ign http://ubuntu.qualitynet.net quantal/universe Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-updates/main Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-updates/multiverse Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-updates/restricted Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-updates/universe Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-backports/main Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-backports/multiverse Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-backports/restricted Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-backports/universe Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-security/main Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-security/multiverse Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-security/restricted Translation-en_US
Ign http://ubuntu.qualitynet.net quantal-security/universe Translation-en_US
Fetched 24.6 MB in 1min 18s (314 kB/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
ahm@ahm-PH67A-UD3-B3:~$ 


```

---

### Post by plucky on 2013-02-25
You are mixing Quantal and Precise sources.

> Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages [594 B]        
Get:3 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [737 B]  

> W: Failed to fetch gzip:/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages  Hash Sum mismatch

Open Software Sources and disable the Precise repositories.

Then run the "rm" command again and then run the "apt-get update" command.


Good Luck

---

