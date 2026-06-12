---
title: "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by koolninad on 2013-02-07
Hello I am using Lubuntu in my Comapaq Presario V3000 Laptop. I dont have wireless driver for my laptop hence tried to install them but it gets struct in between and i am unable to install any other thing I also tried installing driver offline but with no gains.
when i try installing new software or update i get this message 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

and when I enter this command in terminal "sudo dpkg --configure -a"

it echo some line and gets stuck at Unable to connect lwfinger.com

I aslo tried clearing lock and other stuff available on google and ubuntu forum 

please help me sooo and thanks in advance

---

### Post by ibjsb4 on 2013-02-07
Open a terminal and enter:

```
sudo apt-get update
```

And please post any errors.

---

### Post by zombifier25 on 2013-02-07
Also post the output of these commands:
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

---

### Post by koolninad on 2013-02-07
prodigy@prodigy:~$ sudo apt-get update
[sudo] password for prodigy: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by koolninad on 2013-02-07
prodigy@prodigy:~$ cat /etc/apt/sources.list
# deb cdrom:[Lubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ quantal main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main



prodigy@prodigy:~$ ls /etc/apt/sources.list.d/
n-muench-programs-ppa-quantal.list


This are the output of the 2 commands you said

---

### Post by zombifier25 on 2013-02-08
> **koolninad said:**
> prodigy@prodigy:~$ sudo apt-get update
[sudo] password for prodigy: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

You should reboot the machine and run that command again. Don't forget to post the entire output.

---

### Post by koolninad on 2013-02-08
Now I have rebooted my machine and output is this....

Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal InRelease                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates InRelease 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports InRelease
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                             
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates Release.gpg [933 B]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg [316 B]                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                           
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [28.4 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal Release                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources/DiffIndex
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages/DiffIndex           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [13.8 kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [691 B]   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports Release            
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [73.0 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main Sources                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted Sources                    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe Sources                      
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [34.4 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse Sources                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main i386 Packages             
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,385 B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse i386 Packages     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main Translation-en                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe Translation-en               
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main Sources [75.1 kB]     
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted Sources [1,302 B]
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe Sources [77.2 kB] 
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse Sources [2,936 B]
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main i386 Packages [186 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted i386 Packages [3,067 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe i386 Packages [163 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,112 B]
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main Translation-en [90.0 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe Translation-en     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) quantal-backports/universe Translation-en_US
Fetched 860 kB in 38s (22.2 kB/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6804EA8EAE0D85C

---

### Post by ibjsb4 on 2013-02-09
Did this get fixed?  If not the first link should work for you.

[NO_PUBKEY]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=NO_PUBKEY&as_qdr=all&sa=Google+Search&lang=en")

---

### Post by koolninad on 2013-02-25
noo it didnt work for me... m still facing the same proble

---

