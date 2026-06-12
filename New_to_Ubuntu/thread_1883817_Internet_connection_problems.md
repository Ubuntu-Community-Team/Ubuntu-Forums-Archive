---
title: "Internet connection problems"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by Wilfred Padambo on 2011-11-20
Am having great problems to run any application in Terminal due to my internet settings. I believe.  Am getting the following error all the time since installation of ubuntu 11.10. But am able to surf on the internet.

wilfred@wilfred-HP-dX2000-MT:~$ sudo apt-get install synaptic
[sudo] password for wilfred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
wilfred@wilfred-HP-dX2000-MT:~$ 

Am using Wired connection and also Proxy server. Where should I change the settings so that I can successfully run applications in the Terminal and also Ubuntu Software Center. Am using Ubuntu 11.10.
Wilfred

---

### Post by Rodney9 on 2011-11-20
I would run this in the terminal - 

sudo apt-get update && sudo apt-get upgrade

then try and install Synaptic again.

Rodney

---

### Post by Wilfred Padambo on 2011-11-21
Thanks 4 the reply and suggestion but look at the following result and tell me where you think am going wrong. I will definitely appreciate your help because am very new to ubuntu. Thanks in advance.

wilfred@wilfred-HP-dX2000-MT:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for wilfred: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
  407  Proxy Authentication Required
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  407  Proxy Authentication Required
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
  407  Proxy Authentication Required
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  407  Proxy Authentication Required
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex          
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages/DiffIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages
  407  Proxy Authentication Required
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
  407  Proxy Authentication Required
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/oneiric/main/source/Sources)  407  Proxy Authentication Required

W: Failed to fetch [http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/oneiric/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/multiverse/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  407  Proxy Authentication Required

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  407  Proxy Authentication Required

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by I_can_see_the_light on 2011-11-21
Have a look here:

[https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)

If you scroll down a bit there's some info relating to logging in/authentication which seems to be your problem.

I don't use a proxy myself though so I can't tell if it's going to work.

---

### Post by Wilfred Padambo on 2011-11-26
Am still having problems with the proxy settings. I have tried editing the apt.conf with all sorts of lines but to no avail. How do others do it? Is it that am using a wrong ubuntu because am using 11.10. I really need to install synaptic because that' what worked in Ubuntu 11.4.
 
Thanks
 
Wilfred

---

