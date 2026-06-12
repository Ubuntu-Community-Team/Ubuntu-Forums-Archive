---
title: "Red Triangle with errors after update on main window bar"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by send2 on 2013-03-26
Hi all,

I am getting the following errors after the last pushed updates. I am running Ubuntu 12.04 LTS on a Toshiba Satellite A505-S6986. What to do to correct? thanks:
[ATTACH=CONFIG]240588[/ATTACH]

---

### Post by ibjsb4 on 2013-03-26
For a start "cooperjona ppa stormcloud" is no longer available and needs to be removed from you software sources.

[http://ppa.launchpad.net/cooperjona/](http://ppa.launchpad.net/cooperjona/)

Then if you would do an update in terminal and post it.

```
sudo apt-get update
```

---

### Post by send2 on 2013-03-26
> **ibjsb4 said:**
> For a start "cooperjona ppa stormcloud" is no longer available and needs to be removed from you software sources.

[http://ppa.launchpad.net/cooperjona/](http://ppa.launchpad.net/cooperjona/)

Then if you would do an update in terminal and post it.

```
sudo apt-get update
```


Thanks for your reply. I took out that package from the software sources, when I ran sudo apt-get update this is what I got: 

```
warrior@warrior-Satellite-A505:~$ sudo apt-get update
[sudo] password for warrior: 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://repo.steampowered.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:3 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://www.remastersys.com precise Release.gpg                             
Hit http://repo.steampowered.com precise Release                               
Hit http://repository.spotify.com stable Release.gpg                           
Hit http://us.archive.ubuntu.com precise Release                               
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://deb.playonlinux.com precise Release.gpg                             
Get:5 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://extras.ubuntu.com precise Release                                   
Hit http://www.remastersys.com precise Release                                 
Get:6 http://security.ubuntu.com precise-security/main Sources [64.7 kB]       
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise Release                               
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://repository.spotify.com stable Release                               
Hit http://deb.playonlinux.com precise Release                                 
Hit http://us.archive.ubuntu.com precise-backports Release                     
Get:7 http://linux.dropbox.com precise Release [2,603 B]                       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://www.remastersys.com precise/main Sources                            
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://repository.spotify.com stable/non-free Sources                      
Get:8 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:9 http://security.ubuntu.com precise-security/universe Sources [22.6 kB]   
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [233 kB]
Hit http://deb.playonlinux.com precise/main amd64 Packages                     
Hit http://www.remastersys.com precise/main amd64 Packages                     
Hit http://www.remastersys.com precise/main i386 Packages                      
Ign http://www.remastersys.com precise/main TranslationIndex                   
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:12 http://linux.dropbox.com precise/main amd64 Packages [1,148 B]          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:13 http://us.archive.ubuntu.com precise-updates/main Sources [371 kB]      
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://deb.playonlinux.com precise/main i386 Packages                      
Ign http://deb.playonlinux.com precise/main TranslationIndex                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:14 http://linux.dropbox.com precise/main i386 Packages [1,148 B]           
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Get:15 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Get:16 http://security.ubuntu.com precise-security/universe amd64 Packages [68.6 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Get:17 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [243 kB] 
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Get:19 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,494 B]
Get:20 http://us.archive.ubuntu.com precise-updates/universe Sources [82.7 kB] 
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:21 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,746 B]
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:22 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [591 kB]
Hit https://private-ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://www.remastersys.com precise/main Translation-en_US                  
Get:23 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:24 http://security.ubuntu.com precise-security/universe i386 Packages [70.5 kB]
Hit https://private-ppa.launchpad.net precise Release                          
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:25 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Ign http://www.remastersys.com precise/main Translation-en                     
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit https://private-ppa.launchpad.net precise Release                          
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Get:26 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:27 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [190 kB]
Ign http://deb.playonlinux.com precise/main Translation-en_US                  
Ign http://archive.canonical.com precise/partner Translation-en                
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://linux.dropbox.com precise/main Translation-en                       
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Get:28 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,418 B]
Get:29 http://us.archive.ubuntu.com precise-updates/main i386 Packages [602 kB]
Ign http://deb.playonlinux.com precise/main Translation-en                     
Ign http://repository.spotify.com stable/non-free Translation-en               
Get:30 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.1 kB]
Get:31 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [192 kB]
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://download.virtualbox.org precise Release.gpg                         
Hit http://download.virtualbox.org precise Release                             
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Fetched 2,902 kB in 22s (127 kB/s)
W: Failed to fetch http://download.virtualbox.org/virtualbox/debian/dists/precise/Release  Unable to find expected entry 'contrib/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
warrior@warrior-Satellite-A505:~$ 

```

thanks for the help...

---

### Post by ibjsb4 on 2013-03-26
In terminal:

```
gksudo gedit /etc/apt/sources.list
```

And either remove the source line or just comment (#) it out.  The source line for vBox will have "src" in it.

If unsure about this, just post your sources.list.

---

### Post by send2 on 2013-03-26
> **ibjsb4 said:**
> In terminal:

```
gksudo gedit /etc/apt/sources.list
```

And either remove the source line or just comment (#) it out.  The source line for vBox will have "scr" in it.

If unsure about this, just post your sources.list.

Here is my sources list file: 

```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://www.remastersys.com/ubuntu precise main
deb-src http://www.remastersys.com/ubuntu precise main
deb-src http://download.virtualbox.org/virtualbox/debian precise contrib
deb http://repository.spotify.com stable non-free
deb-src http://repository.spotify.com stable non-free
```

Do i comment out by adding # # to the line  ----------> deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib?

thanks again...

---

### Post by ibjsb4 on 2013-03-26
deb-src [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib
Remove this line.

I can give you instructions on how to install VirtualBox, but first lets get your sources list working.

In terminal:

```
sudo apt-get update
```

Any errors?

---

### Post by send2 on 2013-03-26
After changing the list and after running sudo apt-get update I get the following errors:

```
warrior@warrior-Satellite-A505:~$ gksudo gedit /etc/apt/sources.list
warrior@warrior-Satellite-A505:~$ sudo apt-get update
Hit http://dl.google.com stable Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://us.archive.ubuntu.com precise Release                               
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://repo.steampowered.com precise Release.gpg                           
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://deb.playonlinux.com precise Release.gpg                             
Hit http://repo.steampowered.com precise Release                               
Hit http://us.archive.ubuntu.com precise-backports Release                     
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://deb.playonlinux.com precise Release                                 
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [371 kB]       
Hit http://deb.playonlinux.com precise/main amd64 Packages                     
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://deb.playonlinux.com precise/main i386 Packages                      
Ign http://deb.playonlinux.com precise/main TranslationIndex                   
Hit http://dl.google.com stable Release.gpg                                    
Get:6 http://security.ubuntu.com precise-security/main Sources [64.7 kB]       
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable Release                                        
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,494 B]
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [82.7 kB]  
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://repo.steampowered.com precise/steam TranslationIndex                
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,746 B]
Get:10 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [591 kB]
Get:11 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:12 http://security.ubuntu.com precise-security/universe Sources [22.6 kB]  
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [1,380 B]
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [233 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:16 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [190 kB]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://dl.google.com stable/main Translation-en_US                         
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,418 B]
Get:18 http://us.archive.ubuntu.com precise-updates/main i386 Packages [602 kB]
Get:19 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:20 http://security.ubuntu.com precise-security/universe amd64 Packages [68.6 kB]
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Get:21 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:22 http://security.ubuntu.com precise-security/main i386 Packages [243 kB] 
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://deb.playonlinux.com precise/main Translation-en_US                  
Get:23 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:24 http://security.ubuntu.com precise-security/universe i386 Packages [70.5 kB]
Get:25 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://deb.playonlinux.com precise/main Translation-en                     
Get:26 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.1 kB]
Get:27 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [192 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:28 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
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
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://www.remastersys.com precise Release.gpg                             
Hit http://download.virtualbox.org precise Release.gpg                         
Hit http://download.virtualbox.org precise Release                             
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://www.remastersys.com precise Release                                 
Hit http://download.virtualbox.org precise/contrib amd64 Packages              
Hit http://www.remastersys.com precise/main Sources                            
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://download.virtualbox.org precise/contrib i386 Packages               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://www.remastersys.com precise/main amd64 Packages                     
Hit http://www.remastersys.com precise/main i386 Packages                      
Ign http://www.remastersys.com precise/main TranslationIndex                   
Ign http://download.virtualbox.org precise/contrib TranslationIndex            
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Ign http://download.virtualbox.org precise/contrib Translation-en_US           
Ign http://download.virtualbox.org precise/contrib Translation-en              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Ign http://www.remastersys.com precise/main Translation-en_US                  
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://www.remastersys.com precise/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://ppa.launchpad.net precise/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                     
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                  
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Err http://linux.dropbox.com precise Release.gpg                               
  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)
Err http://repository.spotify.com stable Release.gpg                           
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Get:29 http://linux.dropbox.com precise Release [2,603 B]                      
Ign http://linux.dropbox.com precise/main amd64 Packages/DiffIndex             
Ign http://linux.dropbox.com precise/main i386 Packages/DiffIndex              
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Get:30 http://linux.dropbox.com precise/main amd64 Packages [1,148 B]          
Get:31 http://linux.dropbox.com precise/main i386 Packages [1,148 B]           
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Ign http://linux.dropbox.com precise/main Translation-en_US                    
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign http://linux.dropbox.com precise/main Translation-en                       
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit http://repository.spotify.com stable Release                               
Ign http://repository.spotify.com stable/non-free Sources/DiffIndex            
Ign http://repository.spotify.com stable/non-free amd64 Packages/DiffIndex     
Ign http://repository.spotify.com stable/non-free i386 Packages/DiffIndex      
Ign http://repository.spotify.com stable/non-free TranslationIndex             
Hit http://repository.spotify.com stable/non-free Sources                      
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://repository.spotify.com stable/non-free i386 Packages                
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Ign http://repository.spotify.com stable/non-free Translation-en               
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Fetched 2,902 kB in 33s (86.3 kB/s)
W: Failed to fetch http://repository.spotify.com/dists/stable/Release.gpg  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://linux.dropbox.com/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
warrior@warrior-Satellite-A505:~$ 

```

Thanks ibjsb4 for your help again :)

Note: I will have to wait untill Saturday to continue with your help, I won't be able to have access to my computer untill that time. Thanks again for your help....

I am back online......

---

