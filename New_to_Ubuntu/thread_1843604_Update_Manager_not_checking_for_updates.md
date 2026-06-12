---
title: "Update Manager not checking for updates"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by musicnotes on 2011-09-13
I have Update Manager set to check for updates daily, but when I ran Update Manager today (mainly out of curiosity), it said that it had not checked for updates for something like 136 days. Any idea why this is, or what I can do to fix it?  Running 11.04. Thanks.

---

### Post by Frogs Hair on 2011-09-13
Do you have the update manager set to notify only or is it set install updates automatically ? If there were no updates to install when you checked I would think they have been being installed automatically .

---

### Post by musicnotes on 2011-09-13
Nope, it's not set to notify only, it's set to install automatically, but nothing was installed for 4 months!

---

### Post by westie457 on 2011-09-13
Does the updates tab in Software Sources look very similar to this.

---

### Post by musicnotes on 2011-09-13
Yes, almost exactly the same, except I have it set to "Normal releases" rather than "Long-term releases only". Everything else is the same.

---

### Post by plucky on 2011-09-14
> **musicnotes said:**
> Yes, almost exactly the same, except I have it set to "Normal releases" rather than "Long-term releases only". Everything else is the same.

What does ```
sudo apt-get update
``` show you?



Also show us our sources.list ```
cat /etc/apt/sources.list
```

---

### Post by musicnotes on 2011-09-14
<user>@<computer>:~$ sudo apt-get update
[sudo] password for <user>: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty InRelease                                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty Release.gpg                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty Release                                     
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,209 B]                 
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty/main i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main TranslationIndex                       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [31.4 kB]             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [67.5 kB]         
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main Translation-en_US                      
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [10.6 kB]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [650 B]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [179 kB]   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [105 kB]        
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [14 B]    
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [25.2 kB]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [37.5 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,071 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,890 B] 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [318 kB]  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [92.2 kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,258 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
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
Fetched 910 kB in 3s (250 kB/s)
Reading package lists... Done
<user>@<computer>:~$

---

### Post by musicnotes on 2011-09-14
<user>@<computer>:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
<user>@<computer>:~$

---

### Post by plucky on 2011-09-14
That all looks good.

Now try ```
sudo apt-get upgrade
``` and post output.

Good Luck

---

### Post by musicnotes on 2011-10-12
> **plucky said:**
> That all looks good.

Now try ```
sudo apt-get upgrade
``` and post output.

Good Luck

<user>@<computer>:~$ sudo apt-get upgrade
[sudo] password for <user>: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I just checked it again and there were a ton of updates available, none of which were downloaded or installed automatically.

---

### Post by plucky on 2011-10-13
> I just checked it again and there were a ton of updates available, none of which were downloaded or installed automatically. 

Is that when using the **Update Manager?**

What does ```
sudo apt-get dist-upgrade
``` show you?

This command will not upgrade you to the next release,but might show you if there are held packages.


Good Luck

---

