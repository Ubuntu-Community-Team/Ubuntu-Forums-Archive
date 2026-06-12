---
title: "unable to update failed to fetch 404"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by micahpage on 2014-08-09
Im trying to update via
```
sudo apt-get update && sudo apt-get upgrade
```
the output i get from that is:
```
metulburr@ubuntu ~  $ sudo apt-get update && sudo apt-get upgradeIgn http://us.archive.ubuntu.com trusty InRelease
Ign http://dl.google.com stable InRelease                                                                
Hit http://us.archive.ubuntu.com trusty Release.gpg                                                      
Hit http://us.archive.ubuntu.com trusty Release                                                          
Ign http://dl.google.com stable InRelease                                                                
Ign http://archive.ubuntu.com raring InRelease                                                           
Hit http://us.archive.ubuntu.com trusty/main Sources                                       
Hit http://dl.google.com stable Release.gpg                                                
Ign http://extras.ubuntu.com trusty InRelease                                              
Hit http://us.archive.ubuntu.com trusty/restricted Sources                                 
Ign http://ppa.launchpad.net trusty InRelease                                              
Hit http://dl.google.com stable Release.gpg                                                
Hit http://us.archive.ubuntu.com trusty/universe Sources                                   
Ign http://archive.ubuntu.com raring Release.gpg                                           
Hit http://dl.google.com stable Release                                                    
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                                               
Hit http://extras.ubuntu.com trusty Release.gpg                                                          
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                                              
Ign http://ppa.launchpad.net trusty InRelease                                              
Hit http://dl.google.com stable Release                                                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages                                        
Ign http://archive.ubuntu.com raring Release                                                             
Hit http://dl.google.com stable/main amd64 Packages                                        
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                            
Hit http://extras.ubuntu.com trusty Release                                                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages                                        
Hit http://dl.google.com stable/main i386 Packages                                         
Ign http://ppa.launchpad.net trusty InRelease                                              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                                 
Ign http://archive.ubuntu.com raring/main amd64 Packages/DiffIndex                         
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages                           
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                             
Hit http://extras.ubuntu.com trusty/main Sources                                           
Hit http://ppa.launchpad.net trusty Release.gpg                                            
Ign http://archive.ubuntu.com raring/restricted amd64 Packages/DiffIndex                   
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages                           
Hit http://dl.google.com stable/main amd64 Packages                                        
Hit http://dl.google.com stable/main i386 Packages                                         
Ign http://archive.ubuntu.com raring/universe amd64 Packages/DiffIndex                     
Hit http://us.archive.ubuntu.com trusty/main Translation-en                                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                                                  
Ign http://ppa.launchpad.net trusty Release.gpg                                                          
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en                          
Ign http://archive.ubuntu.com raring/multiverse amd64 Packages/DiffIndex                   
Hit http://extras.ubuntu.com trusty/main i386 Packages                                     
Hit http://ppa.launchpad.net trusty Release.gpg                                            
Ign http://archive.ubuntu.com raring/main i386 Packages/DiffIndex                          
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en                          
Hit http://ppa.launchpad.net trusty Release                                                
Ign http://archive.ubuntu.com raring/restricted i386 Packages/DiffIndex                                  
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                                          
Ign http://ppa.launchpad.net trusty Release                                                
Ign http://archive.ubuntu.com raring/universe i386 Packages/DiffIndex                      
Ign http://archive.ubuntu.com raring/multiverse i386 Packages/DiffIndex                    
Hit http://ppa.launchpad.net trusty Release                                                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                  
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                   
Ign http://dl.google.com stable/main Translation-en_US                                     
Ign http://dl.google.com stable/main Translation-en                                        
Ign http://dl.google.com stable/main Translation-en_US                                     
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                             
Ign http://dl.google.com stable/main Translation-en                                        
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US                       
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US                       
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US   
Ign http://extras.ubuntu.com trusty/main Translation-en_US           
Ign http://extras.ubuntu.com trusty/main Translation-en              
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://archive.ubuntu.com raring/main Translation-en_US
Ign http://archive.ubuntu.com raring/main Translation-en
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring/multiverse Translation-en
Ign http://archive.ubuntu.com raring/restricted Translation-en_US
Ign http://archive.ubuntu.com raring/restricted Translation-en
Ign http://archive.ubuntu.com raring/universe Translation-en_US
Ign http://archive.ubuntu.com raring/universe Translation-en
Err http://archive.ubuntu.com raring/main amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com raring/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com raring/universe amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com raring/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com raring/restricted i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com raring/universe i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
Err http://archive.ubuntu.com raring/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.153 80]
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.153 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
metulburr@ubuntu ~  $ 



```

