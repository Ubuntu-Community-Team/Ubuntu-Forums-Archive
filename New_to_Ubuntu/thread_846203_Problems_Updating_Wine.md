---
title: "Problems Updating Wine"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Eric Qel-Droma on 2008-07-01
Hello!

On my laptop, I currently have Wine 0.9.59.  I'd like to update it as I have on my desktop.  I followed the instructions on the Ubuntu/Debian page on winehq, and when I run my update manager right now, I get a listing for Wine, but it is "grayed out" and I can't check it.  What's going on?

Thanks!

---

### Post by Hospadar on 2008-07-01
what happens when you ```
sudo apt-get update
sudo apt-get upgrade
``` in a terminal

---

### Post by pedro_orange on 2008-07-01
There is a totally bitchin' sticky on the WINE section of the Ubuntu forums that tells you how to install the latest version of WINE.

This is step by step stuff that you literally paste into Terminal, use it, love it!

:)

---

### Post by Tatty on 2008-07-01
[http://ubuntuforums.org/showthread.php?t=559105](http://ubuntuforums.org/showthread.php?t=559105)

According to this thread it is because of possible dependency conflicts.  

Im not sure but i would assume it is because the wine you have installed currently is from the official ubuntu repository, and is probably tweaked slightly from the official wine respoitory.

So perhaps you should first try uninstalling the version of wine you have installed currently.  As i say im not sure but this seems like a logical thing to try.

---

### Post by Eric Qel-Droma on 2008-07-01
> **Hospadar said:**
> what happens when you ```
sudo apt-get update
sudo apt-get upgrade
``` in a terminal

I get:
```
eric@eric-laptop:~$ sudo apt-get update
[sudo] password for eric: 
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Hit http://security.ubuntu.com hardy-security/restricted Sources               
Hit http://security.ubuntu.com hardy-security/universe Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://dl.google.com stable Release.gpg                                    
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/non-free Packages                              
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Hit http://wine.budgetdedicated.com etch Release.gpg
Ign http://wine.budgetdedicated.com etch/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Hit http://wine.budgetdedicated.com etch Release
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release              
Ign http://wine.budgetdedicated.com etch/main Packages              
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://wine.budgetdedicated.com etch/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://wine.budgetdedicated.com etch/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
eric@eric-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  wine
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
eric@eric-laptop:~$ 

```

---

### Post by Eric Qel-Droma on 2008-07-01
> **pedro_orange said:**
> There is a totally bitchin' sticky on the WINE section of the Ubuntu forums that tells you how to install the latest version of WINE.

This is step by step stuff that you literally paste into Terminal, use it, love it!

:)

Sorry.  I did a search before posting this thread.  I hadn't noticed that there was a whole WINE forum.  I'll check there in the future.

:-)

Eric

---

### Post by nowshining on 2008-07-01
lol

Next time let us know ur OS version of Ubuntu. :)

---

