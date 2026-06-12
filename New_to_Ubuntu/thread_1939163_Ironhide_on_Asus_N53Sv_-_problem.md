---
title: "Ironhide on Asus N53Sv - problem"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by DanPower on 2012-03-11
Hi all, first post... I've been using Ubuntu for a few weeks now, had a play with it back at 7.04 but only just started using it again.  I'm enjoying it, have it behaving quite how I like it, but I'm having some problems with ironhide.

I have a new N53Sv which I did a WUBI install of 11.10 on for a week or so, all good.  Ironhide installed ok although I had trouble with the indicator.  I decided I liked Ubuntu and would stick with it so I recently formatted and am now dual booting 11.10 and Win7.  I installed ironhide again, but I had the same problems with the indicator crashing.

I found [this bug and fix](https://github.com/MrMEEE/ironhide/issues/77) so I followed the steps here.  I was still having problems and thought I'd stuffed up, so I decided to try to remove ironhide and reinstall.  I did this through ppa-purge but it didn't seem to work properly.  I found [this guide to installing Ironhide](http://www.ivegotavirus.com/blog/2011/09/01/how-to-set-up-intel-optimus-graphics-on-ubuntu-save-battery-life/) so I followed the steps for removing the nVidia libraries and bumblebee figuring that it would work for ironhide and it seemed to - on the autoremove step ironhide was removed.

Now I am running into some problems.  When I run ```
sudo apt-get install nvidia-current nvidia-settings acpi-call-dkms
``` I got the message "No candidate for acpi-call-dkms."  Installing the two nvidia packages by themselves worked, and I found [these instructions](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html) on installing acpi-call a diffferent way, so I did that.  On the last step I get ```
:~/acpi_call$ sudo ./test_off.sh
Trying \_SB.PCI0.P0P1.VGA._OFF: failed
Trying \_SB.PCI0.P0P2.VGA._OFF: failed
Trying \_SB_.PCI0.OVGA.ATPX: failed
Trying \_SB_.PCI0.OVGA.XTPX: failed
Trying \_SB.PCI0.P0P3.PEGP._OFF: failed
Trying \_SB.PCI0.P0P2.PEGP._OFF: failed
Trying \_SB.PCI0.P0P1.PEGP._OFF: failed
Trying \_SB.PCI0.MXR0.MXM0._OFF: failed
Trying \_SB.PCI0.PEG1.GFX0._OFF: failed
Trying \_SB.PCI0.PEG0.GFX0.DOFF: works!
```

So the last one seems to have worked.  Unplugging my AC adapter now tells me I've got an extra 45 minutes or so but the figure is still low (2:45 from full charge).

So now I try to install ironhide ```
sudo apt-get install ironhide
``` and I get ```
E: Unable to locate package ironhide
```  I have run and rerun ```
sudo add-apt-repository ppa:mj-casalogic/ironhide
``` and ```
sudo apt-get update
``` then retried but with no success.  The PPA has files in /var/apt/lists and the file ppa.launchpad.net_mj-casalogic_ironhide_ubuntu_dists_oneiric_main_binary-amd64_Packages contains an ironhide entry.

So I'm pretty much stuck for ideas, can anyone help me?

EDIT: I should mention that now if I try to run ```
sudo apt-get install acpi_call_dkms
``` I get the same error as ironhide, and I don't get the candidate error anymore. *I know I already install acpi_call through a different method but I thought that information might be relevant...

Thanks in advance


EDIT: I have run ```
apt-get clean
``` I have used purge-ppa to remove the ironhide repository and then re-added and tried to install, I have run ```
apt-get upgrade
```and```
apt-get update-dist
```and none of it works... :(

---

### Post by DanPower on 2012-03-11
Hi again, I have since installed pyJupiter.. I'm not sure if it's relevant but after a reboot it doesn't seem to do anything.. changing modes makes no difference to the battery life estimate.  In fact, after installing Jupiter the battery life from a full charge has dropped from 2:45 to 1:50..

---

### Post by fuduntu on 2012-03-12
> **DanPower said:**
> Hi again, I have since installed pyJupiter.. I'm not sure if it's relevant but after a reboot it doesn't seem to do anything.. changing modes makes no difference to the battery life estimate.  In fact, after installing Jupiter the battery life from a full charge has dropped from 2:45 to 1:50..

You did not install Jupiter, please don't confuse the two.  pyJupiter is likely to be pulled upstream, but for now they are two completely different products.

---

### Post by DanPower on 2012-03-12
CORRECTION: Hi again, I have since installed pyJupiter.. I'm not sure if it's relevant but after a reboot it doesn't seem to do anything.. changing modes makes no difference to the battery life estimate. In fact, after installing **py**Jupiter the battery life from a full charge has dropped from 2:45 to 1:50..

@fuduntu - thankyou for pointing out my 2-letter typo.  While I've got you here, do you have any suggestions about my actual problem?

---

### Post by shizz on 2012-03-12
Hi Dan. I have the same laptop as you and have IRONHIDE working. What I recommend is starting the install again and follow this tutorial [http://ubuntuforums.org/showthread.php?p=11318882](http://ubuntuforums.org/showthread.php?p=11318882) 

Take note of reply 3 by Croo before attempting it as he corrects an error made by the original poster. 

Also, for part 6 of the tutorial, as explained in part 5, you will need to change part of the command to include your laptop type. so where you see ".lenovo.ThinkPadT420" you need to replace it with ".asus.N53Sv"

I hope this helps.

---

### Post by fuduntu on 2012-03-12
> **DanPower said:**
> CORRECTION: Hi again, I have since installed pyJupiter.. I'm not sure if it's relevant but after a reboot it doesn't seem to do anything.. changing modes makes no difference to the battery life estimate. In fact, after installing **py**Jupiter the battery life from a full charge has dropped from 2:45 to 1:50..

@fuduntu - thankyou for pointing out my 2-letter typo.  While I've got you here, do you have any suggestions about my actual problem?

NP, It's unfortunate that this applet is out there because it's being pulled upstream (the author is a new team member).  On topic though, check and make sure that the the 'jupiter' group is at the very bottom of /etc/sudoers.

I don't think they have shifted to /etc/sudoers.d yet but I could be wrong.

---

### Post by DanPower on 2012-03-12
Hi Shizz, thanks for that link.. here's what I get when I follow the first bit:```
-N53SV:~$ sudo add-apt-repository ppa:mj-casalogic/ironhide
[sudo] password for : 
You are about to add the following PPA to your system:
 Ironhide
 Ironhide is the continuation of bumblebee
 More info: https://launchpad.net/~mj-casalogic/+archive/ironhide
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Rj3io3r9gZ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B71FFE7D8F72DE5509A5FD3EC7305B5ECF7E0B3
gpg: requesting key ECF7E0B3 from hkp server keyserver.ubuntu.com
gpg: key ECF7E0B3: "Launchpad PPA for MrMEEE" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
-N53SV:~$ sudo apt-get update && upgrade
Ign http://jp.archive.ubuntu.com oneiric InRelease                             
Ign http://jp.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://jp.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Hit http://jp.archive.ubuntu.com oneiric Release.gpg                           
Get:1 http://jp.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://jp.archive.ubuntu.com oneiric-backports Release.gpg                 
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Get:3 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Hit http://jp.archive.ubuntu.com oneiric Release                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release                                   
Get:4 http://jp.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Get:5 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Get:6 http://security.ubuntu.com oneiric-security Release [40.8 kB]            
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://jp.archive.ubuntu.com oneiric-backports Release                     
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Get:7 http://ppa.launchpad.net oneiric Release [9,763 B]                       
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://jp.archive.ubuntu.com oneiric/main Sources                          
Hit http://jp.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://jp.archive.ubuntu.com oneiric/universe Sources                      
Hit http://jp.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://jp.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://jp.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://jp.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://jp.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://jp.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://jp.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://jp.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://jp.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://jp.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://jp.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://jp.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://jp.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:8 http://jp.archive.ubuntu.com oneiric-updates/main Sources [130 kB]       
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign https://private-ppa.launchpad.net oneiric InRelease                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:9 http://security.ubuntu.com oneiric-security/main Sources [34.5 kB]       
Get:10 http://ppa.launchpad.net oneiric/main Sources [968 B]                   
Get:11 http://ppa.launchpad.net oneiric/main amd64 Packages [1,056 B]          
Get:12 http://ppa.launchpad.net oneiric/main i386 Packages [1,068 B]           
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Get:13 http://jp.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:14 http://jp.archive.ubuntu.com oneiric-updates/universe Sources [46.8 kB] 
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:15 http://jp.archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Get:16 http://security.ubuntu.com oneiric-security/restricted Sources [14 B]   
Get:17 http://security.ubuntu.com oneiric-security/universe Sources [12.2 kB]  
Get:18 http://security.ubuntu.com oneiric-security/multiverse Sources [1,654 B]
Get:19 http://security.ubuntu.com oneiric-security/main amd64 Packages [90.2 kB]
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:20 http://jp.archive.ubuntu.com oneiric-updates/main amd64 Packages [298 kB]
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Ign https://private-ppa.launchpad.net oneiric InRelease                        
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:21 http://security.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:22 http://security.ubuntu.com oneiric-security/universe amd64 Packages [30.4 kB]
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Get:23 http://security.ubuntu.com oneiric-security/multiverse amd64 Packages [3,194 B]
Get:24 http://security.ubuntu.com oneiric-security/main i386 Packages [90.4 kB]
Ign https://private-ppa.launchpad.net oneiric InRelease                        
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:25 http://jp.archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:26 http://jp.archive.ubuntu.com oneiric-updates/universe amd64 Packages [102 kB]
Hit https://private-ppa.launchpad.net oneiric Release.gpg                      
Get:27 http://security.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:28 http://security.ubuntu.com oneiric-security/universe i386 Packages [30.4 kB]
Hit https://private-ppa.launchpad.net oneiric Release.gpg                      
Get:29 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,362 B]
Hit https://private-ppa.launchpad.net oneiric Release.gpg                      
Get:30 http://security.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:31 http://security.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]
Get:32 http://security.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:33 http://security.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Ign http://dl.google.com stable InRelease                                      
Hit https://private-ppa.launchpad.net oneiric Release                          
Get:34 http://jp.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,202 B]
Get:35 http://jp.archive.ubuntu.com oneiric-updates/main i386 Packages [298 kB]
Get:36 http://security.ubuntu.com oneiric-security/main Translation-en [50.7 kB]
Hit https://private-ppa.launchpad.net oneiric Release                          
Get:37 http://dl.google.com stable Release.gpg [198 B]                         
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Hit https://private-ppa.launchpad.net oneiric Release                          
Hit https://private-ppa.launchpad.net oneiric/main amd64 Packages              
Hit https://private-ppa.launchpad.net oneiric/main i386 Packages               
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign https://private-ppa.launchpad.net oneiric/main TranslationIndex            
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:38 http://security.ubuntu.com oneiric-security/universe Translation-en [21.4 kB]
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Get:39 http://jp.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:40 http://jp.archive.ubuntu.com oneiric-updates/universe i386 Packages [103 kB]
Hit https://private-ppa.launchpad.net oneiric/main amd64 Packages              
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:41 http://dl.google.com stable Release [1,351 B]                           
Hit https://private-ppa.launchpad.net oneiric/main i386 Packages               
Ign https://private-ppa.launchpad.net oneiric/main TranslationIndex            
Get:42 http://jp.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]
Get:43 http://jp.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:44 http://jp.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:45 http://jp.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:46 http://jp.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://jp.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://jp.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://jp.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://jp.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://jp.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://jp.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://jp.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://jp.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Hit http://jp.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://jp.archive.ubuntu.com oneiric-backports/restricted i386 Packages    
Hit http://jp.archive.ubuntu.com oneiric-backports/universe i386 Packages      
Hit http://jp.archive.ubuntu.com oneiric-backports/multiverse i386 Packages    
Hit http://jp.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://jp.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://jp.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://jp.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://jp.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://jp.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://jp.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://jp.archive.ubuntu.com oneiric/universe Translation-en               
Get:47 http://jp.archive.ubuntu.com oneiric-updates/main Translation-en [141 kB]
Get:48 http://dl.google.com stable/main amd64 Packages [1,269 B]               
Hit https://private-ppa.launchpad.net oneiric/main amd64 Packages              
Hit https://private-ppa.launchpad.net oneiric/main i386 Packages       
Ign https://private-ppa.launchpad.net oneiric/main TranslationIndex            
Hit http://jp.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://jp.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Get:49 http://jp.archive.ubuntu.com oneiric-updates/universe Translation-en [61.8 kB]
Hit http://jp.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://jp.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://jp.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://jp.archive.ubuntu.com oneiric-backports/universe Translation-en     
Get:50 http://dl.google.com stable/main i386 Packages [1,256 B]                
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en
Ign https://private-ppa.launchpad.net oneiric/main Translation-en_US
Ign https://private-ppa.launchpad.net oneiric/main Translation-en
Ign https://private-ppa.launchpad.net oneiric/main Translation-en_US
Ign https://private-ppa.launchpad.net oneiric/main Translation-en
Ign https://private-ppa.launchpad.net oneiric/main Translation-en_US
Ign https://private-ppa.launchpad.net oneiric/main Translation-en
Fetched 1,671 kB in 3min 0s (9,274 B/s)
W: Failed to fetch http://ppa.launchpad.net/marco/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/marco/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/marco/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/psyke83/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
danimal@danimal-N53SV:~$ sudo apt-get install ironhide ironhide-ui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ironhide
E: Unable to locate package ironhide-ui
:~$ 
```

Reading through the list of sources there, I can't see ironhide?

---

### Post by DanPower on 2012-03-13
So I removed the files referring to mj-casalogic from /etc/apt/sources.list.d and re-added the repo, and it worked.  ironhide installed and running glxgears gave me 60fps, optirun glxgears gave me messages about enabling/disabling the card and 1200fps.

BUT now after a reboot, optirun glxgears gives me no messages about the nvidia card and 60fps.  The only terminal output is the 'synchronized to refresh rate' message.  optirun just won't work.

Launching the ironhide indicator applet shows the card as OFF, running glxgears from this menu doesn't switch the card on.  Trying to run 'configure apps' or the Application Settings menu item both do nothing, which is the issue I was trying to fix in the first place...

Battery life has not changed, watching the battery rate it is hovering around 30,000mw steady which is no change from before.

This is starting to get really frustrating, what am I doing wrong?



EDIT: After another reboot, optirun command is now working again... *sigh* some consistency would be nice.

---

### Post by shizz on 2012-03-13
I'm sorry I can't be of much more help. I never use the graphics card with Ubuntu so I never really test it to be on or off. I just know it was being turned off as before it I got battery life of like an hour, where as after it I was getting up to 3:30 fully charged and idling.

How much battery life do you get fully charged?

---

