---
title: "Update failed. No further upgrades allowed."
date: 2013-10-04
forum: New to Ubuntu
---

### Post by dwjeanes2 on 2013-10-04
I started an update. It ran for a couple of hours, and was proceeding. I went to bed. When I got up, the update was still running, but had made no progress for 7 hours. I tried to cancel it using the gui, no luck. I then killed the process and rebooted. When I tried to restart the update after the reboot, some flag somewhere is set saying that an update is already running. 

What do I do now?

Please let me know what further info is needed, if any. Ubuntu v 12.04 on a Dell Latitude D620 (yes, it's old). Please give paths for any log files that are needed.

Thanks

---

### Post by bapoumba on 2013-10-04
Please open a terminal an paste the outputs to:
```
cat /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dwjeanes2 on 2013-10-04
david@david-Latitude-D620:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
david@david-Latitude-D620:~$ 


[sudo] password for david: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@david-Latitude-D620:~$ 









david@david-Latitude-D620:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@david-Latitude-D620:~$ 



There ya go... :)

---

### Post by Buntu Bunny on 2013-10-04
Were you trying to update to 12.04?

---

### Post by Old_Grey_Wolf on 2013-10-05
> **dwjeanes2 said:**
> [sudo] password for david: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

david@david-Latitude-D620:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@david-Latitude-D620:~$ 


It looks like you have a partial upgrade that has locked dpkg. Try these commands to clear the lock:
```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```

---

### Post by dwjeanes2 on 2013-10-05
> **Old_Grey_Wolf said:**
> It looks like you have a partial upgrade that has locked dpkg. Try these commands to clear the lock:
```
sudo rm -rf /var/lib/apt/lists/*

sudo apt-get update

sudo apt-get dist-upgrade
```



david@david-Latitude-D620:~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for david: 
david@david-Latitude-D620:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338 B]                                                                                                                       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                                                                                                     
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                                                                                                            
Get:5 [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg [490 B]                                                                                   
Get:6 [http://repo.steampowered.com](http://repo.steampowered.com) precise Release [2,303 B]                                                                                                              
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]                                                                                                       
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                                                                                  
Get:9 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [464 B]                                                                                                              
Get:10 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources [548 B]                                                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                     
Get:11 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [799 B]                                                                                                   
Get:12 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [8,928 B]                                                                                               
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam TranslationIndex                                                                                                           
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [89.6 kB]                                                                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                                    
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]                                                                                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                                                       
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [28.1 kB]                                                                                             
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,804 B]                                                                         
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [343 kB]                                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                                                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                                  
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US                                                                 
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]                                            
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [86.3 kB]                                                                   
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                                                                                         
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,640 B]                                                                 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]                                                     
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]                                     
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]                                     
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]                                       
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [156 kB]                                           
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [1,299 B]                                                   
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [1,253 B]                                                       
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [52.6 kB]                                                         
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                                                                                 
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]     
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]               
Get:32 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]
Get:34 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB] 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]         
Get:36 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [8,130 B]
Get:37 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [10.8 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex          
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]                                                                                                  
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]                                                                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                                                                  
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                                                                   
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]                                                                                                 
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]                                                                                            
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]                                                                                             
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                                                                             
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]                                                                                               
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]                                                                                         
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]                                                                                         
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]                                                                                           
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [420 kB]                                                                                                 
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]                                                                                          
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [96.2 kB]                                                                                            
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,343 B]                                                                                          
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [714 kB]                                                                                           
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]                                                                                    
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [221 kB]                                                                                       
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.0 kB]                                                                                    
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                                                                       
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                                                                                 
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                                                                                 
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                                                                   
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en [726 kB]                                                                                                  
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]                                                                                           
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en [2,395 B]                                                                                           
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en [3,341 kB]                                                                                            
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [313 kB]                                                                                          
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [8,064 B]                                                                                   
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en [2,637 B]                                                                                   
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [127 kB]                                                                                      
Fetched 19.4 MB in 26s (721 kB/s)                                                                                                                                         
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@david-Latitude-D620:~$ 
david@david-Latitude-D620:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@david-Latitude-D620:~$ 

Here is the full standard output above.

---

### Post by Bashing-om on 2013-10-05
dwjeanes2; Strange, 

let's get a better handle on what is not going on.
These questions are relevant:
[quote=Buntu Bunny]
Were you trying to update to 12.04?
[/quote]
[quote=Old_Grey_Wolf]
It looks like you have a partial upgrade that has locked dpkg
[/quote]


If the above is true, AND you have no other instance of a package manager open at the same time . AND you have rebooted the system;
As it appears Old_Grey_Wolf's worthy advise did not have the desired result:
Then try:
```

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
sudo apt-get update
sudo apt-get dist-upgrade

```

[INDENT]proper procedure for particular instance
[/INDENT]

---

### Post by Old_Grey_Wolf on 2013-10-05
Bashing-om is correct. I provided the command to clear the apt/list but forgot the command to clear the lock.

---

### Post by bapoumba on 2013-10-05
Hello :)
And of course please make sure you have no other package manager open (synaptic, software center etc.).

---

### Post by dwjeanes2 on 2013-10-06
Ok, I have not yet done these last things. I will asap. 

I just want to say thanks for the help and advice. I love Ubuntu and the community is the best.

I'll post further after I do the above, whether successful or not.

Thanks again.

---

### Post by dwjeanes2 on 2013-10-06
> **Bashing-om said:**
> dwjeanes2; Strange, 

let's get a better handle on what is not going on.
These questions are relevant:




If the above is true, AND you have no other instance of a package manager open at the same time . AND you have rebooted the system;
As it appears Old_Grey_Wolf's worthy advise did not have the desired result:
Then try:
```

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock
sudo apt-get update
sudo apt-get dist-upgrade

```
[INDENT]proper procedure for particular instance
[/INDENT]


I believe all I was doing was updating 12.04, but I'm not gonna say that for certain. I just allowed the auto-updater to do it's thing. 

And yes, per my OP, the upgrade hung, sat overnight with no progress. There have been several reboots since, and I only use default upgrades through the Ubuntu site. I don't use any other package managers, nor do I use much of anything that isn't ubuntu specific. It's a pretty vanilla install, with wine, which I don't use since all the apps I need are native to ubuntu.

---

### Post by dwjeanes2 on 2013-10-06
> **dwjeanes2 said:**
> I believe all I was doing was updating 12.04, but I'm not gonna say that for certain. I just allowed the auto-updater to do it's thing. 

And yes, per my OP, the upgrade hung, sat overnight with no progress. There have been several reboots since, and I only use default upgrades through the Ubuntu site. I don't use any other package managers, nor do I use much of anything that isn't ubuntu specific. It's a pretty vanilla install, with wine, which I don't use since all the apps I need are native to ubuntu.

OK, that was pretty scary... The first line "sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock" caused my system to blank screen. no error messages, nothing except a dark screen and an ON power light... A reboot was successful, but I have no idea if it worked.

How can I check the status (results) to see if the above commands were successful before the system crashed? Do I just look for "/var/lib/dpkg/lock" to see if it was deleted?


update:

Well, I tried again, breaking the above commands into 2 lines. The first  "sudo fuser -cuk /var/lib/dpkg/lock" again caused a black screen. I  looked in /var/lib/dpkg and lock is still there. How can I tell if the  fuser command worked?

---

### Post by dwjeanes2 on 2013-10-06
Well, I tried again, breaking the above commands into 2 lines. The first "sudo fuser -cuk /var/lib/dpkg/lock" again caused a black screen. I looked in /var/lib/dpkg and lock is still there. How can I tell if the fuser command worked?

---

### Post by Old_Grey_Wolf on 2013-10-06
Try these commands
```
sudo rm /var/lib/apt/lists/lock
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by dwjeanes2 on 2013-10-06
I got this when I did "sudo apt-get update"

...
Fetched 72 B in 6s (11 B/s)                                                                                                                                               
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by Old_Grey_Wolf on 2013-10-06
This is my last try. If it doesn't work maybe someone else will come along. Enter```
sudo rm /var/lib/dpkg/lock
sudo apt-get update
sudo apt-get dist-upgrade
```

This is without the sudo fuser -cuk /var/lib/dpkg/lock command that does interupt the graphic card communication.

---

### Post by dwjeanes2 on 2013-10-06
david@david-Latitude-D620:/var/lib/dpkg$ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                                                                                                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                                                                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                                                                                  
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg                                                                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                                                    
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise Release                                                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                                                                
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                                                                                                                    
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                                                                                                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                                              
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                                                                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                                                                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                                                                                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                                                                                                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                                                                                                    
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                                                                                   
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam TranslationIndex                                                                                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                                                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                                                          
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US                                                         
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
david@david-Latitude-D620:/var/lib/dpkg$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-54-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-54-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod..........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-54-generic
Building for architecture i686
Building initial module for 3.2.0-54-generic
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-54-generic/updates/dkms/

depmod........

DKMS: install completed.


_________________________________________________

after that, the shell did not return a command prompt. I am gonna let it sit for a while. Maybe it's busy.

---

### Post by Old_Grey_Wolf on 2013-10-06
It looks like it was updating and ran into a problem with your broadcom wireless driver. You have a different problem now unless it resolves itself. I would recommend starting a new thread if problems persist.

---

### Post by dwjeanes2 on 2013-10-06
> **Old_Grey_Wolf said:**
> It looks like it was updating and ran into a problem with your broadcom wireless driver. You have a different problem now unless it resolves itself. I would recommend starting a new thread if problems persist.

OK. What do I post in the new thread? Please let me know any commands to issue and post results from. 

Would It be best to just do a clean re-install? I'm not really interested in exploring why this happened, I just want a stable system. Perhaps there is a more current Ubuntu version that I can upgrade to.

---

### Post by Old_Grey_Wolf on 2013-10-06
Upgrading from 11.04 to 12.04 has it's risks. Did you upgrade to 11.10 then 12.04?

If you have backed up important files, reboot and see what happens. It may just work fine after a reboot. I would post this with an explanation that you were trying to upgrade to 12.04```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
david@david-Latitude-D620:/var/lib/dpkg$ sudo dpkg --configure -a
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.2) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...

-------- Uninstall Beginning --------
Module: bcmwl
Version: 6.20.155.1+bdcom
Kernel: 3.2.0-54-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
- Uninstallation
- Deleting from: /lib/modules/3.2.0-54-generic/updates/dkms/
- Original module
- No original module was found for this module on this kernel.
- Use the dkms install command to reinstall any previous module version.

depmod..........

DKMS: uninstall completed.

------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building only for 3.2.0-54-generic
Building for architecture i686
Building initial module for 3.2.0-54-generic
Done.

wl:
Running module version sanity check.
- Original module
- No original module exists within this kernel
- Installation
- Installing to /lib/modules/3.2.0-54-generic/updates/dkms/

depmod........

DKMS: install completed.
```You could just do a clean install if you want. Then resort the important files.

---

### Post by dwjeanes2 on 2013-12-21
My apologies if this is a duplicate post. My system is very unstable following a failed upgrade attempt. I was on 12.4, I believe, and was trying to go to the most current release. The upgrade hung and I am stuck with a terribly unstable system. I have no idea how to proceed. It has taken almost 20 minutes just to type this plea for help, due to the slowness of my system now. Any and all help would be greatly appreciated.

---

### Post by raja.genupula on 2013-12-21
This information is not enough. 

Any way you are in 12.04 , so that you can have a direct upgrade to 14.04 LTS

---

### Post by Bucky Ball on 2013-12-21
> **raja.genupula said:**
> This information is not enough. 

Any way you are in 12.04 , so that you can have a direct upgrade to 14.04 LTS

When it's released that is, and that is not for months yet. 

The only upgrade you can do from 12.04 without upgrading with a clean install is to 12.10, NOT the latest release, which is 13.10. So we can presume that is what you are attempting, an in-system upgrade to 12.10?

---

### Post by deadflowr on 2013-12-21
Did you shutdown/reboot when the upgrade appeared to hang?
Upgrades tend to have quite a few moments when the user needs to confirm a change.
Such as a new samba configuration package/file, or something like that.
It normally pops up a new window, but sometimes that window hides behind the upgrade window, or may even pop up in a different workspace.
This of course is mere speculation, by me.

Seeing that the state you are now in is borked(or at least slow and clucky) I would assume that all the packages downloaded and the repositories have changed to the newer version.
You might try seeing if the fix-broken packages command might fix the problem.
```
sudo apt-get install -f
```

Don't know if it'll work, but aside from trying, you might have to do a reinstall.
If you reinstall backup your files.
You can use the livecd to help do this, if it gets to that.

---

### Post by Bucky Ball on 2013-12-21
Your threads have been merged. Please do not start duplicate threads. Unsure why Old Grey Wolf advised you to start a new thread as you are getting plenty of help here. You dilute your chances of getting help by duplicating the same issue elsewhere.

As has been suggested, do a clean install of 12.04 easiest. Your latest post, as your previous, is a little ambiguous so just keep it simple and clean install.

---

### Post by dwjeanes2 on 2013-12-21
> **Bucky Ball said:**
> Your threads have been merged. Please do not start duplicate threads. Unsure why Old Grey Wolf advised you to start a new thread as you are getting plenty of help here. You dilute your chances of getting help by duplicating the same issue elsewhere.

As has been suggested, do a clean install of 12.04 easiest. Your latest post, as your previous, is a little ambiguous so just keep it simple and clean install.

That old report was an upgrade TO 12.4, not FROM 12.4. This was an attempt to upgrade FROM 12.4. Is the fix the same? I'm really not trying to re-raise that old issue, I just want to fix a new, to me, problem. My apologies if the posts appear to be the same issue, but the issue from October was fixed, and I was very grateful for the help.

It's fine to merge the threads, but I am worried that this might cloud the focus on my new problem.

Thanks

---

### Post by Bucky Ball on 2013-12-21
> **dwjeanes2 said:**
> OK. What do I post in the new thread? Please let me know any commands to issue and post results from. 

Would It be best to just do a clean re-install? I'm not really interested in exploring why this happened, I just want a stable system. Perhaps there is a more current Ubuntu version that I can upgrade to.

This was your last post in this thread in October. It does not appear to be fixed. The thread is also not marked as solved, therefore, as far as I can tell, it wasn't. 

Now you say you are in 12.04, you believe, but don't seem too sure. It doesn't sound like things have been going right for some time. You give no indication of what release you are, or were, attempting to upgrade to, or how, and no clue as to what actually went wrong, no detail of any errors or what you have done to try and fix. So ...

Either do a clean install of 12.04 LTS or 13.10. Both will upgrade to 14.04 LTS when it comes out and that is supported for five years.

I repeat, if you were running 12.04 LTS, and you don't seem certain of that, and trying to upgrade through update manager your only option would be to 12.10. That is supported for another six months and then you'll be doing this all over again. Whatever, a clean install will get you over this and back on track. Hopefully. ;)

---

### Post by dwjeanes2 on 2013-12-22
Ok, my apologies that the previous thread was not closed. I did believe that I had stated that the problem had been resolved, but, evidently, I did not. My bad. I will just do a clean install of 13.10 for now.

Please mark this issue closed.

---

### Post by Iowan on 2013-12-22
If you think the problem is solved, you can mark the thread as such:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

