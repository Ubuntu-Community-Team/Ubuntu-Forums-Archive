---
title: "Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by megabean on 2013-06-20
Hi all,

Also new to the Ubuntu world I did an automatic update install and came to the brokencount>0 problem. Reading through various posts and answers, I also did the sudo apt-get install -f and this is the result. Now i'm completely stuck and hope somebody here can help me fix this problem. If you need more information, ask away and many thanks to those who can offer any kind of help,,,thanks

megabean@megabean-AOA110:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia k3b-data kde-l10n-engb kde-l10n-zhcn
  kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n libflac++6 libiso9660-8
  libvcdinfo0 linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic vcdimager
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.5.0-36 linux-headers-3.5.0-36-generic linux-headers-generic
The following NEW packages will be installed
  linux-headers-3.5.0-36 linux-headers-3.5.0-36-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 2 newly installed, 0 to remove and 26 not upgraded.
3 not fully installed or removed.
Need to get 13.1 MB of archives.
After this operation, 70.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-proposed/main linux-headers-3.5.0-36 all 3.5.0-36.57 [12.1 MB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-proposed/main linux-headers-3.5.0-36-generic i386 3.5.0-36.57 [957 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-proposed/main linux-headers-generic i386 3.5.0.36.52 [2,258 B]
Fetched 13.1 MB in 17s (735 kB/s)                                                
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by Impavidus on 2013-06-21
It cannot find the package info file. Whay happens if you first do```
sudo apt-get update
```and then try again?

---

### Post by fantab on 2013-06-21
You can only run one 'apt' manager at a given time. If you have anything like 'Software Center' or Update-manager running then close them first.

Now run the following in Terminal and post their output:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by megabean on 2013-06-21
this is what i get when running sudo apt-get update,

Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release.gpg [933 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                     
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]    
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release.gpg [933 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed Release.gpg [933 B]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release                      
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [1,833 B] 
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [51.0 kB]       
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [696 B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [19.2 kB]  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [142 kB] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [3,531 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [54.3 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,396 B]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release [49.6 kB]        
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed Release [49.6 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en [75.4 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Sources                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_GB                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted i386 Packages              
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe i386 Packages                
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en [33.2 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en_GB                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en               
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Sources [2,564 B]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Sources [105 kB]      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_GB         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_GB     
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Sources [3,998 B]
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Sources [88.8 kB] 
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main i386 Packages [270 kB]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted i386 Packages [4,841 B]
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe i386 Packages [195 kB]
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [10.9 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en [102 kB]
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Sources [14 B]      
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Sources [14 B]
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Sources [15.6 kB]
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Sources [1,879 B]
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe i386 Packages [20.5 kB]
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse i386 Packages [2,184 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en [17.6 kB]
Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted Sources [14 B] 
Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main Sources [16.2 kB]    
Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse Sources [14 B] 
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe Sources [8,085 B]
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted i386 Packages [14 B]
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main i386 Packages [38.2 kB]
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse i386 Packages [14 B]
Get:45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe i386 Packages [13.2 kB]
Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main Translation-en [22.1 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted Translation-en    
Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe Translation-en [7,093 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted Translation-en_GB 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe Translation-en_GB   
Fetched 1,531 kB in 36s (41.7 kB/s)                                            
Reading package lists... Done

---

### Post by megabean on 2013-06-21
this is what i get  when i run sudo apt-get upgrade

megabean@megabean-AOA110:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 linux-headers-generic : Depends: linux-headers-3.5.0-34-generic but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by megabean on 2013-06-21
and this is what i get when running sudo apt-get -f install

megabean@megabean-AOA110:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  calligra-l10n-engb cdparanoia k3b-data kde-l10n-engb kde-l10n-zhcn kdevelop-l10n
  kdevelop-php-docs-l10n kdevelop-php-l10n libflac++6 libiso9660-8 libvcdinfo0
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic vcdimager
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.5.0-36 linux-headers-3.5.0-36-generic linux-headers-generic
The following NEW packages will be installed
  linux-headers-3.5.0-36 linux-headers-3.5.0-36-generic
The following packages will be upgraded:
  linux-headers-generic
1 upgraded, 2 newly installed, 0 to remove and 30 not upgraded.
3 not fully installed or removed.
Need to get 0 B/13.1 MB of archives.
After this operation, 70.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)


I hope this helps
Thanks for the support so far ;)

---

### Post by ro12 on 2013-06-22
I am having almost the exact same problem as you too!

---

### Post by megabean on 2013-06-22
Let's hope somebody out there in Ubuntu world can help us with our problem,,, fingers crossed, and toes   [-o<

---

### Post by perspectoff on 2013-06-22
From Ubuntuguide:

[http://ubuntuguide.org/wiki/Ubuntu_Raring_Packages#Repair_broken_packages](http://ubuntuguide.org/wiki/Ubuntu_Raring_Packages#Repair_broken_packages)

Try rebuilding the headers:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by megabean on 2013-06-22
done the two commands and this is the result:

megabean@megabean-AOA110:~$ sudo rm /var/lib/apt/lists/* -vf
[sudo] password for megabean: 
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_source_Sources'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_Release.gpg'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_quantal_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_quantal_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_quantal_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-backports_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-proposed_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_quantal-updates_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_universe_source_Sources'
megabean@megabean-AOA110:~$ sudo apt-get update
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release.gpg [933 B]                 
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]          
Get:4 [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg [933 B]                 
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release.gpg [933 B]         
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]            
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release [11.9 kB]                       
Get:8 [http://archive.canonical.com](http://archive.canonical.com) quantal Release [7,078 B]                   
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release.gpg [933 B]       
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed Release.gpg [933 B]       
Get:11 [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources [3,144 B]          
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal Release [49.6 kB]                  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [1,833 B]
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources [2,422 B]                 
Get:15 [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages [5,148 B]    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [51.0 kB]      
Get:17 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages [3,779 B]           
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates Release [49.6 kB]          
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [696 B]  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [19.2 kB]  
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports Release [49.6 kB]        
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [142 kB] 
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed Release [49.6 kB]         
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [3,531 B]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Sources [5,646 B]       
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [54.3 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_GB             
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Sources [872 kB]              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_GB                    
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,396 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en [75.4 kB]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en [587 B]
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Sources [166 kB]        
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en [1,066 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en [33.2 kB]
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Sources [5,522 kB]        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_GB         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_GB     
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main i386 Packages [1,136 kB]      
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted i386 Packages [8,387 B] 
Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe i386 Packages [5,285 kB]  
Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse i386 Packages [133 kB]  
Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en_GB [96.4 kB]   
Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/main Translation-en [660 kB]       
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en_GB [80.7 kB]
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en [100 kB] 
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en_GB [2,406 B]
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en [2,575 B]
Get:45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en_GB [5,492 B]
Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en [3,648 kB] 
Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Sources [2,564 B]
Get:48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Sources [105 kB]      
Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Sources [3,998 B]
Get:50 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Sources [88.8 kB] 
Get:51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main i386 Packages [270 kB]
Get:52 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted i386 Packages [4,841 B]
Get:53 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe i386 Packages [195 kB]
Get:54 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [10.9 kB]
Get:55 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en [132 kB]
Get:56 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en [6,183 B]
Get:57 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en [1,477 B]
Get:58 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en [102 kB]
Get:59 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Sources [14 B]      
Get:60 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Sources [14 B]
Get:61 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Sources [15.6 kB]
Get:62 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Sources [1,879 B]
Get:63 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]
Get:64 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Get:65 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe i386 Packages [20.5 kB]
Get:66 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse i386 Packages [2,184 B]
Get:67 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en [14 B]
Get:68 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en [1,706 B]
Get:69 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en [14 B]
Get:70 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en [17.6 kB]
Get:71 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted Sources [14 B] 
Get:72 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main Sources [16.2 kB]    
Get:73 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse Sources [14 B] 
Get:74 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe Sources [8,085 B]
Get:75 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted i386 Packages [14 B]
Get:76 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main i386 Packages [38.2 kB]
Get:77 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse i386 Packages [14 B]
Get:78 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe i386 Packages [13.2 kB]
Get:79 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main Translation-en [22.1 kB]
Get:80 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse Translation-en [14 B]
Get:81 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted Translation-en [14 B]
Get:82 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe Translation-en [7,093 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-proposed/universe Translation-en_GB
Fetched 19.5 MB in 2min 1s (160 kB/s)
Reading package lists... Done
megabean@megabean-AOA110:~$ 

will do a re-boot now and see if the problem has disappeared

---

### Post by megabean on 2013-06-22
The no-entry icon is still there, also when i run the update manager, I get the message: package system is broken with these details: 
The following packages have unmet dependencies:
linux-headers-generic: Depends: linux-headers-3.5.0-34-generic but it is not installed.

The latest version installed that i found is 3.5.0-33 and that is about as far as I got with my investigation.
hope this helps
cheers
re-editing this post,,,just checked again and 3.5.0-34 is installed,,,now i'm really lost..

---

