---
title: "Ubuntu update manager not showing any new updates"
date: 2011-12-28
forum: New to Ubuntu
---

### Post by computerandu on 2011-12-28
Hi All,

I was without internet for few weeks and when I got internet yesterday I tried to update Ubuntu 11.10. To my surprise update manager showed no new updates at all. It olnly reads as:

The package information was updated 17 days ago. Press the check button below to check for new software updates.

I clicked on it and found no updates at all.

When I went into terminal and tried with sudo apt-get update..here is what i got:

```
Ign http://ftp.u-picardie.fr oneiric InRelease
Ign http://ftp.u-picardie.fr oneiric-updates InRelease                                                                                                
Ign http://ftp.u-picardie.fr oneiric-backports InRelease                                                                                              
Ign http://ftp.u-picardie.fr oneiric-security InRelease                                                                                               
Ign http://extras.ubuntu.com oneiric InRelease                                                                                                        
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                                                                                             
Hit http://extras.ubuntu.com oneiric Release                                                                                                          
Err http://extras.ubuntu.com oneiric Release                                                                                                          
  
Hit http://ftp.u-picardie.fr oneiric Release.gpg                                                                                                      
Ign http://linux.dropbox.com oneiric InRelease                                                                                                        
Hit http://ftp.u-picardie.fr oneiric-updates Release.gpg                                                                                              
Hit http://ftp.u-picardie.fr oneiric-backports Release.gpg                                                                                            
Hit http://ftp.u-picardie.fr oneiric-security Release.gpg                                                                                             
Hit http://linux.dropbox.com oneiric Release.gpg                                                                                                      
Hit http://ftp.u-picardie.fr oneiric Release                                                                                                          
Hit http://ftp.u-picardie.fr oneiric-updates Release                                                                                                  
Hit http://ftp.u-picardie.fr oneiric-backports Release                                                                                                
Hit http://ftp.u-picardie.fr oneiric-security Release                                                                                                 
Hit http://ftp.u-picardie.fr oneiric/main i386 Packages                                                                                               
Hit http://ftp.u-picardie.fr oneiric/restricted i386 Packages                                                                                         
Hit http://ftp.u-picardie.fr oneiric/universe i386 Packages                                                                                           
Hit http://ftp.u-picardie.fr oneiric/multiverse i386 Packages                                                                                         
Hit http://ftp.u-picardie.fr oneiric/main TranslationIndex                                                                                            
Hit http://ftp.u-picardie.fr oneiric/multiverse TranslationIndex                                                                                      
Hit http://ftp.u-picardie.fr oneiric/restricted TranslationIndex                                                                                      
Hit http://ftp.u-picardie.fr oneiric/universe TranslationIndex                                                                                        
Hit http://ftp.u-picardie.fr oneiric-updates/main i386 Packages                                                                                       
Hit http://linux.dropbox.com oneiric Release                                                                                                          
Hit http://ftp.u-picardie.fr oneiric-updates/restricted i386 Packages                                                                                 
Hit http://ftp.u-picardie.fr oneiric-updates/universe i386 Packages                                                                                   
Hit http://ftp.u-picardie.fr oneiric-updates/multiverse i386 Packages                                                                                 
Hit http://ftp.u-picardie.fr oneiric-updates/main TranslationIndex                                                                                    
Hit http://ftp.u-picardie.fr oneiric-updates/multiverse TranslationIndex                                                                              
Hit http://ftp.u-picardie.fr oneiric-updates/restricted TranslationIndex                                                                              
Hit http://ftp.u-picardie.fr oneiric-updates/universe TranslationIndex                                                                                
Hit http://ftp.u-picardie.fr oneiric-backports/main i386 Packages                                                                                     
Hit http://ftp.u-picardie.fr oneiric-backports/restricted i386 Packages                                                                               
Hit http://ftp.u-picardie.fr oneiric-backports/universe i386 Packages                                                                                 
Hit http://ftp.u-picardie.fr oneiric-backports/multiverse i386 Packages                                                                               
Hit http://ftp.u-picardie.fr oneiric-backports/main TranslationIndex                                                                                  
Hit http://ftp.u-picardie.fr oneiric-backports/multiverse TranslationIndex                                                                            
Hit http://ftp.u-picardie.fr oneiric-backports/restricted TranslationIndex                                                                            
Hit http://ftp.u-picardie.fr oneiric-backports/universe TranslationIndex                                                                              
Hit http://ftp.u-picardie.fr oneiric-security/main i386 Packages                                                                                      
Hit http://ftp.u-picardie.fr oneiric-security/restricted i386 Packages                                                                                
Hit http://ftp.u-picardie.fr oneiric-security/universe i386 Packages                                                                                  
Hit http://ftp.u-picardie.fr oneiric-security/multiverse i386 Packages                                                                                
Hit http://ftp.u-picardie.fr oneiric-security/main TranslationIndex                                                                                   
Hit http://linux.dropbox.com oneiric/main i386 Packages                                                                                               
Ign http://linux.dropbox.com oneiric/main TranslationIndex                                                                                            
Hit http://ftp.u-picardie.fr oneiric-security/multiverse TranslationIndex                                                                             
Hit http://ftp.u-picardie.fr oneiric-security/restricted TranslationIndex                                                                             
Hit http://ftp.u-picardie.fr oneiric-security/universe TranslationIndex                                                                               
Hit http://ftp.u-picardie.fr oneiric/main Translation-en                                                                                              
Hit http://ftp.u-picardie.fr oneiric/multiverse Translation-en                                                                                        
Hit http://ftp.u-picardie.fr oneiric/restricted Translation-en                                                                                        
Hit http://ftp.u-picardie.fr oneiric/universe Translation-en                                                                                          
Hit http://ftp.u-picardie.fr oneiric-updates/main Translation-en                                                                                      
Hit http://ftp.u-picardie.fr oneiric-updates/multiverse Translation-en                                                                                
Hit http://ftp.u-picardie.fr oneiric-updates/restricted Translation-en                                                                                
Hit http://ftp.u-picardie.fr oneiric-updates/universe Translation-en                                                                                  
Hit http://ftp.u-picardie.fr oneiric-backports/main Translation-en                                                                                    
Hit http://ftp.u-picardie.fr oneiric-backports/multiverse Translation-en                                                                              
Hit http://ftp.u-picardie.fr oneiric-backports/restricted Translation-en                                                                              
Hit http://ftp.u-picardie.fr oneiric-backports/universe Translation-en                                                                                
Hit http://ftp.u-picardie.fr oneiric-security/main Translation-en                                                                                     
Hit http://ftp.u-picardie.fr oneiric-security/multiverse Translation-en                                                                               
Hit http://ftp.u-picardie.fr oneiric-security/restricted Translation-en                                                                               
Hit http://ftp.u-picardie.fr oneiric-security/universe Translation-en                                                                                 
Ign http://archive.canonical.com oneiric InRelease                                                                                                    
Get:2 http://archive.canonical.com oneiric Release.gpg [198 B]                                                                         
Hit http://archive.canonical.com oneiric Release                                            
Err http://archive.canonical.com oneiric Release                              
  
Ign http://dl.google.com stable InRelease                                     
Ign http://linux.dropbox.com oneiric/main Translation-en_US                   
Get:3 http://dl.google.com stable Release.gpg [198 B]      
Get:4 http://dl.google.com stable Release [1,347 B]                   
Ign http://linux.dropbox.com oneiric/main Translation-en        
Get:5 http://dl.google.com stable/main i386 Packages [1,214 B]
Ign http://dl.google.com stable/main TranslationIndex                             
Ign http://dl.google.com stable/main Translation-en_US     
Ign http://dl.google.com stable/main Translation-en        
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease
Get:6 http://ppa.launchpad.net oneiric Release.gpg [316 B]
Hit http://ppa.launchpad.net oneiric Release.gpg
Get:7 http://ppa.launchpad.net oneiric Release.gpg [316 B]
Get:8 http://ppa.launchpad.net oneiric Release.gpg [316 B]
Get:9 http://ppa.launchpad.net oneiric Release.gpg [316 B]
Hit http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net oneiric Release
Hit http://ppa.launchpad.net oneiric Release
Hit http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net oneiric Release    
Hit http://ppa.launchpad.net oneiric Release
Hit http://ppa.launchpad.net oneiric Release
Ign http://ppa.launchpad.net oneiric Release
Err http://ppa.launchpad.net oneiric Release
  
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Hit http://ppa.launchpad.net oneiric/main Sources
Hit http://ppa.launchpad.net oneiric/main i386 Packages
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net oneiric/main TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Sources/DiffIndex
Ign http://ppa.launchpad.net oneiric/main i386 Packages/DiffIndex                                                                                     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                            
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                     
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                               
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                     
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                               
Hit http://ppa.launchpad.net oneiric/main Sources                                                                                                     
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                                                               
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                                                                                           
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                                              
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                                                                                           
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                                              
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                                                                                           
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                                              
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                                                                                           
Ign http://ppa.launchpad.net oneiric/main Translation-en                                                                                              
Fetched 4,293 B in 6s (631 B/s)                                                                                                                       
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG E0319082F37F3AB0 Launchpad fixes for aprsd
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG 73AD8184264CE9C6 Launchpad PPA for Simon Schneegans
W: GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG DFB844B8BB91632D Launchpad PPA for Weather Indicator Team
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net oneiric Release: The following signatures were invalid: BADSIG C2518248EEA14886 Launchpad VLC

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release  

W: Failed to fetch http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

Just for clarification sake, I have selected the best server for the updates in update manager settings.

These GPG error can be solved by updating the GPG keys ...but that, according to me, should not be the reason why it is not showing any new updates.


Any ideas people?

---

### Post by M!K3_$ on 2011-12-28
> **computerandu said:**
> 
These GPG error can be solved by updating the GPG keys ...but that, according to me, should not be the reason why it is not showing any new updates.


Worth a shot...
```
sudo apt-key update
```

---

### Post by computerandu on 2011-12-28
> **M!K3_$ said:**
> Worth a shot...
```
sudo apt-key update
```

Changes nothing

[HTML]gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2[/HTML]

---

### Post by lolpenguin on 2011-12-28
```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```
Try this.

---

### Post by computerandu on 2011-12-29
> **lolpenguin said:**
> ```
sudo apt-get upgrade && sudo apt-get dist-upgrade
```Try this.

Nothing is upgraded.

---

### Post by mcduck on 2011-12-29
One thing to keep in mind is that the "The package information was updated 17 days ago" message doesn't mean that it wouldn't have updated *any* package information for 17 days.

The counter will only reset once you successfully check for updates in every configured repository, meaning that any non-functioning repository, GPG error etc. will result in this message. (even if you had just updated all the software from the official repositories)


Also, if you are having any problems with the Ubuntu repositories, try switching to another mirror (even if the repository you are currently using was recommended to you as best server).

---

### Post by computerandu on 2011-12-29
> **mcduck said:**
> One thing to keep in mind is that the "The package information was updated 17 days ago" message doesn't mean that it wouldn't have updated *any* package information for 17 days.

The counter will only reset once you successfully check for updates in every configured repository, meaning that any non-functioning repository, GPG error etc. will result in this message. (even if you had just updated all the software from the official repositories)


Also, if you are having any problems with the Ubuntu repositories, try switching to another mirror (even if the repository you are currently using was recommended to you as best server).

Hmm.. that might be a reason... but in any case we are familiar with bunch of updates provided by Ubuntu almost on a daily basis. And in my case, I do not see any updates available for me.

I'll check with your suggestions once I reach home.
img, #cubbies-overlay{ -moz-transition-property: margin, box-shadow, z-index; -moz-transition-duration: 0.1s; -webkit-transition-property: margin, box-shadow, z-index; -webkit-transition-duration: 0.1s; } .cubbies-selected{ z-index: 9999; box-shadow: 3px 3px 8px -1px blue !important; cursor: pointer !important; margin: -3px 3px 3px -3px; } .cubbies-selected:active{ box-shadow: 2px 2px 5px -1px darkblue !important; margin: -1px 1px 1px -1px; } #cubbies-overlay{ position: fixed; z-index: 9999; bottom: 30px; left: 30px; box-shadow: 0 2px 3px rgba(0,0,0,0.8); border: none; } #cubbies-overlay:hover{ box-shadow: 0 2px 3px rgb(0,0,0); }

---

