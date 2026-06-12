---
title: "what do my apt-get update errors mean?"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by mark1977 on 2011-12-30
Hi,

When I run sudo apt-get update, I get the following warnings and error:

```
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                  
Ign http://archive.canonical.com natty InRelease                    
Ign http://mirror.bytemark.co.uk oneiric InRelease                   
Ign http://mirror.bytemark.co.uk oneiric-updates InRelease           
Ign http://mirror.bytemark.co.uk oneiric-backports InRelease         
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net oneiric InRelease                       
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]            
Hit http://archive.canonical.com oneiric Release.gpg                 
Ign http://mirror.bytemark.co.uk oneiric-security InRelease          
Hit http://mirror.bytemark.co.uk oneiric Release.gpg                 
Hit http://mirror.bytemark.co.uk oneiric-updates Release.gpg         
Hit http://ppa.launchpad.net oneiric Release.gpg                     
Hit http://ppa.launchpad.net oneiric Release.gpg                     
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://archive.canonical.com natty Release.gpg                   
Hit http://mirror.bytemark.co.uk oneiric-backports Release.gpg       
Hit http://ppa.launchpad.net oneiric Release.gpg                     
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://archive.canonical.com oneiric Release                     
Hit http://mirror.bytemark.co.uk oneiric-security Release.gpg        
Hit http://mirror.bytemark.co.uk oneiric Release                     
Hit http://extras.ubuntu.com oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://archive.canonical.com natty Release                       
Hit http://mirror.bytemark.co.uk oneiric-updates Release             
Hit http://extras.ubuntu.com oneiric/main i386 Packages              
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://archive.canonical.com oneiric/partner amd64 Packages      
Hit http://mirror.bytemark.co.uk oneiric-backports Release           
Hit http://mirror.bytemark.co.uk oneiric-security Release            
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://archive.canonical.com natty/partner amd64 Packages        
Hit http://mirror.bytemark.co.uk oneiric/main amd64 Packages         
Hit http://mirror.bytemark.co.uk oneiric/restricted amd64 Packages   
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://archive.canonical.com natty/partner i386 Packages         
Ign http://archive.canonical.com natty/partner TranslationIndex      
Hit http://mirror.bytemark.co.uk oneiric-updates/main amd64 Packages 
Hit http://mirror.bytemark.co.uk oneiric-updates/restricted amd64 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/main amd64 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/restricted amd64 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/universe amd64 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/multiverse amd64 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/main i386 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/restricted i386 Packages
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main i386 Packages              
Ign http://ppa.launchpad.net oneiric/main TranslationIndex           
Hit http://mirror.bytemark.co.uk oneiric-backports/universe i386 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/multiverse i386 Packages
Hit http://mirror.bytemark.co.uk oneiric-backports/main TranslationIndex
Hit http://mirror.bytemark.co.uk oneiric-backports/multiverse TranslationIndex
Hit http://mirror.bytemark.co.uk oneiric-backports/restricted TranslationIndex
Hit http://mirror.bytemark.co.uk oneiric-backports/universe TranslationIndex
Hit http://mirror.bytemark.co.uk oneiric-backports/main Translation-en
Hit http://mirror.bytemark.co.uk oneiric-backports/multiverse Translation-en
Hit http://mirror.bytemark.co.uk oneiric-backports/restricted Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB          
Hit http://mirror.bytemark.co.uk oneiric-backports/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://archive.canonical.com natty/partner Translation-en_GB     
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Fetched 72 B in 1s (51 B/s)
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.bytemark.co.uk/ubuntu/dists/oneiric/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.bytemark.co.uk/ubuntu/dists/oneiric-updates/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.bytemark.co.uk/ubuntu/dists/oneiric-security/Release  Unable to find expected entry 'non-free/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```And the contents of sources.list is:

```
more sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
#deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.bytemark.co.uk/ubuntu/ oneiric main restricted non-free
#deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric contrib universe non-free multiverse #Added by software-
properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric-updates main restricted non-free
#deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric-updates non-free restricted main multiverse universe #Ad
ded by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric universe contrib
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric multiverse
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric-backports main restricted universe multiverse
#deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric-backports main restricted universe multiverse #Added by 
software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner non-free
# deb-src http://archive.canonical.com/ubuntu oneiric partner

deb http://mirror.bytemark.co.uk/ubuntu/ oneiric-security main restricted non-free
deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric-security non-free restricted main multiverse universe #Ad
ded by software-properties
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric-security universe
deb http://mirror.bytemark.co.uk/ubuntu/ oneiric-security multiverse


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner




```Can you help explain what it means and how to fix it?

Thankyou!

---

### Post by Paqman on 2011-12-30
It's saying that it's getting corrupted lists of what software is available. Try switching to a different server and update again. You can switch servers in Software Sources > Install from > Other > Select best server.

