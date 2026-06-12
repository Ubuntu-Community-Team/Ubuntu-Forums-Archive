---
title: "&quot;Requires installation of untrusted packages&quot;"
date: 2016-04-03
forum: New to Ubuntu
---

### Post by Jorhel on 2016-04-03
Hi,
I have the same problem [as in thread [http://ubuntuforums.org/showthread.php?t=2306802]](http://ubuntuforums.org/showthread.php?t=2306802]) when trying to install a photo management from the Ubuntu software centre.
I had installed F-spot didn't like it much but was OK then I could not open it anymore. Click on it the window will appear for a few seconds then shut.
So I browsed through the ubunto software centre and found a couple that sounded like what I wanted. But every time I tried to install I got the message require the installation of untrusted packages. With the option to click OK or repair.
Ok got me nowhere, repair seem to have started the install process but at the end nothing happened.
So 2 questions: 
1st :I thought that anything listed in the sofware centre was trustable? I have installed a few packges through it before without any issues. Is that not the case.
2nd : How do I found a software that the computer will let me install?
I'm on Xubuntu 14.04LTS.
I ran the code above and didn't came up with any GPG errors.
Thanks

---

### Post by oldos2er on 2016-04-03
Please post the complete output from ```
sudo apt-get update
```

---

### Post by Jorhel on 2016-04-03
```
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty InRelease
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports InRelease [65.9 kB]        
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty Release.gpg                            
Get:3 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/main Sources [271 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:6 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/restricted Sources [5,352 B] 
Get:7 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/universe Sources [151 kB]    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [110 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:9 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/multiverse Sources [5,946 B]
Get:10 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/main i386 Packages [714 kB] 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,035 B] 
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [34.7 kB]   
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,750 B] 
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [423 kB]  
Get:15 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:16 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/universe i386 Packages [358 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_NZ                     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:18 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Get:19 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/main Translation-en [373 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [126 kB]
Get:21 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/multiverse Translation-en [7,227 B]
Get:22 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,699 B]
Get:23 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-updates/universe Translation-en [186 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5,175 B]
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty Release                                
Get:25 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/main Sources [8,696 B]    
Get:26 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Get:27 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/universe Sources [34.4 kB]
Get:28 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:29 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/main i386 Packages [9,797 B]
Get:30 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:31 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/universe i386 Packages [41.4 kB]
Get:32 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty-backports/universe Translation-en
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/main Sources                           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/multiverse Sources                     
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [245 kB] 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/main Translation-en_NZ                 
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/multiverse Translation-en_NZ           
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/restricted Translation-en_NZ           
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/universe Translation-en_NZ             
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2,570 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,206 B]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [74.3 kB]
Fetched 3,444 kB in 19s (173 kB/s)                                             
Reading package lists... Done
```

---

### Post by grahammechanical on 2016-04-03
You have some PPAs enabled. Go to System Settings>Software & Updates>Other Software & disable any PPAs. And see if the removes that message.

PPA = Personal Package Archive. It is personal to the particular programmer to set up the archive. Installing software through a PPA is not the same as installing software through the software centre. If we install software through a PPA, the we are trusting the programmer But as far as Ubuntu developers are concerned the software is untrusted packages.

And please wrap large blocks of text such as terminal printout in code tags. Select the text and click the last icon on the right of the set of icons above the anel where we type our text.

Regards.

---

### Post by Jorhel on 2016-04-04
Thanks,
Sorry about the quote it's a learning curve but I'm impressed by the speed with which my few threads have been answered
I rebooted my computer and was able to install digiKam without the untrusted message. It works with a tendency to crash unexpectely but that might not be linked.
The PPA program was installed through the terminal to enable flash in firefox. if I disable it it will stop working and I need it...:confused:

---

