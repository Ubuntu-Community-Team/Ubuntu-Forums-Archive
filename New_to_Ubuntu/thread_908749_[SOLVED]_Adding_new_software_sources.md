---
title: "[SOLVED] Adding new software sources"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-02
I have Linux Mint.
I want to add the following sources to get Banshee:

```
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
```

Usually, in Ubuntu, I'd just go to admin > software sources, but linux mint does not have this. Also, I tried adding it in the Repos in synaptic, but I kept getting some error. Any help?

---

### Post by iaculallad on 2008-09-02
> **adobrakic said:**
> I have Linux Mint.
I want to add the following sources to get Banshee:

```
deb http://ppa.launchpad.net/banshee-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/banshee-team/ubuntu hardy main
```

Usually, in Ubuntu, I'd just go to admin > software sources, but linux mint does not have this. Also, I tried adding it in the Repos in synaptic, but I kept getting some error. Any help?

Try this in your terminal:

```
gksudo gedit /etc/apt/sources.list
```

and append the lines of text below on the last part of the file:

> deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main


Save and Close, and:

```
sudo apt-get update && sudo apg-get upgrade
```

---

### Post by DMK62 on 2008-09-02
You can always add them by editing your sources.list file

From the terminal

gksu gedit /etc/apt/sources.list

then run sudo apt-get update

Dale

I just checked the default Mint 5 repos and banshee is available, its version 0.13.2 +dfsg-9

Note on previous post Mint handles updates a bit differently than Ubuntu so I would not recommend running the apt-get upgrade command.

---

### Post by adobrakic on 2008-09-02
Yeah, i saw that version is available, but version 1.2 or something is out.

Also, i get this error after adding those two things to the bottom of source.list:

```

ado@ado-desktop ~ $ sudo apt-get update && sudo apg-get upgrade
Ign http://ppa.launchpad.net hardy Release.gpg
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Hit http://packages.medibuntu.org hardy Release.gpg                            
Ign http://packages.linuxmint.com elyssa Release.gpg                           
Hit http://archive.ubuntu.com hardy Release.gpg                                
Ign http://archive.ubuntu.com hardy/main Translation-en_US                     
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Hit http://wine.budgetdedicated.com hardy Release.gpg                          
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US               
Ign http://ppa.launchpad.net banshee Release.gpg                               
Ign http://ppa.launchpad.net banshee/main Translation-en_US                    
Hit http://archive.canonical.com hardy Release                                 
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://packages.linuxmint.com elyssa/main Translation-en_US                
Ign http://packages.linuxmint.com elyssa/upstream Translation-en_US            
Ign http://packages.linuxmint.com elyssa/import Translation-en_US              
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US               
Ign http://archive.ubuntu.com hardy/universe Translation-en_US                 
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US               
Hit http://archive.ubuntu.com hardy-updates Release.gpg                        
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US             
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US         
Hit http://wine.budgetdedicated.com hardy Release                              
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://packages.medibuntu.org hardy/free Translation-en_US                 
Hit http://archive.canonical.com hardy/partner Packages                        
Get:2 http://packages.linuxmint.com elyssa Release [7813B]                     
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US       
Hit http://archive.ubuntu.com hardy Release                                    
Ign http://wine.budgetdedicated.com hardy/main Packages                        
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US             
Hit http://archive.ubuntu.com hardy-updates Release                            
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://ppa.launchpad.net banshee Release                                   
Hit http://wine.budgetdedicated.com hardy/main Packages                        
Hit http://packages.medibuntu.org hardy Release                                
Hit http://archive.ubuntu.com hardy/main Packages                              
Hit http://archive.ubuntu.com hardy/restricted Packages                        
Hit http://archive.ubuntu.com hardy/universe Packages                          
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Ign http://ppa.launchpad.net banshee/main Packages                             
Ign http://packages.linuxmint.com elyssa/main Packages                         
Hit http://archive.ubuntu.com hardy/multiverse Packages                        
Hit http://archive.ubuntu.com hardy-updates/main Packages                      
Hit http://archive.ubuntu.com hardy-updates/restricted Packages                
Get:3 http://ppa.launchpad.net hardy/main Packages [2754B]                     
Ign http://packages.linuxmint.com elyssa/upstream Packages                     
Hit http://archive.ubuntu.com hardy-updates/universe Packages                  
Hit http://archive.ubuntu.com hardy-updates/multiverse Packages                
Hit http://packages.medibuntu.org hardy/free Packages                          
Get:4 http://ppa.launchpad.net hardy/main Sources [1604B]                      
Hit http://packages.medibuntu.org hardy/non-free Packages                      
Ign http://packages.linuxmint.com elyssa/import Packages             
Err http://ppa.launchpad.net banshee/main Packages
  404 Not Found
Hit http://packages.linuxmint.com elyssa/main Packages
Hit http://packages.linuxmint.com elyssa/upstream Packages
Hit http://packages.linuxmint.com elyssa/import Packages 
Fetched 39.8kB in 2s (19.1kB/s)                          
W: Failed to fetch http://ppa.launchpad.net/banshee-team/ubuntu/dists/banshee/main/binary-i386/Packages.gz  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

--edit--
Nevermind, synaptic still allowed me to download it.
Thanks! :)

---