---

### Post by mark1977 on 2011-12-30
Thanks paqman for your suggestion. I tried that but still get the same errors:

```
Fetched 1,638 kB in 5s (297 kB/s)                    
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirrors.coreix.net/ubuntu/dists/oneiric/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirrors.coreix.net/ubuntu/dists/oneiric-updates/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirrors.coreix.net/ubuntu/dists/oneiric-security/Release  Unable to find expected entry 'non-free/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Paqman on 2011-12-30
Hmm, well the only thing that's leaping out at me from your sources.list file is that you have the Partner repo enabled for both Natty and Oneiric. That's not right, so try removing the Natty line and see if it acts any less confused.

That's a bit of a stab in the dark though, I'm not sure if it's related to your problem at all.

---

### Post by mark1977 on 2011-12-30
Thanks for the idea paqman, but that didn't work...

---

### Post by mapreri on 2011-12-30
in ubuntu doesn't exist the "non-free" repository (there is in Debian).

in your sources.list delete "non-free" in all entry

---

### Post by mark1977 on 2011-12-30
Thanks mapreri - I did as you suggested and it got rid of all but one error!

```
sudo apt-get update
Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease                      
Ign http://ppa.launchpad.net oneiric InRelease                      
Ign http://mirrors.coreix.net oneiric InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                       
Ign http://archive.canonical.com oneiric InRelease                                               
Hit http://ppa.launchpad.net oneiric Release.gpg                                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                                                 
Hit http://extras.ubuntu.com oneiric Release.gpg                                                 
Hit http://archive.canonical.com oneiric Release.gpg                                             
Hit http://ppa.launchpad.net oneiric Release.gpg                     
Ign http://mirrors.coreix.net oneiric-updates InRelease              
Hit http://extras.ubuntu.com oneiric Release                         
Hit http://archive.canonical.com oneiric Release                                                 
Hit http://ppa.launchpad.net oneiric Release                                                      
Hit http://ppa.launchpad.net oneiric Release                                                      
Ign http://mirrors.coreix.net oneiric-backports InRelease                                                    
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                                                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                                              
Hit http://ppa.launchpad.net oneiric Release                                                     
Hit http://extras.ubuntu.com oneiric/main i386 Packages                                                      
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Ign http://archive.canonical.com oneiric/partner TranslationIndex                          
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                   
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                    
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                 
Ign http://mirrors.coreix.net oneiric-security InRelease                                   
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                   
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                                      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                   
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                                         
Hit http://ppa.launchpad.net oneiric/main i386 Packages                                          
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                 
Hit http://mirrors.coreix.net oneiric Release.gpg                                          
Hit http://mirrors.coreix.net oneiric-updates Release.gpg                                                    
Hit http://mirrors.coreix.net oneiric-backports Release.gpg                                                  
Hit http://mirrors.coreix.net oneiric-security Release.gpg                                                   
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                                                  
Ign http://archive.canonical.com oneiric/partner Translation-en_GB                               
Ign http://extras.ubuntu.com oneiric/main Translation-en                                         
Ign http://archive.canonical.com oneiric/partner Translation-en                                  
Hit http://mirrors.coreix.net oneiric Release                        
Hit http://mirrors.coreix.net oneiric-updates Release                                             
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                                       
Ign http://ppa.launchpad.net oneiric/main Translation-en                   
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB
Hit http://mirrors.coreix.net oneiric-backports Release
Ign http://ppa.launchpad.net oneiric/main Translation-en                                          
Hit http://mirrors.coreix.net oneiric-security Release                                            
Hit http://mirrors.coreix.net oneiric/universe amd64 Packages               
Hit http://mirrors.coreix.net oneiric-updates/universe amd64 Packages
Hit http://mirrors.coreix.net oneiric-updates/multiverse amd64 Packages
Hit http://mirrors.coreix.net oneiric-updates/universe i386 Packages
Hit http://mirrors.coreix.net oneiric-updates/multiverse i386 Packages
Hit http://mirrors.coreix.net oneiric-updates/multiverse TranslationIndex
Hit http://mirrors.coreix.net oneiric-updates/universe TranslationIndex
Hit http://mirrors.coreix.net oneiric-backports/main amd64 Packages
Hit http://mirrors.coreix.net oneiric-backports/restricted amd64 Packages
Hit http://mirrors.coreix.net oneiric-backports/universe amd64 Packages
Hit http://mirrors.coreix.net oneiric-backports/multiverse amd64 Packages
Hit http://mirrors.coreix.net oneiric-backports/main i386 Packages
Hit http://mirrors.coreix.net oneiric-backports/restricted i386 Packages
Hit http://mirrors.coreix.net oneiric-backports/universe i386 Packages
Hit http://mirrors.coreix.net oneiric-backports/multiverse i386 Packages
Hit http://mirrors.coreix.net oneiric-backports/main TranslationIndex
Hit http://mirrors.coreix.net oneiric-backports/multiverse TranslationIndex
Hit http://mirrors.coreix.net oneiric-backports/restricted TranslationIndex
Hit http://mirrors.coreix.net oneiric-backports/universe TranslationIndex
Hit http://mirrors.coreix.net oneiric-security/universe amd64 Packages
Hit http://mirrors.coreix.net oneiric-security/multiverse amd64 Packages
Hit http://mirrors.coreix.net oneiric-security/universe i386 Packages
Hit http://mirrors.coreix.net oneiric-security/multiverse i386 Packages
Hit http://mirrors.coreix.net oneiric-security/multiverse TranslationIndex
Hit http://mirrors.coreix.net oneiric-security/universe TranslationIndex
Hit http://mirrors.coreix.net oneiric-updates/multiverse Translation-en
Hit http://mirrors.coreix.net oneiric-updates/universe Translation-en
Hit http://mirrors.coreix.net oneiric-backports/main Translation-en
Hit http://mirrors.coreix.net oneiric-backports/multiverse Translation-en
Hit http://mirrors.coreix.net oneiric-backports/restricted Translation-en
Hit http://mirrors.coreix.net oneiric-backports/universe Translation-en
Hit http://mirrors.coreix.net oneiric-security/multiverse Translation-en
Hit http://mirrors.coreix.net oneiric-security/universe Translation-en
W: Failed to fetch http://mirrors.coreix.net/ubuntu/dists/oneiric/Release  Unable to find expected entry 'contrib/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```For reference, here is my updated sources.list:




