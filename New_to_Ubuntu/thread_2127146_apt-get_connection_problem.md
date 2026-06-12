---
title: "apt-get connection problem"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by amin021023 on 2013-03-19
Hi something's wrong with my apt-get and software center....

this is what I get when I try "sudo apt-get update"

```
amin@amin-Aspire-5349:~$ sudo apt-get updateIgn http://us.archive.ubuntu.com quantal InRelease
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://archive.canonical.com quantal InRelease                             
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Ign http://ppa.launchpad.net quantal Release.gpg                               
Ign http://ppa.launchpad.net quantal Release                                                                                                          
Ign http://archive.canonical.com quantal Release.gpg                                                                                                  
Err http://extras.ubuntu.com quantal Release.gpg                                                                                                      
  Could not connect to 37.220.10.118:443 (37.220.10.118). - connect (110: Connection timed out)
Ign http://extras.ubuntu.com quantal Release                                                                                                          
Ign http://extras.ubuntu.com quantal/main Sources/DiffIndex                                                                                
Ign http://extras.ubuntu.com quantal/main i386 Packages/DiffIndex                                                                          
Err http://extras.ubuntu.com quantal/main Translation-en_US                                                                                
  Unable to connect to 37.220.10.118:443:
Err http://extras.ubuntu.com quantal/main Translation-en                                                                                   
  Unable to connect to 37.220.10.118:443:
Err http://extras.ubuntu.com quantal/main Sources                                                                                          
  Unable to connect to 37.220.10.118:443:
Err http://extras.ubuntu.com quantal/main i386 Packages                                                                                    
  Unable to connect to 37.220.10.118:443:
Ign http://us.archive.ubuntu.com quantal-backports InRelease                                                                               
Ign http://security.ubuntu.com quantal-security InRelease                                                                                  
Ign http://ppa.launchpad.net quantal/main Sources/DiffIndex                                                                                           
Ign http://us.archive.ubuntu.com quantal Release.gpg                                                                                                  
Ign http://security.ubuntu.com quantal-security Release.gpg                                                                                           
Ign http://ppa.launchpad.net quantal/main i386 Packages/DiffIndex                                                                                     
Ign http://archive.canonical.com quantal Release                                                                                                      
Ign http://archive.canonical.com quantal/partner i386 Packages/DiffIndex                                                                              
Err http://archive.canonical.com quantal/partner Translation-en_US                                                   
  Unable to connect to 37.220.10.118:443:
Err http://archive.canonical.com quantal/partner Translation-en                                                      
  Unable to connect to 37.220.10.118:443:
Err http://archive.canonical.com quantal/partner i386 Packages                                                       
  Unable to connect to 37.220.10.118:443:
27% [Connecting to 37.220.10.118 (37.220.10.118)] [Waiting for headers] [Waiting for headers]               
```

it's like it has connection issues...
and also the software center is unable to download/install anything...

thanks in advance...

---

### Post by slickymaster on 2013-03-19
Try these at a terminal window, one at a time:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update && sudo apt-get upgrade
```
The first command clears the current list of software and the other two downloads and refreshes the list.

---

### Post by amin021023 on 2013-03-19
> **slickymaster said:**
> Try these at a terminal window, one at a time:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update && sudo apt-get upgrade
```
The first command clears the current list of software and the other two downloads and refreshes the list.


thanks but got new error now:

