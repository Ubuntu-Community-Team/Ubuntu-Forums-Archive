---
title: "Can update my system."
date: 2013-02-15
forum: New to Ubuntu
---

### Post by whitefish10 on 2013-02-15
Hi guys I am trying to update my system but I got the following error.

[HTML]
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

[/HTML]

I tried to use 
sudo rm -fR /var/lib/apt/lists/*

But it didnt work after I did the sudo apt-get update.

Please advise me.Thanks,

---

### Post by kc1di on 2013-02-15
in a terminal try the following then try to update again.

```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

### Post by whitefish10 on 2013-02-15
> **kc1di said:**
> in a terminal try the following then try to update again.

```
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

I got the same error.

---

### Post by schragge on 2013-02-15
Try
```
sudo rm /var/cache/apt/archives/partial/*
sudo apt-get update

```

---

### Post by ibjsb4 on 2013-02-15
Try a different download source and your original rm command with update.

---

### Post by whitefish10 on 2013-02-15
> **schragge said:**
> Try
```
sudo rm /var/cache/apt/archives/partial/*
sudo apt-get update

```

ahm@ahm-PH67A-UD3-B3:~$ sudo rm /var/cache/apt/archives/partial/*
[sudo] password for ahm: 
rm: cannot remove `/var/cache/apt/archives/partial/*': No such file or directory
ahmed@ahmed-PH67A-UD3-B3:~$ sudo apt-get update
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                       
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [31.0 kB]       
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports InRelease                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources             
Get:2 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal Release.gpg [933 B]                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [14.9 kB]   
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources             
Get:4 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports Release.gpg [933 B]       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [83.3 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages      
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [37.4 kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1,150 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [83.2 kB] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [38.0 kB]
Get:11 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal Release [49.6 kB]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates Release              
Get:12 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports Release [49.6 kB]
Get:13 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/main Sources [872 kB]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Get:14 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/restricted Sources [5,646 B]       
Get:15 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/universe Sources [5,522 kB]        
Get:16 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/multiverse Sources [166 kB]        
Get:17 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/main amd64 Packages [1,137 kB]     
Get:18 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/restricted amd64 Packages [8,369 B]
Get:19 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/universe amd64 Packages [5,274 kB] 
Get:20 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/multiverse amd64 Packages [131 kB] 
Get:21 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/main i386 Packages [1,136 kB]      
Get:22 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/restricted i386 Packages [8,387 B] 
Get:23 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/universe i386 Packages [5,285 kB]  
Get:24 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/multiverse i386 Packages [133 kB]  
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/main Translation-en                   
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/universe Translation-en               
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/main Sources                  
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/restricted Sources            
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/universe Sources              
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/multiverse Sources            
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/main amd64 Packages           
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/restricted amd64 Packages     
Get:25 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/universe amd64 Packages [168 kB]
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages     
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/main i386 Packages            
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/restricted i386 Packages      
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/universe i386 Packages        
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/multiverse i386 Packages      
Get:26 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/main Translation-en [94.7 kB]
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/universe Translation-en       
Get:27 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/main Sources [14 B]      
Get:28 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/restricted Sources [14 B]
Get:29 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/universe Sources [6,399 B]
Get:30 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/multiverse Sources [781 B]
Get:31 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/main amd64 Packages [14 B]
Get:32 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/restricted amd64 Packages [14 B]
Get:33 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/universe amd64 Packages [7,120 B]
Get:34 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages [1,118 B]
Get:35 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]
Get:36 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Get:37 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/universe i386 Packages [7,916 B]
Get:38 [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/multiverse i386 Packages [1,118 B]
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/universe Translation-en     
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Fetched 20.1 MB in 3min 35s (93.3 kB/s)
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_universe_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_multiverse_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_quantal-security_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
ahm@ahm-PH67A-UD3-B3:~$

---

### Post by kc1di on 2013-02-15
did you try a different mirror?

---

### Post by whitefish10 on 2013-02-16
> **kc1di said:**
> did you try a different mirror?

It worked, thanks.

---

### Post by kc1di on 2013-02-16
Glad it's working enjoy :)

---

