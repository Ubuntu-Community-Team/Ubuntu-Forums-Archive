---
title: "Help upgrading from Natty 11.04 to 11.10 Oneiric"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by avanman on 2012-11-29
Hello,

I've recently upgraded from 10.04 to 10.10 then to 11.04.  I now want to move to 11.10.  But I'm having some problems whenever I do apt-get update.  The update manager also crashes whenever I try to open it.  Here is the output of apt-get update:

E: Type '/etc/apt/sources.list' is not known on line 49 in source list /etc/apt/sources.list
E: The list of sources could not be read.

And here is my sources.list (the spaces between blocks of text are as they appear in the list, I did not modify them here):

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-security universe
# deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) maverick contrib non-free # disabled on upgrade to maverick
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed restricted main universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports restricted main multiverse universe
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

/etc/apt/sources.list

Also, here is the error message upon opening the update manager: "Could not initialize the package information

An unresolvable problem occured while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message: 'E:Type '/etc/apt/sources.list' is not known on line 49 in sources list /etc/apt/sources.list'"

Any help or suggestions would be greatly appreciated.  Thanks in advance,

avanman

---

### Post by snowpine on 2012-11-29
Edit the file with:

```
gksu gedit /etc/apt/sources.list
```

or

```
sudo nano /etc/apt/sources.list
```

Delete line 49 that says:

```
/etc/apt/sources.list
```

Save the file, quit, and try again.

Also see here (since 11.04 is out of support): [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by claracc on 2012-11-29
I think the problem is in the last line:

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository

You need to introduce a new line in order to have two separate lines:

deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
#Third party developers repository

---

### Post by avanman on 2012-11-29
Thanks for the replies.  I deleted the last line and that solved the particular issue, but now running apt-get update yields the following output:

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security InRelease            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed InRelease            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports InRelease           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security Release.gpg                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release.gpg         
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security Release                        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main amd64 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main amd64 Packages            
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                         
  404  Not Found
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main amd64 Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe amd64 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Further, when I check for updates in the update manager, after checking, I get this error message:

Failed to download repository information.

W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Not sure what to do.  Thanks,

avanman

---

### Post by claracc on 2012-11-29
This is the expected behaviour since ubuntu natty 11.04 reached its end of life on october 28, so you will not receive more security updates.

You will have to install a supported ubuntu release.

---

### Post by snowpine on 2012-11-29
Recommend to read this (since 11.04 is out of support): [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Fresh reinstall is often the fastest and most stable option.

---

### Post by avanman on 2012-11-29
So if I were to go directly to installing 12.04 LTS, I should back up my files and everything because they won't transfer right?

---

### Post by snowpine on 2012-11-29
> **avanman said:**
> So if I were to go directly to installing 12.04 LTS, I should back up my files and everything because they won't transfer right?

You should back up your files because it is good to have a back up. :)

Whether or not the 12.04 installer will overwrite your existing files depends on which options you choose. If you use the whole disk, or re-use your existing Ubuntu partitions, then yes, they'll be gone. If you have a separate /home partition and don't format it, then your user files/settings will be preserved (but that's no excuse not to have a backup), and if you do a "dual boot" of 12.04 side by side with 11.10 then your files will also be separate.

Also I highly recommend you test drive a Live DVD of the new release first, as there have been drastic changes to the interface as well as some difficulties with certain hardware.

---

