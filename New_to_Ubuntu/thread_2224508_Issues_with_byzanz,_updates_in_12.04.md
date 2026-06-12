---
title: "Issues with byzanz, updates in 12.04"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by connor.ruebusch on 2014-05-16
I'm trying to install byzanz so that I have a method of capturing GIFs on my Ubuntu netbook (I'm running 12.04). This seems to be the best method I've come across for Ubuntu; on Windows I use GifCam, which is very simple to use, but no such program seems to exist for Linux systems--if one does, please recommend it to me! 

Anyway, in trying to install byzanz I've come across a couple problems. I'm using the following commands in the terminal. 

sudo add-apt-repository -y ppa:fossfreedom/byzanz
sudo apt-get update
sudo apt-get install -y byzanz

Here's what I get in return for each of those commands, respectively. 

> sudo add-apt-repository -y ppa:fossfreedom/byzanz

gives me

> gpg: keyring `/tmp/tmpMxOMBx/secring.gpg' created
gpg: keyring `/tmp/tmpMxOMBx/pubring.gpg' created
gpg: requesting key F4FE239D from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpMxOMBx/trustdb.gpg: trustdb created
gpg: key F4FE239D: public key "Launchpad PPA for fossfreedom" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

> sudo apt-get update

gives me 

> Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan Release.gpg                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan Release                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public Sources             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public amd64 Packages      
Hit [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public i386 Packages       
Ign [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public TranslationIndex    
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [104 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [2,320 B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [385 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [458 kB]         
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [93.1 kB]
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex [2,320 B]        
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex [2,320 B]        
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [2,320 B]                 
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [2,320 B]          
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [414 kB] 
60% [15 Sources bzip2 0 B] [10 Sources 181 kB/458 kB 39%] [17 Packages 56.9 kB/bzip2: (stdin) is not a bzip2 file.
60% [16 Packages bzip2 0 B] [10 Sources 181 kB/458 kB 39%] [17 Packages 56.9 kBbzip2: (stdin) is not a bzip2 file.
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Ign [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public Translation-en_US   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://asus.archive.canonical.com](http://asus.archive.canonical.com) precise-annan/public Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
81% [16 Packages xz 0 B] [10 Sources 286 kB/458 kB 63%] [17 Packages 280 kB/414/usr/bin/xz: (stdin): File format not recognized
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [97.6 kB]
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex [2,320 B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [2,320 B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [179 kB]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [8,028 B]  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [107 kB]     
90% [16 Packages lzma 0 B] [10 Sources bzip2 0 B] [26 Sources 48.7 kB/107 kB 45/usr/bin/lzma: (stdin): File format not recognized
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [777 kB]  
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [57.1 kB]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [12.2 kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [240 kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [806 kB]   
Get:32 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [2,320 B]           
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [246 kB]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en [347 kB]  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Fetched 4,512 kB in 15s (289 kB/s)                                             
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: Unknown error executing gpgv
W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu/dists/precise/Release.gpg](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu/dists/precise/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_Release.gpg).

W: Failed to fetch [http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/ehoover/compholio/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_ehoover_compholio_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch [http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/gwendal-lebihan-dev?cinnamon-stable/ppa/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu/dists/precise/main/i18n/Index](http://ppa.launchpad.net/fossfreedom/byzanz/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/ppa.launchpad.net_fossfreedom_byzanz_ubuntu_dists_precise_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.



Now obviously there are some errors there. These gave me some trouble a while back, I think because I accidentally had a partial install of Cinnamon on my system, but I thought the issue had been resolved. Apparently it's still there, but whereas before is was keeping me from installing updates, I've not had an issue with that again until now. 

Finally, 

> sudo apt-get install -y byzanz

returns

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_gwendal-lebihan-dev?cinnamon-stable_ppa_ubuntu_dists_precise_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.



I'm not really sure what's caused this problem to crop up again when I was sure it had been resolved, but there it is. If it helps to look at the process of resolving it last time, here's the link to that thread: [http://ubuntuforums.org/showthread.php?t=2199241&page=2&p=12942289#post12942289](http://ubuntuforums.org/showthread.php?t=2199241&page=2&p=12942289#post12942289)

Thanks!

---

### Post by cariboo on 2014-05-25
Do you get the error every time you run:

```
sudo apt-get update
```

---