```
cat sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
# deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Mark - all non-free don't exist in ubuntu (but they do in debian) so they should be commented out!
# deb http://mirrors.coreix.net/ubuntu/ oneiric main restricted non-free
# deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric contrib universe non-free multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://mirrors.coreix.net/ubuntu/ oneiric-updates main restricted non-free
# deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric-updates non-free restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.coreix.net/ubuntu/ oneiric universe contrib
deb http://mirrors.coreix.net/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.coreix.net/ubuntu/ oneiric multiverse
deb http://mirrors.coreix.net/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.coreix.net/ubuntu/ oneiric-backports main restricted universe multiverse
# deb-src http://mirror.bytemark.co.uk/ubuntu/ oneiric-backports main restricted universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner non-free
# deb-src http://archive.canonical.com/ubuntu oneiric partner

# deb http://mirrors.coreix.net/ubuntu/ oneiric-security main restricted non-free
# deb-src http://mirrors.coreix.net/ubuntu/ oneiric-security non-free restricted main multiverse universe #Added by software-properties
deb http://mirrors.coreix.net/ubuntu/ oneiric-security universe
deb http://mirrors.coreix.net/ubuntu/ oneiric-security multiverse


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
# deb-src http://extras.ubuntu.com/ubuntu oneiric main
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

```

---

### Post by spacecheck on 2011-12-30
So either comment out:   "deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) oneiric universe contrib"   or   remove "contrib" from that line.

Good luck

---

### Post by mapreri on 2011-12-30
your sources.list is horrible! :)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I suggest you to completely rewrite your file so as look like ```
##Official Ubuntu repository
deb http://mirrors.coreix.net/ubuntu/ oneiric main restricted universe multiverse
deb http://mirrors.coreix.net/ubuntu/ oneiric-updates main restricted universe multiverse
deb http://mirrors.coreix.net/ubuntu/ oneiric-backports main restricted universe multiverse
deb http://mirrors.coreix.net/ubuntu/ oneiric-security main restricted universe multiverse



deb http://archive.canonical.com/ubuntu oneiric partner
deb http://extras.ubuntu.com/ubuntu oneiric main
```
the "contrib" repository exist only in debian... you like debian, so :)


ps. sorry if i write misspelled, but I don't speak english so well...

---

### Post by Johnny3 on 2011-12-30
Would going to software sources and clicking revert reset things?
Thanks and God Bless Johnny3 65+++ old new bee

---

### Post by mark1977 on 2011-12-30
> **spacecheck said:**
> So either comment out:   "deb [http://mirrors.coreix.net/ubuntu/](http://mirrors.coreix.net/ubuntu/) oneiric universe contrib"   or   remove "contrib" from that line.

Good luck

Thanks, that fixed it!

---

### Post by mark1977 on 2011-12-30
> **mapreri said:**
> your sources.list is horrible! :)[]("https://help.ubuntu.com/community/Repositories/Ubuntu")
ps. sorry if i write misspelled, but I don't speak english so well...

Yeah, I agree :).

Your english seems good to me, thanks for your help and I am checking out that link.

---