```
amin@amin-Aspire-5349:~$ sudo apt-get update && sudo apt-get upgradeIgn http://security.ubuntu.com quantal-security InRelease
Ign http://extras.ubuntu.com quantal InRelease                                 
Ign http://ppa.launchpad.net quantal InRelease                                 
Ign http://us.archive.ubuntu.com quantal InRelease                             
Ign http://archive.canonical.com quantal InRelease                             
Ign http://extras.ubuntu.com quantal Release.gpg                               
Ign http://ppa.launchpad.net quantal Release.gpg                               
Ign http://security.ubuntu.com quantal-security Release.gpg                    
Ign http://us.archive.ubuntu.com quantal-updates InRelease                     
Ign http://archive.canonical.com quantal Release.gpg                           
Ign http://extras.ubuntu.com quantal Release                                   
Ign http://ppa.launchpad.net quantal Release                                   
Ign http://security.ubuntu.com quantal-security Release                        
Ign http://us.archive.ubuntu.com quantal-backports InRelease                   
Ign http://archive.canonical.com quantal Release                               
Ign http://us.archive.ubuntu.com quantal Release.gpg                           
Ign http://us.archive.ubuntu.com quantal-updates Release.gpg                   
Ign http://us.archive.ubuntu.com quantal-backports Release.gpg                 
Ign http://us.archive.ubuntu.com quantal Release                               
Ign http://us.archive.ubuntu.com quantal-updates Release                       
Ign http://us.archive.ubuntu.com quantal-backports Release                     
Err http://archive.canonical.com quantal/partner i386 Packages                 
  407  Unauthorized
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Ign http://archive.canonical.com quantal/partner Translation-en                
Err http://extras.ubuntu.com quantal/main Sources                              
  407  Unauthorized
Err http://ppa.launchpad.net quantal/main Sources                              
  407  Unauthorized
Err http://extras.ubuntu.com quantal/main i386 Packages                        
  407  Unauthorized
Err http://ppa.launchpad.net quantal/main i386 Packages                        
  407  Unauthorized
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Err http://security.ubuntu.com quantal-security/main Sources                   
  407  Unauthorized
Err http://security.ubuntu.com quantal-security/restricted Sources             
  407  Unauthorized
Err http://security.ubuntu.com quantal-security/universe Sources               
  407  Unauthorized
Err http://security.ubuntu.com quantal-security/multiverse Sources
  407  Unauthorized
Err http://security.ubuntu.com quantal-security/main i386 Packages             
  407  Unauthorized
Err http://security.ubuntu.com quantal-security/restricted i386 Packages       
  407  Unauthorized
Err http://security.ubuntu.com quantal-security/universe i386 Packages
  407  Unauthorized
Err http://security.ubuntu.com quantal-security/multiverse i386 Packages
  407  Unauthorized
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Ign http://security.ubuntu.com quantal-security/main Translation-en
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en
Err http://us.archive.ubuntu.com quantal/main Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal/restricted Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal/universe Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal/multiverse Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal/main i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal/restricted i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal/universe i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal/multiverse i386 Packages
  407  Unauthorized
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal/main Translation-en
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal/universe Translation-en
Err http://us.archive.ubuntu.com quantal-updates/main Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-updates/restricted Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-updates/universe Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-updates/multiverse Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-updates/main i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-updates/universe i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages
  407  Unauthorized
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en
Err http://us.archive.ubuntu.com quantal-backports/main Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-backports/restricted Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-backports/universe Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-backports/multiverse Sources
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-backports/main i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-backports/universe i386 Packages
  407  Unauthorized
Err http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages
  407  Unauthorized
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  407  Unauthorized


W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://ppa.launchpad.net/alza/project/ubuntu/dists/quantal/main/source/Sources  407  Unauthorized


W: Failed to fetch http://ppa.launchpad.net/alza/project/ubuntu/dists/quantal/main/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://archive.canonical.com/ubuntu/dists/quantal/partner/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/main/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-i386/Packages  407  Unauthorized


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-i386/Packages  407  Unauthorized



```

---

### Post by MoebusNet on 2013-03-19
I'm no expert, but it looks as though you may have a proxy issue:

[http://ubuntuforums.org/showthread.php?t=1573551](http://ubuntuforums.org/showthread.php?t=1573551)

[http://ubuntuforums.org/showthread.php?t=1575](http://ubuntuforums.org/showthread.php?t=1575)

---

### Post by rich4421972 on 2013-03-19
Keep trying. Sometimes the ubuntu servers are running at capacity and cannot connect everyone. Keep cycling through with your apt-get command. If worse comes to worst, ping each archive location to see if you are really connecting at all. Hope this helps. :)

---

### Post by amin021023 on 2013-03-21
ok thanks guys the proxy problem is now fixed...I just removed username and password requirement from my proxy server..easy peasy..

---

### Post by MoebusNet on 2013-03-21
This might help you reenable your username & password:

[http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html](http://www.ubuntugeek.com/how-to-configure-ubuntu-desktop-to-use-your-proxy-server.html)

---