the system is ubuntu 14.04 

Ive tried researching various site about fixes broken repos including:
[http://alicious.com/remove-broken-apt-repos/](http://alicious.com/remove-broken-apt-repos/)
but the commands they give cause other errors

ppas
```
metulburr@ubuntu ~ $ ls /etc/apt/sources.list.dbartbes-love-unstable-trusty.list       kernel-ppa-ppa-trusty.list
bartbes-love-unstable-trusty.list.save  sonkun-sfml-development-trusty.list
google-chrome.list                      sonkun-sfml-development-trusty.list.save
google-chrome.list.save                 sonkun-sfml-stable-trusty.list
google-talkplugin.list                  sonkun-sfml-stable-trusty.list.save
google-talkplugin.list.save             zanchey-asciinema-trusty.list
ia32-libs-raring.list                   zanchey-asciinema-trusty.list.save
ia32-libs-raring.list.save
metulburr@ubuntu ~ $ 
```

Most of the stuff on researching is ppas as to 3rd party libs or ranodm stuff. However this one is man amd64 packages. I dont know if i "should" remove it or not. Although i am not sure how if i wanted to.

```
metulburr@ubuntu ~ $ uname -a
Linux ubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by grahammechanical on 2014-08-09
Personal Package Archives (PPA) are useful for installing software if we are willing to take responsibility for what is downloaded. Once the application has been downloaded and installed we should disable the PPA to avoid problems like this. We go to System Settings>Software and Updates>Other Software tab.

There is another matter that is causing this problem. You seem to be using 14.04 (code name trusty tahr) but you also have repositories from 13.04 (code name raring ringtail). Each version of Ubuntu has it own set of repositories/archives. And those raring archives although official Ubuntu archives are now closed because Ubuntu 13.04 has reached end of life. And that is why the updater cannot access those URLs and gives errors.

Regards.

---

### Post by Jonathan Precise on 2014-08-09
@grahammechanical: If one removes the PPAs however, one would have to manually check from time to time the ppa's site to see if there are any updates. If one keeps the ppa the software can auto-update or at least semi-auto-update. However when upgrading to another release of ubuntu (say from 13.10 -> 14.04 LTS) one should disable them.

@micahpage: Please post the output of:

```
cat /etc/apt/sources.list
```

The output should help us identify which lines to edit/remove.

---

### Post by micahpage on 2014-08-29
Thanks for the responses, i have been busy the past couple of weeks, so i have been unable to respond.

This is a fresh install of 14.04. I never upgraded from 13.10. 

```
metulburr@ubuntu ~  $ cat /etc/apt/sources.list# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.




## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main
metulburr@ubuntu ~ $ 



```

---

### Post by buzzingrobot on 2014-08-29
404's indicate that the server did not respond:  It doesn't exist, it's down, etc.  Your first post showed 404's on Raring repos, which is not surprising since those repos went offline when Raring supported ended.

If you see persistent 404's on 14.04, most likely something more fundamental is affecting youor net connections. (Occasional server temporary downtime isn't unusual.) The primary server you use can be changed in the Software & Updates tool.

---

### Post by nachoxs on 2014-10-13
I had the same exact problem on 14.04. As someone else already said, if you go to the program "software and updates", and then click on "other software", you will see a checked item called "Ubuntu 13.04 Raring Ringtail". So simply uncheck it and that should fix the problem. It worked for me. You will realize this item is there even if you have a fresh install of 14.04.

---

