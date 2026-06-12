---
title: "Ubuntu/Muon Software Centre not downloading apps."
date: 2011-12-06
forum: New to Ubuntu
---

### Post by Chizzleface on 2011-12-06
Hi all!

I recently upgraded to kubuntu and am much loving the KDE-Plasma interface on it!

However, I'm having a bit of trouble with the Software Centres and downloading programs. 

[ubuntu software centre]Whenever I click on "Install" the button flashes to "installing" for a very brief second then back to the install button. No downloads ever happen, and I don't get asked for my password. 

[muon software centre]Whenever I try to install through this it simply says I don't have the permission to do this. 

When I run commands for install in Terminal, the downloads happen just fine, same with Synaptic - but I'd much prefer the easier option of using the software centres! Is there anything that could be causing this issue, and how do I solve it?

Cheers!

---

### Post by oldos2er on 2011-12-06
Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a konsole, and post the output here?

---

### Post by Chizzleface on 2011-12-06
```
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://gb.archive.ubuntu.com oneiric InRelease                             
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://gb.archive.ubuntu.com maverick-backports InRelease                  
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                           
Get:1 http://gb.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://gb.archive.ubuntu.com maverick-backports Release.gpg                
Hit http://gb.archive.ubuntu.com oneiric Release                               
Get:2 http://gb.archive.ubuntu.com oneiric-updates Release [32.4 kB]           
Get:3 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://gb.archive.ubuntu.com maverick-backports Release                    
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric/main Sources                          
Hit http://gb.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://gb.archive.ubuntu.com oneiric/universe Sources                      
Hit http://gb.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://gb.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://gb.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://gb.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://gb.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:4 http://gb.archive.ubuntu.com oneiric-updates/main Sources [94.3 kB]      
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Get:5 http://gb.archive.ubuntu.com oneiric-updates/restricted Sources [1,348 B]
Get:6 http://gb.archive.ubuntu.com oneiric-updates/universe Sources [25.8 kB]  
Get:7 http://gb.archive.ubuntu.com oneiric-updates/multiverse Sources [1,992 B]
Get:8 http://gb.archive.ubuntu.com oneiric-updates/main i386 Packages [219 kB] 
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:9 http://gb.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,935 B]
Get:10 http://gb.archive.ubuntu.com oneiric-updates/universe i386 Packages [64.1 kB]
Get:11 http://gb.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [4,396 B]
Get:12 http://gb.archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]
Get:13 http://gb.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:14 http://gb.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:15 http://gb.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://gb.archive.ubuntu.com maverick-backports/main Sources               
Hit http://gb.archive.ubuntu.com maverick-backports/restricted Sources         
Hit http://gb.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://gb.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://gb.archive.ubuntu.com maverick-backports/main i386 Packages         
Hit http://gb.archive.ubuntu.com maverick-backports/restricted i386 Packages   
Hit http://gb.archive.ubuntu.com maverick-backports/universe i386 Packages     
Hit http://gb.archive.ubuntu.com maverick-backports/multiverse i386 Packages   
Ign http://gb.archive.ubuntu.com maverick-backports/main TranslationIndex      
Ign http://gb.archive.ubuntu.com maverick-backports/multiverse TranslationIndex
Ign http://gb.archive.ubuntu.com maverick-backports/restricted TranslationIndex
Ign http://gb.archive.ubuntu.com maverick-backports/universe TranslationIndex  
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://gb.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com oneiric-updates/universe Translation-en       
Ign http://gb.archive.ubuntu.com maverick-backports/main Translation-en_GB     
Ign http://gb.archive.ubuntu.com maverick-backports/main Translation-en        
Ign http://gb.archive.ubuntu.com maverick-backports/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com maverick-backports/multiverse Translation-en  
Ign http://gb.archive.ubuntu.com maverick-backports/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com maverick-backports/restricted Translation-en  
Ign http://gb.archive.ubuntu.com maverick-backports/universe Translation-en_GB 
Ign http://gb.archive.ubuntu.com maverick-backports/universe Translation-en    
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://archive.canonical.com maverick InRelease
Ign http://archive.canonical.com oneiric InRelease                   
Hit http://archive.ubuntu.com oneiric Release.gpg                    
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://archive.canonical.com maverick Release.gpg
Hit http://archive.ubuntu.com oneiric Release  
Hit http://security.ubuntu.com oneiric-security Release               
Hit http://archive.canonical.com oneiric Release.gpg                  
Hit http://archive.canonical.com maverick Release                     
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://archive.canonical.com oneiric Release
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources     
Hit http://security.ubuntu.com oneiric-security/multiverse Sources   
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.canonical.com maverick/partner Sources            
Hit http://archive.canonical.com maverick/partner i386 Packages      
Ign http://archive.canonical.com maverick/partner TranslationIndex   
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB         
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Ign http://archive.canonical.com oneiric/partner TranslationIndex    
Hit http://archive.ubuntu.com oneiric/main Translation-en            
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Ign http://archive.canonical.com maverick/partner Translation-en_GB
Ign http://archive.canonical.com maverick/partner Translation-en               
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Ign http://archive.canonical.com oneiric/partner Translation-en                
Fetched 446 kB in 6s (72.3 kB/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Lots of stuff there, no error messages that I can see.

---

### Post by oldos2er on 2011-12-06
Are you using 11.10 or 10.10? You've got repositories for both listed, which I imagine is causing your problem.

---

### Post by Chizzleface on 2011-12-06
> **oldos2er said:**
> Are you using 11.10 or 11.04? You've got repositories for both listed, which I imagine is causing your problem.

11.10 - I upgraded Ubuntu from 11.04 and then added the KDE package to it after that.

---

### Post by oldos2er on 2011-12-06
Then edit your sources.list ```
kdesudo kate /etc/apt/sources.list
``` and either delete or comment out (#) all the maverick lines. When you're done, run ```
sudo apt-get update
``` again, and Software Center should work.

---

### Post by kio_http on 2011-12-06
Or you can use my sources.lst 

Its a clean on with KDE updates and virtual box repos



```
# 

# deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted

# deb cdrom:[Kubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111011)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mu.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://mu.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://download.virtualbox.org/virtualbox/debian oneiric contrib
deb-src http://download.virtualbox.org/virtualbox/debian oneiric contrib
```

---

### Post by Chizzleface on 2011-12-06
All maverick repositories removed, but still having the same issue :(

I tried in Muon again to replicate the error message:

```
Authentication Failure.

This operation cannot continue since proper authorization was not provided
```

---

### Post by kio_http on 2011-12-06
> **Chizzleface said:**
> All maverick repositories removed, but still having the same issue :(

I tried in Muon again to replicate the error message:

```
Authentication Failure.

This operation cannot continue since proper authorization was not provided
```

The password you are providing is incorrect.

If it is correct check muon package manager instead of muon software center and tell me it that works. The link in my signature provides some information on resetting KDE to defaults if you are interested.

---

### Post by Chizzleface on 2011-12-06
> **kio_http said:**
> The password you are providing is incorrect.

If it is correct check muon package manager instead of muon software center and tell me it that works. The link in my signature provides some information on resetting KDE to defaults if you are interested.

I get the same error message in package manager - in both cases it does not ask for a password at all, just comes up with the error message.

---

### Post by kio_http on 2011-12-06
> **Chizzleface said:**
> I get the same error message in package manager - in both cases it does not ask for a password at all, just comes up with the error message.

Try in terminal

```
sudo apt-get purge policykit-1 policykit-desktop-privileges polkit-kde-1
```
then
```
sudo apt-get install policykit-1 policykit-desktop-privileges polkit-kde-1
```
now open muon again
If this fails a temporary workarround is to press ALT+ F2 "kdesudo muon" or ALT+F2 "kdesudo muon-installer

You can also update to the latest version of muon like this
```
sudo apt-add-repository ppa:echidnaman/qapt-experimental 
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by linuxrev on 2011-12-06
I liked Muon too at first sight, but since it messed up my first (rather large) update after installation, I switched back to good old Synaptic, despite the ugly GTK+ interface...

---

### Post by Chizzleface on 2011-12-07
> **kio_http said:**
> Try in terminal

```
sudo apt-get purge policykit-1 policykit-desktop-privileges polkit-kde-1
```then
```
sudo apt-get install policykit-1 policykit-desktop-privileges polkit-kde-1
```now open muon again

Indirectly, this has sorted the problem! Running these commands removed both Muon and Ubunto Software centers, and once I had re-installed Ubuntu Software Center from Synaptic, it has resolved the problem and I am now able to download the programs!

Cheers for your help ^_^

---

### Post by NormanFLinux on 2012-09-23
Muon is the crappiest set of update utilities KDE ever designed.

This is the first package manager I have seen that uninstalled itself and vanished from the desktop. When I reinstalled it, I had no way to run it and its sister applications with privilege except through Konsole. :)

Kubuntu really needs to work on producing a quality package manager. Synaptic presented none of those problems. I've always liked it. Why Kubuntu can't use what Ubuntu used reliably for over a decade is something only their quality assurance department folks can answer.

I like KDE but this was ridiculous! :lolflag:

---

### Post by oldos2er on 2012-09-23
> **NormanFLinux said:**
>  Why Kubuntu can't use what Ubuntu used reliably 

It can: ```
sudo apt-get install synaptic
```

---

