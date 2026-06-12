---
title: "Unable to download updates."
date: 2013-05-20
forum: New to Ubuntu
---

### Post by piyushroutray on 2013-05-20
I am unable to download updates even though I am connected to the internet with 7.96Mbps download speed. There are no firewalls or anything as such which I know of to prevent any downloads.
My configuration is  

```

3.2.0-43-generic-pae #68-Ubuntu SMP Wed May 15 03:55:10 UTC 2013 i686 i686 i386 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
NAME="Ubuntu"
VERSION="12.04.2 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.2 LTS)"
VERSION_ID="12.04"
```

And I am getting the following error. Thanks in advance.
[ATTACH=CONFIG]242824[/ATTACH]

Also, I have tried using sudo apt-get update from the terminal but that simply ignores most of the files which it cannot seem to connect to.

---

### Post by matt_symes on 2013-05-20
Hi

Open a terminal and type

```
sudo apt-get update
```

Post the output back here between code tags. It will give more diagnostic information than that screenshot.

You can copy the output form the terminal (highlight text->right click ->copy) and paste into your next post.

To use code tags in your next post, highlight the text in your post to put between code tags and hit the # button in the toolbar above where you type text.

I'll edit your post #1 and put code tags in it for you.

Kind regards

---

### Post by piyushroutray on 2013-05-20
```
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise Release                                                  
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main TranslationIndex                                    
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted TranslationIndex                              
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main i386 Packages                                       
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted i386 Packages                                 
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en_US                                   
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en                                      
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en_US                             
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                                                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                                                                        
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                                                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                                                                                        
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                                                                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                                                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                                                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                                                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                                                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                                                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                                                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                                                                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                          
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [383 kB]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex             
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [87.1 kB]                                               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]                                           
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [625 kB]                                             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]                                     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [203 kB]                                           
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                      
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                                
  404  Not Found
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Fetched 1,385 kB in 1s (716 kB/s)
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch [http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by supremedalek on 2013-05-20
Sounds like it can't find [http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources). Anything you need from that? Otherwise you could comment that out and try again.

---

### Post by matt_symes on 2013-05-20
Hi

Please use code tags :) It makes it much easier to read and you are more likely to get help if you help others that way.

> W: Failed to fetch [http://ppa.launchpad.net/boost-lates...source/Sources](http://ppa.launchpad.net/boost-lates...source/Sources)  404  Not Found

[http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources)

This PPA does not have a repository for Precise. These are the repositories for it....

[http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/)

You can remove it from the software centre  -> software sources. Look for the boost-latest PPA.
> 
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted i386 Packages

To remove this error, disable updates from the CDRom on software sources in the same window.
> 
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                      
  404  Not Found

..and the same for this one. Remove the reference to it using software sources.

Then type

```
sudo apt-get update
```

If you are not sure how to remove software sources, I'll post some commands you can copy and paste into the terminal to do it for you.

Kind regards

---

### Post by piyushroutray on 2013-05-20
Hello Matt!
Thanks a ton for the help. I disabled the cd-rom option. I found the software sources but I just wanted to make sure I am doing the correct thing before going ahead and doing it. Attached is a screenshot of the software sources on my system. Can you point out which ones to remove? (I believe, you meant the last two.)
Thanks and regards.

> **matt_symes said:**
> Hi

Please use code tags :) It makes it much easier to read and you are more likely to get help if you help others that way.



[http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/precise/main/source/Sources)

This PPA does not have a repository for Precise. These are the repositories for it....

[http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/](http://ppa.launchpad.net/boost-latest/ppa/ubuntu/dists/)

You can remove it from the software centre  -> software sources. Look for the boost-latest PPA.


To remove this error, disable updates from the CDRom on software sources in the same window.


..and the same for this one. Remove the reference to it using software sources.

Then type

```
sudo apt-get update
```

If you are not sure how to remove software sources, I'll post some commands you can copy and paste into the terminal to do it for you.

Kind regards

---

### Post by matt_symes on 2013-05-20
Hi

Yep. Disable the last two.

Then open a terminal and type

```
sudo apt-get update
```

If it throws any more errors then post them back here.

If not, type

```
sudo apt-get upgrade
```

If that throws no errors then you should be good to go.

Post back any errors.

Kind regards

---

### Post by piyushroutray on 2013-05-20
I removed the last two. However, shouldn't I add something in their place?
How do I add the boost-latest ppa, which you said. It doesn't let me add there. Is there any terminal code to add them?
Thanks!

---

### Post by matt_symes on 2013-05-21
Hi

> **piyushroutray said:**
> I removed the last two. However, shouldn't I add something in their place?
How do I add the boost-latest ppa, which you said. It doesn't let me add there. Is there any terminal code to add them?
Thanks!

You cant' add the boost-latest launchpad ppa for Precise as it does not exist.

Maybe you could build it from source or find another PPA hosting it for Precise.

A better idea is to find out why there is no PPA for Precise in launchpad though.

Kind regards

---

