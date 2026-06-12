---
title: "errors That I have been getting"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by manners2345 on 2008-09-22
For the last 20 days I have been trying to update my system. I have used package manager, update manager, apt-get update. 

I keep getting errors the last is as follows:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

THIS WHAT I GET FROM APT-GET

root@OlerThanDirt-laptop:/home/fred# apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]                    
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
  
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
  
Fetched 760B in 21s (35B/s)                                                    
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@OlerThanDirt-laptop:/home/fred# 

HOW DO I SOLVE THIS??????

manners2345

---

### Post by spiderbatdad on 2008-09-22
I would edit my sources list:```
gksu gedit /etc/apt/sources.list
```and place # marks at the beginnings of the lines for the entries 
 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B] [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]

---

### Post by Lan Zeird on 2008-09-22
is your error been resolved already?

---

### Post by manners2345 on 2008-09-22
I went to etc/apt/sources.list.  Do not find what you referenced. This is what I found!!

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

Also how do you do a thank you?? at my age CRS is ver pronounced. I found it a couple of times but cannot remember where!!!

manners2345

---

### Post by nothingspecial on 2008-09-22
Try removing the comment (#) from the line arrow 1 is pointing at.

Thanks can be given by clicking the star thingy (arrow 2)

[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=86070&stc=1&d=1222083491[/IMG]

Sorry that picture is not very clear, it`s the line that says -

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

---

### Post by manners2345 on 2008-09-22
Sorry it has taken this long to respond. when I shut down last night it was 2045 my time, it now 0830 the next day my time.

did what was suggested, removed # from line.

Then ran apt-get update, got the following: 


root@OlerThanDirt-laptop:/home/fred# apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]            
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release  
  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages                       
Fetched 191B in 6s (31B/s)                                                     
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
root@OlerThanDirt-laptop:/home/fred# 

Then ran update manager, got the following:



W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

This what I get from sources list now:

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

Do not see that symbol for thanks

anyway thank you 
manners2345

---

### Post by manners2345 on 2008-09-24
I have solved my problem. I went to the Software Sources in The Administration part of System and changed servers till I found one that did not show up with errors when ever I tried to update. When I finally found one there were close to 35 updates that needed to be applied.

Now All I have to do is remember how I did it!!!  CRS!!! Thank you to all that tried to help!!! If I could find the little thing with the star and ribbon I would use it, but cannot!!!!

manners2345

---

