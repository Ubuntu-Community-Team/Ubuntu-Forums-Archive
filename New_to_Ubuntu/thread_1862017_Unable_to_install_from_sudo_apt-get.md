---
title: "Unable to install from sudo apt-get"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by deveshsamaiya on 2011-10-16
I am using Ubuntu 11.10, whenever i give a command to install some package using sudo apt-get install xyz it gives me this error...

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package avr-libc

when i give sudo apt-get update command output is this 
```

Ign http://security.ubuntu.com oneiric-security InRelease           
Ign http://in.archive.ubuntu.com oneiric InRelease                  
Ign http://extras.ubuntu.com oneiric InRelease 
Hit http://security.ubuntu.com oneiric-security Release.gpg
Ign http://in.archive.ubuntu.com oneiric-updates InRelease
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://security.ubuntu.com oneiric-security Release
Ign http://in.archive.ubuntu.com oneiric-backports InRelease          
Hit http://extras.ubuntu.com oneiric Release   
Hit http://security.ubuntu.com oneiric-security/main Sources          
Hit http://in.archive.ubuntu.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://in.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://in.archive.ubuntu.com oneiric-backports Release.gpg
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://in.archive.ubuntu.com oneiric Release
Hit http://in.archive.ubuntu.com oneiric-updates Release                       
Hit http://in.archive.ubuntu.com oneiric-backports Release                     
Hit http://in.archive.ubuntu.com oneiric/main Sources                          
Hit http://in.archive.ubuntu.com oneiric/restricted Sources          
Get:1 http://in.archive.ubuntu.com oneiric/universe Sources [2,265 B]
98% [1 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Get:2 http://in.archive.ubuntu.com oneiric/multiverse Sources [2,263 B]        
99% [2 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waiting bzip2: (stdin) is not a bzip2 file.
Ign http://extras.ubuntu.com oneiric/main Translation-en_IN                    
Get:3 http://in.archive.ubuntu.com oneiric/main i386 Packages [2,640 B]        
99% [3 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:4 http://in.archive.ubuntu.com oneiric/restricted i386 Packages [2,033 B]  
Get:5 http://in.archive.ubuntu.com oneiric/universe i386 Packages [14 B]
Get:6 http://in.archive.ubuntu.com oneiric/multiverse i386 Packages [1,361 B]
Get:7 http://in.archive.ubuntu.com oneiric/main TranslationIndex [14 B]
Get:8 http://in.archive.ubuntu.com oneiric/multiverse TranslationIndex [5,310 B]
Get:9 http://in.archive.ubuntu.com oneiric/restricted TranslationIndex [14 B]  
Get:10 http://in.archive.ubuntu.com oneiric/universe TranslationIndex [1,981 B]
Get:11 http://in.archive.ubuntu.com oneiric-updates/main Sources [14 B]        
Get:12 http://in.archive.ubuntu.com oneiric-updates/restricted Sources [72 B]  
59% [12 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:13 http://in.archive.ubuntu.com oneiric-updates/universe Sources [70 B]
59% [13 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:14 http://in.archive.ubuntu.com oneiric-updates/multiverse Sources [70 B]
59% [14 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:15 http://in.archive.ubuntu.com oneiric-updates/main i386 Packages [72 B]
59% [15 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:16 http://in.archive.ubuntu.com oneiric-updates/restricted i386 Packages [14 B]
Get:17 http://in.archive.ubuntu.com oneiric-updates/universe i386 Packages [14 B]
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Get:18 http://in.archive.ubuntu.com oneiric-updates/main TranslationIndex [14 B]
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Get:19 http://in.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [14 B]
Get:20 http://in.archive.ubuntu.com oneiric-updates/universe TranslationIndex [14 B]
Get:21 http://in.archive.ubuntu.com oneiric-backports/main Sources [14 B]      
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Get:22 http://in.archive.ubuntu.com oneiric-backports/restricted i386 Packages [5,792 kB]
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Ign http://security.ubuntu.com oneiric-security/main TranslationIndex          
Ign http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Ign http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Ign http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Ign http://security.ubuntu.com oneiric-security/main Translation-en_IN         
Ign http://security.ubuntu.com oneiric-security/main Translation-en            
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en_IN   
Ign http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en_IN   
Ign http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://security.ubuntu.com oneiric-security/universe Translation-en_IN     
Ign http://security.ubuntu.com oneiric-security/universe Translation-en        
99% [22 Packages bzip2 0 B] [Waiting for headers]                   189 kB/s 0sbzip2: (stdin) is not a bzip2 file.
Get:23 http://in.archive.ubuntu.com oneiric-backports/universe i386 Packages [180 kB]
99% [23 Packages bzip2 0 B] [Waiting for headers]                   189 kB/s 0sbzip2: (stdin) is not a bzip2 file.
Get:24 http://in.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [1,583 kB]
99% [24 Packages bzip2 0 B] [Waiting for headers]                   186 kB/s 0sbzip2: (stdin) is not a bzip2 file.
Get:25 http://in.archive.ubuntu.com oneiric-backports/main TranslationIndex [20 B]
Get:26 http://in.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex [1,244 B]
Get:27 http://in.archive.ubuntu.com oneiric-backports/restricted TranslationIndex [20 B]
Get:28 http://in.archive.ubuntu.com oneiric-backports/universe TranslationIndex [5,478 B]
Hit http://in.archive.ubuntu.com oneiric-updates/restricted Sources [72 B]     
Hit http://in.archive.ubuntu.com oneiric-updates/multiverse Sources [70 B]     
Get:29 http://in.archive.ubuntu.com oneiric-updates/multiverse Translation-en_IN [20 B]
99% [29 Translation-en_IN bzip2 0 B] [Waiting for headers]          186 kB/s 0sbzip2: (stdin) is not a bzip2 file.
Get:30 http://in.archive.ubuntu.com oneiric-updates/multiverse Translation-en [20 B]
99% [30 Translation-en bzip2 0 B] [Waiting for headers]             186 kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err http://in.archive.ubuntu.com oneiric/universe Sources                      
  404  Not Found
Err http://in.archive.ubuntu.com oneiric-backports/restricted Sources          
  404  Not Found
Get:31 http://in.archive.ubuntu.com oneiric-backports/universe Sources [20 B]  
Err http://in.archive.ubuntu.com oneiric-backports/multiverse Sources          
  404  Not Found
Err http://in.archive.ubuntu.com oneiric-backports/main i386 Packages
  404  Not Found
Err http://in.archive.ubuntu.com oneiric-backports/restricted i386 Packages
  404  Not Found
Err http://in.archive.ubuntu.com oneiric-backports/universe i386 Packages
  404  Not Found
Err http://in.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
  404  Not Found
Ign http://in.archive.ubuntu.com oneiric-updates/multiverse Translation-en_IN
Fetched 7,580 kB in 1min 17s (97.5 kB/s)
W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources  404  Not Found

W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources  404  Not Found

W: Failed to fetch copy:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages  404  Not Found

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_main_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_multiverse_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_restricted_i18n_Index

W: Failed to fetch http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric-backports_universe_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

```Please help ?
???

---

### Post by ezramorris on 2011-10-16
It could be that the Indian servers are having problems. You could try a different mirror:

[LIST=1]
[*]Click on the system menu at the top right of the screen, then click "System Settings".
[*]Select "Software Sources".
[*]Under "Download from", click "Other".
[*]Click "Select Best Server".
[*]It will then test various servers to find the best one.
[/LIST]

Then try running [FONT="Courier New"]sudo apt-get update[/FONT] again.

Hope this helps,
Ezra.

---

### Post by TeoBigusGeekus on 2011-10-16
You should perhaps change your server?

---

### Post by fdrake on 2011-10-16
like the above sug you should change the server.
> 
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages  **_[COLOR="Red"]Hash Sum mismatch[/COLOR]_**

may be some errors/corruption with the server.

---

