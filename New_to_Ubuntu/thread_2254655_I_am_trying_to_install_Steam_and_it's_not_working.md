---
title: "I am trying to install Steam and it's not working"
date: 2014-11-28
forum: New to Ubuntu
---

### Post by philpope15 on 2014-11-28
I have read forums and can't figure this out! I have a fresh install of Ubuntu 12.10 and all I want to do is play steam. 

I have tried to download the installer via the software center as well as the terminal
I have added "deb [arch=i386] [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam" to the "sources" list in the details of the software updater



I cannot seem to figure this out! and 9/10 forums are copies and do not resolve me issue (just dont want to make you think I didnt do any research)

I am running Ubuntu 12.10 on a Compaq Presario C700.

When I try to run ' sudo apt-get update' I get an error message.
(sorry for the length, I'm not the best at formatting yet)

```
pope@Gizmo:~$ sudo apt-get update
[sudo] password for pope: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg                   
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal InRelease                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release.gpg            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal Release                
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main i386 Packages               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US     
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en        
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources
  404  Not Found [IP: 2001:67c:1562::16 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources
  404  Not Found [IP: 2001:67c:1562::16 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources
  404  Not Found [IP: 2001:67c:1562::16 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources
  404  Not Found [IP: 2001:67c:1562::16 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages
  404  Not Found [IP: 2001:67c:1562::16 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1562::16 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages
  404  Not Found [IP: 2001:67c:1562::16 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1562::16 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) quantal/main Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources  
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources    
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages
  404  Not Found [IP: 2001:67c:1562::17 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::16 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::17 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by philpope15 on 2014-11-28
In addition - when I try to run the 'software updater,' I get the error message:

i386/Packages  404  Not Found [IP: 2001:67c:1562::14 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 2001:67c:1562::13 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bucky Ball on 2014-11-28
Welcome. 12.10 is no longer supported. That is why you are getting the 'not found' errors. 

Suggest you install a supported release and try again. 12.04 LTS and 14.04 LTS both have five years support (2017 and 2019 respectively). 14.10 has nine months support. Good luck.

---

