---
title: "Cheeky update manager"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by cerseibaggins on 2012-12-23
My Ubuntu update manager has been having problems for some time now.  Like many others, my update manager is refusing to cooperate with me, citing mergelists and headers as the issue.  I get the following message when I try to open it.

[SIZE="1"]'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/SIZE]

I have tried to enter the command sudo rm /var/lib/apt/ listssudo rm /var/lib/apt/lists/* -vf, but my terminal responds with this:

[SIZE="1"]sudo rm /var/lib/apt/ listssudo rm /var/lib/apt/lists/* -vf
[sudo] password for theresaabbatiello: 
rm: cannot remove `/var/lib/apt/': Is a directory
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages.IndexDiff'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources'
theresaabbatiello@Hodor:~$ sudo apt-get update
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise InRelease
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports InRelease                   
Get:1 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:2 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise Release [49.6 kB]                   
Get:5 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:6 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Get:7 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main Sources [934 kB]               
Get:8 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted Sources [5,470 B]        
Get:9 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe Sources [5,019 kB]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]         
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                     
Get:12 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                      
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:15 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                  
Get:16 [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages [7,435 B]   
Get:17 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:18 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [8,137 B]                 
Get:19 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]     
Get:20 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [6,041 B]    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [59.6 kB]      
Get:22 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages [10.8 kB]          
Get:23 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:24 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB] 
Get:25 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [10.8 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [18.9 kB]  
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,382 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [214 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:30 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB] 
Get:31 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:32 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:33 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [60.1 kB]
Get:36 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Get:37 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]    
Get:38 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Get:39 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Get:40 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Get:41 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main Sources [197 kB]      
Get:42 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted Sources [4,419 B]
Get:43 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe Sources [67.5 kB] 
Get:44 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse Sources [4,244 B]
Get:45 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main amd64 Packages [446 kB]
Get:46 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]
Get:47 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe amd64 Packages [163 kB]
Get:48 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,671 B]
Get:49 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main i386 Packages [454 kB]
Get:50 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]
Get:51 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe i386 Packages [165 kB]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [60.1 kB]
Get:53 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,675 B]
Get:54 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:55 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:56 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:57 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:58 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:59 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:60 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe Sources [20.3 kB]
Get:61 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse Sources [2,669 B]
Get:62 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main amd64 Packages [1,945 B]
Get:63 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:64 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe amd64 Packages [20.3 kB]
Get:65 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [2,489 B]
Get:66 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:67 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:68 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe i386 Packages [20.3 kB]
Get:69 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Get:70 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:71 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:72 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Get:73 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe TranslationIndex [73 B]
Get:74 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/main Translation-en [726 kB]       
Get:75 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/restricted Translation-en [2,395 B]
Get:76 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise/universe Translation-en [3,341 kB] 
Get:77 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,183 B]
Get:78 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [221 kB] 
Get:79 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/main Translation-en [219 kB]
Get:80 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/multiverse Translation-en [5,414 B]
Get:81 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/restricted Translation-en [2,082 B]
Get:82 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-updates/universe Translation-en [97.8 kB]
Get:83 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/main Translation-en [1,244 B]
Get:84 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/multiverse Translation-en [1,476 B]
Get:85 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/restricted Translation-en [14 B]
Get:86 [http://cn.archive.ubuntu.com](http://cn.archive.ubuntu.com) precise-backports/universe Translation-en [14.1 kB]
Get:87 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:88 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [61.1 kB]
Get:89 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,392 B]
Get:90 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:91 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:92 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:93 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:94 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [104 kB]
Get:95 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [995 B]
Get:96 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [978 B]
Get:97 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [36.8 kB]
Fetched 25.6 MB in 20s (1,239 kB/s)                                            
W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index](http://cn.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/cn.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.[/SIZE]

I'm not sure what to do from here.  Any help would be appreciated.  I'm very new to ubuntu and not techy at all. :( I feel kind of lost with all this. I'm sorry if somehow has already posted about this type of error before, and I failed to see it.

Thanks.

---

### Post by ibjsb4 on 2012-12-23
The command should read

```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

---

### Post by NikTh on 2012-12-23
**Please use the [CODE] tags for code.. [See here how]("http://i.stack.imgur.com/zADbK.png")**

And try the command as [ibjsb4]("http://ubuntuforums.org/member.php?u=1729120") stated . Copy and paste the command from here to your terminal.

Thank you.

---

### Post by cerseibaggins on 2012-12-23
Thank you! That seemed to do the trick temporarily, but now I'm receiving this message:

W:Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index](http://cn.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/cn.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index
, E:Some index files failed to download. They have been ignored, or old ones used instead.

My computer also tells me to check my network connection.  My network connection is fine; however, I'm starting to think that my location might be the problem.  I live in China, and I wonder if the firewall is the source of my problems.  

Any thoughts?

---

### Post by NikTh on 2012-12-24
Hi , 
you can try to change the location for the server where Ubuntu downloads the sources - lists . 

Open Update Manager and click "Settings" and at the first Tab , Change the **Download From:** to the **"main"** server. 
Then open a terminal and do ```
sudo apt-get update
``` and see.

Thanks

---

