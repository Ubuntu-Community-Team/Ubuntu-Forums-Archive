---
title: "Tons of error reports, hang-ups, failing repositories all since I last updated..."
date: 2013-03-20
forum: New to Ubuntu
---

### Post by vadertater on 2013-03-20
I have a toshiba c885-s5239 running Ubuntu 12.10 64-bit. I updated two days ago when the software center said new updates were available. Now I keep getting a red caution symbol up by the time and drop down menus in the upper right hand corner. It says I may have failing repositories that I need to fix... no idea how to find those and then how to fix those.

I also get "possible GPU hang ups" continously. The error/bug notification are constantly popping up. If I'm using my laptop for 1 hour, I probable get like 20 of these messages.

I haven't noticed that I can't use Ubuntu, but when I am scrolling down a page on Mozilla, sometimes it will stop and freeze... then come back and continue where I left off. I assume that is a GPU Hang-up?? 

The only thing I've done with ubuntu is use it for school (and a bit of movie/games). I have downloaded and installed redshift, battle for wesnoth, update it, pithos, google calendar app, stellarium, WINE, spotify, etc. The craziest thing I had to do was install a driver for my wireless because toshibas wireless card's aren't compatible with linux. But all these issues started after the last update two days ago.

Anybody have this happen to them? Or know how to diagnose this problem? :confused:

---

### Post by Bashing-om on 2013-03-20
vadertater; Hi !

Let's see what can be done to get to the bottom of this.
Post -between the code tags "#"- the output of terminal codes:
```
 sudo apt-get update ##this updates the repositories database
sudo apt-get upgrade ##this updates your packages and generates the errors/why can not upgrade
cat /etc/apt/sources.list ##prints your apt to get file
ls -la /etc/apt/sources.list.d/ ##list any 3rd party PPAs you have installed

```[INDENT=2]we'll see what is to be seen

[/INDENT]

---

### Post by vadertater on 2013-03-20
You want me to post the whole output for each?? It's quite a bit...

```
nate@nate-Satellite-C855:~$ sudo apt-get update
[sudo] password for nate: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]          
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg [933 B]         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [36.3 kB]       
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                      
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [15.4 kB]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages             
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [692 B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [98.6 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [43.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en             
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1,150 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [98.0 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources [83.1 kB]     
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources [1,302 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources [80.6 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [44.4 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,396 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources [2,933 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages [216 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [3,048 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages [174 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,946 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages [215 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages [3,067 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages [175 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,097 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US  
Fetched 1,410 kB in 14s (98.3 kB/s)                                            
W: Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/jonls/redshift-ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by vadertater on 2013-03-20
```
nate@nate-Satellite-C855:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libperl5.14 perl perl-base perl-modules
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 9,319 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main perl amd64 5.14.2-13ubuntu0.2 [4,422 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main libperl5.14 amd64 5.14.2-13ubuntu0.2 [1,226 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main perl-base amd64 5.14.2-13ubuntu0.2 [1,503 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main perl-modules all 5.14.2-13ubuntu0.2 [3,392 kB]
Fetched 9,319 kB in 4s (2,117 kB/s)       
(Reading database ... 177454 files and directories currently installed.)
Preparing to replace perl 5.14.2-13ubuntu0.1 (using .../perl_5.14.2-13ubuntu0.2_amd64.deb) ...
Unpacking replacement perl ...
Preparing to replace libperl5.14 5.14.2-13ubuntu0.1 (using .../libperl5.14_5.14.2-13ubuntu0.2_amd64.deb) ...
Unpacking replacement libperl5.14 ...
Preparing to replace perl-base 5.14.2-13ubuntu0.1 (using .../perl-base_5.14.2-13ubuntu0.2_amd64.deb) ...
Unpacking replacement perl-base ...
Processing triggers for man-db ...
Setting up perl-base (5.14.2-13ubuntu0.2) ...
(Reading database ... 177454 files and directories currently installed.)
Preparing to replace perl-modules 5.14.2-13ubuntu0.1 (using .../perl-modules_5.14.2-13ubuntu0.2_all.deb) ...
Unpacking replacement perl-modules ...
Setting up libperl5.14 (5.14.2-13ubuntu0.2) ...
Setting up perl-modules (5.14.2-13ubuntu0.2) ...
Setting up perl (5.14.2-13ubuntu0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

### Post by vadertater on 2013-03-20
nate@nate-Satellite-C855:~$ cat /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)]/ quantal main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-backports main restricted universe multiverse

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
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
```

---

### Post by vadertater on 2013-03-20
```

nate@nate-Satellite-C855:~$ ls -la /etc/apt/sources.list.d/
total 40
drwxr-xr-x 2 root root 4096 Mar 13 09:50 .
drwxr-xr-x 6 root root 4096 Mar 19 05:03 ..
-rw-r--r-- 1 root root  134 Mar 13 09:50 atareao-atareao-quantal.list
-rw-r--r-- 1 root root  134 Mar 13 09:50 atareao-atareao-quantal.list.save
-rw-r--r-- 1 root root  140 Mar 13 09:50 gnome3-team-gnome3-quantal.list
-rw-r--r-- 1 root root  140 Mar 13 09:50 jonls-redshift-ppa-quantal.list
-rw-r--r-- 1 root root  140 Mar 13 09:50 jonls-redshift-ppa-quantal.list.save
-rw-r--r-- 1 root root  154 Mar 13 09:50 kevin-mehall-pithos-daily-quantal.list
-rw-r--r-- 1 root root  154 Mar 13 09:50 kevin-mehall-pithos-daily-quantal.list.save
-rw-r--r-- 1 root root    0 Mar 11 19:25 kilian-f_lux-quantal.list
-rw-r--r-- 1 root root   66 Mar 11 19:25 kilian-f_lux-quantal.list.save
```

---

### Post by vadertater on 2013-03-20
Thanks for adding those explanations for the inputs! I appreciate it tons!!

---

### Post by Bashing-om on 2013-03-20
vadertater;
 Making progress.
in /etc/apt/sources.list 
> deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free is added to the wrong file; s/b in the list.d directory.
See here for how to correctly install spotify:
[http://www.ubuntuupdates.org/ppa/spotify](http://www.ubuntuupdates.org/ppa/spotify)

So in your favorite text editor, make a backup of the current sources.list file and edit out that offending line.

I am moving on to the list.d directory and see if I can determine the out-of-service PPAs.

I be back with more info.

---

### Post by Bashing-om on 2013-03-20
vadertater;
sourceslist.d -> redshift. As far as I can tell support for redshift ended with the natty version.
You can go into ubuntu software center and click on edit/software sources.  Go to other software and unclick the software source that is causing the error(redshift).

Still got to look at "main AMD64 and 1386 packages"/// -> then run the apt-gets again for current status.
[INDENT=2]I'll be back

[/INDENT]

---

### Post by vadertater on 2013-03-21
Thanks for you help! I turned off redshift. I have some other questions about this... how did you see these errors? Because I don't see where it says they are saved in the wrong file or any specific mention of these errors. My only experience with programming is MATLAB and it tells you where the error occurs... so how do you tell what is the specific problem from just my postings?


And...
> **Bashing-om said:**
> 

So in your favorite text editor, make a backup of the current sources.list file and edit out that offending line.



What does this mean? where do I find this text? do I have to change directory to sources.list, find the spotify repository, save the offending text (from spotify) and back it up and then it should be debugged?

---

### Post by vadertater on 2013-03-21
Nevermind, I found sources.list. I created a back up for it and I just need to delete the following line: deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free and then save it again????

---

### Post by Bashing-om on 2013-03-21
vadertater;

For your editing, you are correct in your procedure.
As to recognizing the fault with "spotify" that was only being aware of the proper form for any line in the sources.list file, and a bit of googleing.
  
Still stuck on determining where the  "main AMD64 and 1386 packages" seek is originating from. As a means of last resort, will see if the origination is not also in the 3rd party PPAs.//-> redshift ppa the originator ?
Let's see what the status is now: again post the output of terminal codes:
```
sudo apt-get update
sudo apt-get upgrade
```[INDENT=2]
still think'n
[/INDENT]

---

### Post by vadertater on 2013-03-22
```
nate@nate-Satellite-C855:~$ sudo apt-get update
[sudo] password for nate: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                           
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]            
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg [933 B]         
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg [72 B]                      
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg [933 B]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://repository.spotify.com](http://repository.spotify.com) stable Release                               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [36.8 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release [49.6 kB]         
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [15.4 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [692 B]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages [99.8 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted amd64 Packages             
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages [14 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe amd64 Packages               
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages [44.2 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages [1,150 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [99.3 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                       
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [44.8 kB]
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,396 B]
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources [83.5 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources [1,302 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources [80.6 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources [2,933 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main amd64 Packages [217 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted amd64 Packages [3,048 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe amd64 Packages [174 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse amd64 Packages [7,946 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages [216 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages [3,067 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages [175 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages [8,097 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources [14 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources [14 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources [8,529 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources [781 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main amd64 Packages [14 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted amd64 Packages [14 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe amd64 Packages [12.0 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse amd64 Packages [1,118 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages [14 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages [14 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages [12.8 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages [1,118 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US  
Fetched 1,503 kB in 11s (125 kB/s)                                             
Reading package lists... Done
```

---

### Post by vadertater on 2013-03-22
```
nate@nate-Satellite-C855:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libufe-xidgetter0 xul-ext-unity
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 53.3 kB of archives.
After this operation, 90.1 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main xul-ext-unity all 2.4.4-0ubuntu0.1 [48.4 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal-updates/main libufe-xidgetter0 amd64 2.4.4-0ubuntu0.1 [4,934 B]
Fetched 53.3 kB in 0s (127 kB/s)             
(Reading database ... 177492 files and directories currently installed.)
Preparing to replace xul-ext-unity 2.4.1-0ubuntu1.2 (using .../xul-ext-unity_2.4.4-0ubuntu0.1_all.deb) ...
Unpacking replacement xul-ext-unity ...
Preparing to replace libufe-xidgetter0 2.4.1-0ubuntu1.2 (using .../libufe-xidgetter0_2.4.4-0ubuntu0.1_amd64.deb) ...
Unpacking replacement libufe-xidgetter0 ...
Setting up libufe-xidgetter0 (2.4.4-0ubuntu0.1) ...
Setting up xul-ext-unity (2.4.4-0ubuntu0.1) ...
Please restart all running instances of firefox, or you will experience problems.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

### Post by vadertater on 2013-03-22
Thanks for explaining that! That makes sense. 

Here's what I've recently done/recent status: I went ahead and got rid of the line on sources.list. I uninstalled redshift (it wasn't working anyway) and I'm stilling having these issues. I even reinstalled spotify as that link specified. I have noticed that if I don't use spotify, the errors aren't as frequent.

---

### Post by Bashing-om on 2013-03-22
vadertater; 

All looks good at this time. (your last post of "apt-get upgrade complete ?). What are the current errors you are experiencing ?[INDENT=3]we be look'n

[/INDENT]

---

### Post by vadertater on 2013-03-22
Oh crap... I must have deleted a bit off the end because I also copied this bit "nate@nate-Satellite-C855:~$" when I posted the output. 

It's just the same errors... it's not freezing or anything anymore, but occasionally an error message or GPU hang up pops up. It's definitely not as frequent as before. 

I'll keep my eye out for patterns of when it occurs. And if it's still an issue I'll just come back running for help.

Thanks a ton, Bashing-om! You helped a lot - and I learned some stuff too!

---

### Post by DuckHook on 2013-03-22
> **vadertater said:**
> ...I uninstalled redshift (it wasn't working anyway) and I'm stilling having these issues...

...odd. Redshift works for me (Ubuntu 12.04) quite well. But if causing you issues, then no big loss.

---

### Post by Bashing-om on 2013-03-22
vadertater;

Someone is here always to offer assistance. Posting all errors generated will be of the greatest help in making any assessments. As well as background info: I did a and b and c, I expected x and y is what happened kind of thing.
[INDENT=4]
logic defines

[/INDENT]

---

### Post by matt_symes on 2013-03-22
Hi

@OP. Please try to use code tags around text copied and pasted from the terminal.

It is much more readable.

@bashing-om

```
matthew-S206:/proc/8935/fd % apt-cache search redshift
gtk-redshift - Adjusts the color temperature of your screen with GTK+ integration
redshift - Adjusts the color temperature of your screen
matthew-S206:/proc/8935/fd % 
```

... and i don't have that red shift ppa

```
matthew-S206:/proc/8935/fd % grep -ir redshift /etc/apt/sources.list{,.d/}
matthew-S206:/proc/8935/fd %
```

 so maybe the OP could install it fro the default repos if they really want it ?

Kind regards

---

### Post by Bashing-om on 2013-03-22
@ Matt, Thanks heaps,
@ 		vadertater; Your attention is directed to the above post. Installing from the repositories is always preferred over any other install method ; easier to maintain and better integration into the operating system as the code is optimized for specific operating systems.

"ppa-purge" required to remove the current ppa "red shift" package. If guidance needed, holler !
[INDENT=3]
my regards 

[/INDENT]

---

### Post by vadertater on 2013-03-25
Ok, I've tried to see if I recognized any patterns for when the errors are coming up... it's been a bit tough, but I think whenever I use any music player (pithos or spotify), I get the GPU Hang-ups, ubuntu errors from apport, etc. I noticed it once after downloading a word document, I also sometime get it as soon as I reboot (set up to skip log-in, so it happens immideatelywhen ubuntu starts). It has done it before when I am using lots (5) tabs on firefox. I haven't updated or anything since the last time we tinkered with it and I haven't downloaded anything. I uninstalled a few programs I don't use like hedgewars and weather app. But I haven't added anything else cause I want to fix what I have right now.

So... with that... I have read the post from matt_symes and I do not understand completely. I understand that installing to the repositories is better (I don't understand why), but what did I do? I installed a PPA? Is there some kind of article you could point me to to explain this in better detail? 


So for now, I'm going to look up how to purge my ppa and get rid of redshift and spotify (I don't like them anyway...) and then I'll let you know what I find and see if it's correct.


And I will use code tags this time!

---

### Post by Bashing-om on 2013-03-25
vadertater;
Still hang'n with you. Your last makes me wonder //how much ram do you have onboard ?

In any event, I'll be back soon as I catch up.[INDENT=6]look'n and think'n

[/INDENT]

---

### Post by Bashing-om on 2013-03-25
vadertater;

The first in order remains insuring the package manager is happy, then determine IF any installed packages have problems.
When we are assured of the packages'  stability and there are still problems, I have in mind a test to narrow things down a bit more.

For now it is back to the basics, apt-get and the errors that the package management system relays to us.
Once again (with feeling):
```
sudo apt-get update
sudo apt-get upgrade
``` Is everybody happy ?
And the ram situation, got enough to run fat ubuntu ?[INDENT=3]
we be strok'n

[/INDENT]

---

### Post by vadertater on 2013-03-25
```
nate@nate-Satellite-C855:~$ sudo apt-get update
[sudo] password for nate: 
Hit http://us.archive.ubuntu.com quantal Release.gpg
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]
Get:2 http://us.archive.ubuntu.com quantal-updates Release.gpg [933 B]         
Get:3 http://security.ubuntu.com quantal-security Release [49.6 kB]            
Hit http://archive.canonical.com quantal Release.gpg                           
Hit http://ppa.launchpad.net quantal Release.gpg                               
Get:4 http://extras.ubuntu.com quantal Release.gpg [72 B]                      
Hit http://us.archive.ubuntu.com quantal-backports Release.gpg                 
Hit http://us.archive.ubuntu.com quantal Release                               
Hit http://archive.canonical.com quantal Release                               
Hit http://extras.ubuntu.com quantal Release                                   
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://repository.spotify.com stable Release.gpg                           
Get:5 http://us.archive.ubuntu.com quantal-updates Release [49.6 kB]           
Hit http://ppa.launchpad.net quantal Release.gpg                               
Hit http://repository.spotify.com stable Release                               
Get:6 http://security.ubuntu.com quantal-security/main Sources [37.4 kB]       
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://archive.canonical.com quantal/partner amd64 Packages                
Hit http://us.archive.ubuntu.com quantal-backports Release                     
Hit http://extras.ubuntu.com quantal/main Sources                              
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Get:7 http://security.ubuntu.com quantal-security/restricted Sources [14 B]    
Hit http://us.archive.ubuntu.com quantal/main Sources                          
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://archive.canonical.com quantal/partner i386 Packages                 
Hit http://extras.ubuntu.com quantal/main amd64 Packages                       
Get:8 http://security.ubuntu.com quantal-security/universe Sources [15.4 kB]   
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://us.archive.ubuntu.com quantal/restricted Sources                    
Get:9 http://security.ubuntu.com quantal-security/multiverse Sources [692 B]   
Hit http://us.archive.ubuntu.com quantal/universe Sources                      
Hit http://ppa.launchpad.net quantal Release                                   
Hit http://extras.ubuntu.com quantal/main i386 Packages                        
Get:10 http://security.ubuntu.com quantal-security/main amd64 Packages [101 kB]
Hit http://us.archive.ubuntu.com quantal/multiverse Sources                    
Hit http://us.archive.ubuntu.com quantal/main amd64 Packages                   
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://us.archive.ubuntu.com quantal/restricted amd64 Packages             
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Hit http://us.archive.ubuntu.com quantal/universe amd64 Packages               
Hit http://us.archive.ubuntu.com quantal/multiverse amd64 Packages             
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Get:11 http://security.ubuntu.com quantal-security/restricted amd64 Packages [14 B]
Hit http://us.archive.ubuntu.com quantal/main i386 Packages                    
Get:12 http://security.ubuntu.com quantal-security/universe amd64 Packages [44.2 kB]
Hit http://us.archive.ubuntu.com quantal/restricted i386 Packages              
Get:13 http://security.ubuntu.com quantal-security/multiverse amd64 Packages [1,150 B]
Get:14 http://security.ubuntu.com quantal-security/main i386 Packages [100 kB] 
Hit http://us.archive.ubuntu.com quantal/universe i386 Packages                
Hit http://us.archive.ubuntu.com quantal/multiverse i386 Packages              
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://us.archive.ubuntu.com quantal/main Translation-en                   
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Get:15 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]
Get:16 http://security.ubuntu.com quantal-security/universe i386 Packages [44.8 kB]
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Hit http://us.archive.ubuntu.com quantal/multiverse Translation-en             
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Ign http://archive.canonical.com quantal/partner Translation-en_US             
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://us.archive.ubuntu.com quantal/restricted Translation-en             
Ign http://archive.canonical.com quantal/partner Translation-en                
Ign http://extras.ubuntu.com quantal/main Translation-en_US                    
Get:17 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,396 B]
Ign http://extras.ubuntu.com quantal/main Translation-en                       
Hit http://us.archive.ubuntu.com quantal/universe Translation-en               
Get:18 http://security.ubuntu.com quantal-security/main Translation-en [53.9 kB]
Get:19 http://us.archive.ubuntu.com quantal-updates/main Sources [84.0 kB]     
Hit http://ppa.launchpad.net quantal/main Sources                              
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en      
Hit http://ppa.launchpad.net quantal/main amd64 Packages                       
Get:20 http://us.archive.ubuntu.com quantal-updates/restricted Sources [1,302 B]
Hit http://security.ubuntu.com quantal-security/restricted Translation-en      
Get:21 http://us.archive.ubuntu.com quantal-updates/universe Sources [80.6 kB]
Hit http://ppa.launchpad.net quantal/main i386 Packages                        
Hit http://security.ubuntu.com quantal-security/universe Translation-en        
Get:22 http://us.archive.ubuntu.com quantal-updates/multiverse Sources [2,933 B]
Get:23 http://us.archive.ubuntu.com quantal-updates/main amd64 Packages [218 kB]
Get:24 http://us.archive.ubuntu.com quantal-updates/restricted amd64 Packages [3,048 B]
Get:25 http://us.archive.ubuntu.com quantal-updates/universe amd64 Packages [174 kB]
Ign http://security.ubuntu.com quantal-security/main Translation-en_US         
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Get:26 http://us.archive.ubuntu.com quantal-updates/multiverse amd64 Packages [7,946 B]
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US   
Get:27 http://us.archive.ubuntu.com quantal-updates/main i386 Packages [216 kB]
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US     
Get:28 http://us.archive.ubuntu.com quantal-updates/restricted i386 Packages [3,067 B]
Get:29 http://us.archive.ubuntu.com quantal-updates/universe i386 Packages [175 kB]
Get:30 http://us.archive.ubuntu.com quantal-updates/multiverse i386 Packages [8,097 B]
Get:31 http://us.archive.ubuntu.com quantal-updates/main Translation-en [105 kB]
Hit http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en    
Hit http://us.archive.ubuntu.com quantal-updates/restricted Translation-en
Get:32 http://us.archive.ubuntu.com quantal-updates/universe Translation-en [93.4 kB]
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://us.archive.ubuntu.com quantal-backports/main Sources                
Hit http://us.archive.ubuntu.com quantal-backports/restricted Sources          
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Hit http://us.archive.ubuntu.com quantal-backports/universe Sources            
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Sources          
Ign http://ppa.launchpad.net quantal/main Translation-en_US                    
Hit http://us.archive.ubuntu.com quantal-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages   
Ign http://ppa.launchpad.net quantal/main Translation-en                       
Hit http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com quantal-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com quantal-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com quantal-backports/main Translation-en         
Hit http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com quantal-backports/universe Translation-en     
Ign http://us.archive.ubuntu.com quantal/main Translation-en_US                
Ign http://us.archive.ubuntu.com quantal/multiverse Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/restricted Translation-en_US          
Ign http://us.archive.ubuntu.com quantal/universe Translation-en_US            
Ign http://us.archive.ubuntu.com quantal-updates/main Translation-en_US        
Ign http://us.archive.ubuntu.com quantal-updates/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com quantal-updates/universe Translation-en_US    
Ign http://us.archive.ubuntu.com quantal-backports/main Translation-en_US      
Ign http://us.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com quantal-backports/universe Translation-en_US  
Fetched 1,674 kB in 12s (134 kB/s)                                             
Reading package lists... Done

```


```
nate@nate-Satellite-C855:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gir1.2-goa-1.0 gnome-online-accounts libgoa-1.0-0 libgoa-1.0-common
  libssl1.0.0 libssl1.0.0:i386 openssl
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,813 kB of archives.
After this operation, 18.4 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main libssl1.0.0 i386 1.0.1c-3ubuntu2.3 [1,006 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main libssl1.0.0 amd64 1.0.1c-3ubuntu2.3 [1,020 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main gnome-online-accounts amd64 3.6.0-0ubuntu1.1 [97.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main libgoa-1.0-0 amd64 3.6.0-0ubuntu1.1 [150 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main libgoa-1.0-common all 3.6.0-0ubuntu1.1 [4,732 B]
Get:6 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main openssl amd64 1.0.1c-3ubuntu2.3 [525 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main gir1.2-goa-1.0 amd64 3.6.0-0ubuntu1.1 [11.3 kB]
Fetched 2,813 kB in 2s (1,181 kB/s)        
Preconfiguring packages ...
(Reading database ... 175108 files and directories currently installed.)
Preparing to replace libssl1.0.0:i386 1.0.1c-3ubuntu2.2 (using .../libssl1.0.0_1.0.1c-3ubuntu2.3_i386.deb) ...
De-configuring libssl1.0.0:amd64 ...
Unpacking replacement libssl1.0.0:i386 ...
Preparing to replace libssl1.0.0:amd64 1.0.1c-3ubuntu2.2 (using .../libssl1.0.0_1.0.1c-3ubuntu2.3_amd64.deb) ...
Unpacking replacement libssl1.0.0:amd64 ...
Setting up libssl1.0.0:i386 (1.0.1c-3ubuntu2.3) ...
Setting up libssl1.0.0:amd64 (1.0.1c-3ubuntu2.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 175108 files and directories currently installed.)
Preparing to replace gnome-online-accounts 3.6.0-0ubuntu1 (using .../gnome-online-accounts_3.6.0-0ubuntu1.1_amd64.deb) ...
Unpacking replacement gnome-online-accounts ...
Preparing to replace libgoa-1.0-0:amd64 3.6.0-0ubuntu1 (using .../libgoa-1.0-0_3.6.0-0ubuntu1.1_amd64.deb) ...
Unpacking replacement libgoa-1.0-0:amd64 ...
Preparing to replace libgoa-1.0-common 3.6.0-0ubuntu1 (using .../libgoa-1.0-common_3.6.0-0ubuntu1.1_all.deb) ...
Unpacking replacement libgoa-1.0-common ...
Preparing to replace openssl 1.0.1c-3ubuntu2.2 (using .../openssl_1.0.1c-3ubuntu2.3_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace gir1.2-goa-1.0 3.6.0-0ubuntu1 (using .../gir1.2-goa-1.0_3.6.0-0ubuntu1.1_amd64.deb) ...
Unpacking replacement gir1.2-goa-1.0 ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Setting up libgoa-1.0-common (3.6.0-0ubuntu1.1) ...
Setting up libgoa-1.0-0:amd64 (3.6.0-0ubuntu1.1) ...
Setting up gnome-online-accounts (3.6.0-0ubuntu1.1) ...
Setting up openssl (1.0.1c-3ubuntu2.3) ...
Setting up gir1.2-goa-1.0 (3.6.0-0ubuntu1.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

And I have 3.8 GB RAM available.

---

### Post by matt_symes on 2013-03-26
Hi

> So... with that... I have read the post from matt_symes and I do not  understand completely. I understand that installing to the repositories  is better (I don't understand why), but what did I do? I installed a  PPA? Is there some kind of article you could point me to to explain this  in better detail?

The program, redshift, is available in  the main repositories and is not available in the PPA you added for the release version of Ubuntu you are using.

Because it's in the main repos, you can just install it using 

```
sudo apt-get install redshift
```

As for your GPU hang ups, information about your graphics card would be useful here to see if it is a known problem.

From the terminal, please post the output of

```
lspci -nnk | grep -iA3 vga
```

(captial A above). It may also be useful to look in your log files.

```
sudo apt-get install pastebinit
```

```
cat /var/log/Xorg.0.log | pastebinit
```

Copy and paste the URL from the last command into your next post.

Kind regards

---

### Post by Bashing-om on 2013-03-26
vadertater;

Looking good ! Moving on // Your attention is invited to Matt's advise; Comply and the situation should be well in hand shortly.

Off Topic: PPA == Personal Package Archive: Wonderful thing, someone did some beautiful coding that may or may not integrate well into ubuntu's kernel, particularly when the kernel is updated (changes). Case in point is "redshift"; that is now accepted into the standard repositories - quite an accomplishment ! Means in essence it has passed  extensive testing and is under ubuntu's umbrella . Lot's more can be said, will fill a big book.[INDENT=3]
ubuntu - all for one and one for all

[/INDENT]

---

### Post by vadertater on 2013-03-26
Ok, thanks for the explanation Bashing-om. I'll make sure to stay on topic next time... I just have some many questions!

So I'll post the output to those, but I think the Google Calendar indicator is also not compatible. It is 3rd-party and I clicked show details for the error message, and it indicated it had to do with google calendar.

```
nate@nate-Satellite-C855:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:fb20]
    Kernel driver in use: i915
    Kernel modules: i915
```

When I put in:
```
sudo apt-get install pastebinit
```
It told me some of the packages could not be verfified... so should I just install the whole thing? what is it that I'm installing... gonna read over it first.

---

### Post by vadertater on 2013-03-26
Here is the URL you wanted: no such file or directory.

---

### Post by vadertater on 2013-03-26
I'm on top of things today!

It looks like apport... /usr/share/apport/apptor-gpu-error-intel.py keeps occuring. And whenever this happens, the GPU hang-up comes right after. 

I'm also getting something as mentioned in this article: [http://blog.mattrudge.net/2012/12/13/system-program-problem-detected-on-ubuntu-12-10/](http://blog.mattrudge.net/2012/12/13/system-program-problem-detected-on-ubuntu-12-10/) and he mentions something from apport being the issue.

Thoughts?

---

### Post by Bashing-om on 2013-03-26
vadertater; Hey 

Getting to the bottom of things. 
I am aware that there exist the bug with "apptor-gpu-error-intel.py" however, this is my first encounter with it and I am more than willing to have Matt's input to all of this.[INDENT=3]resuming -momentarily- my back seat

[/INDENT]

---

### Post by matt_symes on 2013-03-26
Hi

Sorry typo. Should have been a capital X

```
cat /var/log/Xorg.0.log | pastebinit
```

Blasted keyboard ;)

Post the URL for that. I'll amend my last post.

EDIT:

You're not the only one getting this error by the looks of it.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1135473](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1135473)

How often are you getting the GPU hang error ?

EDIT2:

And another... (This is an old one though)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/754777](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/754777)

EDIT3:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1159536](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1159536)

Post #6 suggests updating the kernel
> 
I did an update to Kernel 3.8.4-030804-generic.
I get the error message only once and then everthing works fine for me.



That may be worth a try and it's a simple fix if it works for you.

Kind regards

---

### Post by vadertater on 2013-03-26
Sweet! I'll read though those threads. Here is the URL as requested [http://paste.ubuntu.com/5650582/](http://paste.ubuntu.com/5650582/)

---

### Post by matt_symes on 2013-03-26
HI

> Here is the URL as requested .....

Nothing really in that log. It may be worth while looking at syslog.

```
grep -m1 -iC5 "hangcheck" /var/log/syslog
```

Captial C above. Copy and paste into your next post. No need for pastebin really here.

This is just to check to see what is going on.

Kind regards

---

### Post by vadertater on 2013-03-27
I upgraded my kernel using this: [http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/](http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/)

Then I rebooted and I am now having issues connecting to the internet via wireless (always a problem) and wired connection... I'm looking at this thread currently [http://ubuntuforums.org/showthread.php?t=2075692&page=2](http://ubuntuforums.org/showthread.php?t=2075692&page=2), so I'll get back to you later tonight. 

I haven't gotten any error messages yet... fingers crossed!

---

### Post by matt_symes on 2013-03-27
Hi

> **vadertater said:**
> I upgraded my kernel using this: [http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/](http://www.liberiangeek.net/2013/03/linux-kernel-3-8-1-releasedhow-to-install-upgrade-in-ubuntu-12-10/)

Then I rebooted and I am now having issues connecting to the internet via wireless (always a problem) and wired connection... I'm looking at this thread currently [http://ubuntuforums.org/showthread.php?t=2075692&page=2](http://ubuntuforums.org/showthread.php?t=2075692&page=2), so I'll get back to you later tonight. 

I haven't gotten any error messages yet... fingers crossed!

Any wired/wireless problems should be easier to fix than random GPU hangups.

Post back on how you get on.

You may also want to pin your kernel so a kernel update will not revert to an older kernel that is giving the same GPU hangup issues.

Kind regards

---

### Post by vadertater on 2013-03-27
I'll look up how to pin the kernel.

and guess what... My wireless is working... how crazy. So if wireless continues to be an issue, I'll post another thread. Here is the output you wanted:

 ```
nate@nate-Satellite-C855:~$ grep -m1 -iC5 "hangcheck" /var/log/syslog
Mar 26 13:12:57 nate-Satellite-C855 AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/2e8d536157ef4c62a395b73669b59bc3
Mar 26 13:12:58 nate-Satellite-C855 AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String('synaptic')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Mar 26 13:17:01 nate-Satellite-C855 CRON[2404]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 26 13:18:27 nate-Satellite-C855 AptDaemon: INFO: Quitting due to inactivity
Mar 26 13:18:27 nate-Satellite-C855 AptDaemon: INFO: Quitting was requested
Mar 26 13:28:31 nate-Satellite-C855 kernel: [ 1605.104090] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 26 13:28:31 nate-Satellite-C855 kernel: [ 1605.104096] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
Mar 26 13:28:31 nate-Satellite-C855 kernel: [ 1605.107234] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
Mar 26 13:35:19 nate-Satellite-C855 kernel: [ 2012.718545] alx 0000:01:00.0: eth0: NIC Link Down
Mar 26 13:35:19 nate-Satellite-C855 NetworkManager[792]: <info> (eth0): carrier now OFF (device state 100, deferring action for 4 seconds)
Mar 26 13:35:24 nate-Satellite-C855 NetworkManager[792]: <info> (eth0): device state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]

```

What did ```
grep -m1 -iC5 "hangcheck" /var/log/syslog
``` do? Just check the /var/log/syslog file? And pastebin was just to reduce the room of the huge output??

---

### Post by vadertater on 2013-03-27
I can't find anything on pinning the kernel. Could you run me through how to do this, please?

---

### Post by schragge on 2013-03-27
See [uhelp]community/AptGet/Howto#Maintenance_commands[/uhelp], specifically #9. Basically, what you might need is
```
echo linux-image-`uname -r` hold|sudo dpkg --set-selections
``` You can manage it from [synaptic](http://manpages.ubuntu.com/manpages/precise/en/man8/synaptic.8.html), too.

Please don't confuse it with [APT pinning]("http://wiki.debian.org/AptPreferences") which is also described at [uhelp]community/PinningHowto[/uhelp]: it's a completely different beast and is usually used when mixing packages from several releases.

---

### Post by matt_symes on 2013-03-27
Hi

I'm glad that your wireless is working :)

> What did 
          
```
grep -m1 -iC5 "hangcheck" /var/log/syslog
``` 

do? Just check the /var/log/syslog file? And pastebin was just to reduce the room of the huge output??



That above command will grep the file /var/log/syslog looking for the word hangcheck. 

When it find the first match (-m 1) it will print that line and 5 lines before and 5 lines after (-C5).

I just wanted to check the error you getting and the surrounding lines. 

The reason why i said to not bother with pastebin is because it will only print a small number of lines (11 in this case) and they would have been easy to copy and paste into a post.

To pin your kernel look at 

```
sudo apt-mark hold linux-image
```

or 

```
sudo apt-get remove linux-image
```

They should both stop automatic kernel updates.

**EDIT:**

Beaten to it by schragge :) That'll teach me to start a post and get a coffee midway.

The method he points out will work as well and, in-fact, *apt-mark hold* is just a wrapper around dpkg --set-selections. You can see this in the man pages.

Good call schragge. Nice link as well.

Kind regards

---

### Post by schragge on 2013-03-27
Your solution is better, Matt. Long commands connected through pipes look rather intimidating to new users, and we are in the Absolute Beginners Section. But I've got a question, too. Locking *linux-image* at the current version would undoubtedly work in *precise* as this package has versioned dependencies there. The OP however is using *quantal*, and from what i see [here]("http://packages.ubuntu.com/quantal-updates/linux-image"), it seems that locking *linux-image* won't prevent newer versions of *linux-image-generic* from being installed. Perhaps [linux-image-generic]("http://packages.ubuntu.com/quantal-updates/linux-image-generic")  should be locked instead?

---

### Post by matt_symes on 2013-03-27
Hi

> **schragge said:**
> Your solution is better, Matt. Long commands connected through pipes look rather intimidating to new users, and we are in the Absolute Beginners Section. But I've got a question, too. Locking *linux-image* at the current version would undobtedly work in *precise* as this package has versioned dependencies there. The OP however is using *quantal*, and from what i see [here]("http://packages.ubuntu.com/quantal-updates/linux-image"), it seems that locking *linux-image* won't prevent newer versions of *linux-image-generic* from being installed. Perhaps [linux-image-generic]("http://packages.ubuntu.com/quantal-updates/linux-image-generic")  should be locked instead?

I think you are right schragge. Good catch ! It's been a good while since i pinned a kernel.

@OP. Lock linux-image-generic.

Kind regards

---

### Post by vadertater on 2013-03-28
Thanks matt and schragge! 

I ended up using matt's method because schragge's gave me an error. I really appreciate all the help from you and thank you Bashing-om! I learned a lot from all of your help!

How do I mark this as solved? And my wifi/wired connection is still acting up... should we solve that hear or should I make a different thread since it's a different issue?

---

### Post by Bashing-om on 2013-03-28
vadertater;

Appreciate your including me in the thanks, to be honest, I did little but learn some too.
Yes, A different issue == another thread.
And the interim method to mark as solved:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=2]
enjoyed working with all

[/INDENT]

---

### Post by vadertater on 2013-03-28
Ok, I lied... just got another error message from usr/share/apport/apportcheckresume just occured when I logged in after a short hibernation. I also got a message about how I need to file a bug report with bugzilla since the new kernel is not a standard linux kernel, the message made me click out before I could just copy and paste it. I'll try to get a more accurate description for the error soon

---

### Post by matt_symes on 2013-03-28
Hi

That sounds like a different issue than the GPU hang issue. 

Have you had any GPU hangs since installing the new kernel ?

Kind regards

---

### Post by vadertater on 2013-03-28
No GPU hangs. My friend recommended I just turn off apport by going into the text and setting enable=0 instead of 1

---

### Post by matt_symes on 2013-03-29
Hi

Your friends suggestion would disable apport and you would not see the error message.

You'll need to edit the file

```
/etc/default/apport
```

and the run the update-initramfs command (IIRC).

If your interested in getting to the root cause of the problem though then post back any error message when it happens again.

Keep an eye on the log file...

```
/var/log/syslog
```

Kind regards

---

### Post by vadertater on 2013-03-29
I'll post back when it pops up again. May be a while... this error doesn't seem to occur as frequently as the last ones.

---

### Post by baldy al on 2013-03-29
Thanks very much to matt_symes for pointing me to this thread and to all participants. Yes I do have in-built intel sandybridge x86/MMX/SSE2. The messages here were a little daunting to start with but I have stuck with it. I used the [http://www.liberiangeek.net/2013/03/...-ubuntu-12-10](http://www.liberiangeek.net/2013/03/...-ubuntu-12-10) link in this thread. I have had no problems since (only an hour or so ago though!:))

Thank you all very much. Keep up the good work guys :KS

---

### Post by CamPsych on 2013-03-29
Hey all. 

I have been having the same issue here, thanks to matt_symes on the Bugs thread and here for directing me. I have done the update and will see how I go, hopefully it fixes the problem. You guys are awesome.

---

### Post by CamPsych on 2013-03-30
Strange, I seem to be having wifi issues too now, have to write this from phone :/

---

### Post by matt_symes on 2013-03-30
Hi

@camPsych.

Are you still getting GPU hangs ?

Can you post the output of

```
sudo lshw -c network
```

and 

```
lspci -nnk | grep -iA3 wireless
```

(capital A above) so we can check your network card.

Kind regards

---

### Post by vadertater on 2013-03-30
Error time!

I get a little info tab that states: It appears you are currently running a mainline kernel. It would be better to report this but upstream at [http://bugzilla.kernel.org/](http://bugzilla.kernel.org/) so that the upstreamkernel developers are aware of the issue. If you'd still like to file a bug against the ubuntu kernel, please boot with an official Ubuntu kernel and re-file

Ubuntu Error is the following:
Executable Path: /usr/share/apport/apportcheckresume
Page: linux-image-3.8.1-030801-generic .....
Problem Type: KernelOops
Title: Suspend/resumefailure
Annotation: This occured during a previous suspend and prevented it from resuming properly (the error did occur on start up, so this makes sense)
ApportVersion: 2.6.1-0ubuntu10
Architecture: amd64

And the list continues... do you need ProcMaps, Proc Status or Sleep Log??? These are much larger blocks of info that cannot be copied and pasted...

---

### Post by matt_symes on 2013-03-30
Hi

Wait 10 minutes. I'm just going to read that guide you followed to update the kernel.

It seems you are not using a Ubuntu kernel.

**EDIT:**

I don't seem to able able to click on that link so i don't know where you got the kernel from.

Use one of the kernels from here 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

At least we know that updating the kernel seems to fix the GPU hang issues.

How is your wireless behaving ? Any other issues besides the resume issue ?

Kind regards

---

### Post by CamPsych on 2013-03-30
Hey guys,
 
Having issues with connectivity.. results below...
 
#cameron@cameron-Aspire-E1-531:~$ sudo lshw -c network
  *-network              
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:88:e3:c0:5f:f2
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.128 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:c0500000-c0503fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 08:3e:8e:4d:50:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.1-030801-generic firmware=N/A ip=192.168.0.5 link=yes multicast=yes wireless=IEEE 802.11bgn #
 
#cameron@cameron-Aspire-E1-531:~$ lspci -nnk | grep -iA3 wireless
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
            Subsystem: Foxconn International, Inc. Device [105b:e042]
            Kernel driver in use: bcma-pci-bridge
            Kernel modules: bcma #
 
Other issue is that I am getting a black screen on waking from sleep, HDD seems to make a noise as though to to start, but nothing, even if I wait. Have to do a hard reboot every time that it does this. No error messages are associated with this.

---

### Post by wildmanne39 on 2013-03-30
I have the same problem with a new laptop, where is the best place to get the upgraded kernel from? for 12.04 with directions for installing.
Thanks

---

### Post by CamPsych on 2013-03-31
Just to clarify...caught the screen in a different light and seems that the screen is completely darkened, can just see the desktop. Efforts to lighten screen fail. 

Just as a sidebar, how do I correctly post code?

---

### Post by wildmanne39 on 2013-03-31
Nevermind found and installed the new kernel.
Thanks

---

### Post by schragge on 2013-03-31
> **CamPsych said:**
> Just as a sidebar, how do I correctly post code?When you click on **Adv Reply**, you will see the **#** button on the toolbar above the text input area. It inserts [noparse][[/noparse]code][noparse][[/noparse]/code] tags around the selected text. You can wrap text in these tags by hand, too.

---

### Post by CamPsych on 2013-03-31
WIFI Issue is fixed, also posted a separate question on it, but ended up finding answer myself: 

*OK folks, after a lot of searching and trial and error, the best result that I found was at [https://help.ubuntu.com/community/Wi...x#Known_Issues]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Known_Issues").  I did this, wondered why it wouldn't work, but then realised at the  last moment that after the upgrade that I had put the password in  incorrectly...so all is working now. *

As per the advise on the known bug thread [http://ubuntuforums.org/showthread.php?t=2073060&page=7](http://ubuntuforums.org/showthread.php?t=2073060&page=7) I also added the PPAs x-swat and ppa glasen/intel-drivers and it seems that I have had no hangs now for the last 12 hours at least. Not sure on the black screen though, will report back.

---

### Post by vadertater on 2013-03-31
> **matt_symes said:**
> 

Use one of the kernels from here 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

At least we know that updating the kernel seems to fix the GPU hang issues.

How is your wireless behaving ? Any other issues besides the resume issue ?

Kind regards

So how do I use one of those kernels? Just follow the same guide and use the filename from those guys instead of the file name they gave me in the article?

And my wireless is a bit crazy. I constantly have to switch between the different networks on campus and my ethernet connection is not being recognized. Those are the big issues. No other one's so far...

---

### Post by Slixt on 2013-03-31
Hello, I also have been having issues with this. I followed the steps all the way up to installing the wrong kernal. I think it's an older kernel? 3.8.1?
So, I'm with vader on this, not sure exactly how to go about it. It was using wget in his link and downloaded 4 files.  2 linux-headers-3.8.1, and 2 of the linux-image-extra-3.8.1. I assume when I click your link, I'll need to download both of each of those file sets for the latest kernel?  I haven't had any of these annoying hangs since switching it.

---

### Post by CamPsych on 2013-03-31
Which kernel did you install? I did the librariangeek website one and it seems that I am going just fine atm.

---

### Post by Slixt on 2013-03-31
I installed the same one it worked fine for me too. I just wasn't sure if having an older or different kernel would somehow blindside me later with complications.

---

### Post by Slixt on 2013-03-31
I may have spoken too soon. Rebooted and was met with this all too familiar box stating the system detected an error.

---

### Post by Slixt on 2013-03-31
The result of **grep -m1 -iC5 "hangcheck" /var/log/syslog** for my system.

```
Mar 31 21:45:02 slixt-Satellite-L755 AptDaemon.PackageKit: INFO: Get updates()
Mar 31 21:45:03 slixt-Satellite-L755 AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/07820a4eed0a42f79fd580bd15a186c3
Mar 31 21:48:35 slixt-Satellite-L755 kernel: [  326.465433] type=1400 audit(1364780915.517:31): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=932 comm="cupsd" pid=932 comm="cupsd" capability=36  capname="block_suspend"
Mar 31 21:51:00 slixt-Satellite-L755 AptDaemon: INFO: Quitting due to inactivity
Mar 31 21:51:00 slixt-Satellite-L755 AptDaemon: INFO: Quitting was requested
Mar 31 22:07:42 slixt-Satellite-L755 kernel: [ 1473.134270] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung
Mar 31 22:07:42 slixt-Satellite-L755 kernel: [ 1473.134276] [drm] capturing error event; look for more information in /debug/dri/0/i915_error_state
Mar 31 22:07:42 slixt-Satellite-L755 kernel: [ 1473.454197] atl1c 0000:03:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 31 22:07:43 slixt-Satellite-L755 kernel: [ 1473.582153] atl1c 0000:03:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.
Mar 31 22:07:45 slixt-Satellite-L755 gnome-session[1679]: WARNING: App 'compiz.desktop' respawning too quickly
Mar 31 22:07:45 slixt-Satellite-L755 gnome-session[1679]: CRITICAL: We failed, but the fail whale is dead. Sorry....


```

EDIT: I'm also now finding the wireless issues. It drops wireless every 50 seconds it seems.

---

### Post by CamPsych on 2013-04-01
Hey again, 

@slixt - check out the above fix on the wifi, you may have some luck with that. That is if you have the same hardware...

@vadertater  - have you had any luck with the  new errors that you are getting, or  working out how to get that kernel working, I got the same 'non  authentic kernel' notice as well today. 

Other issue is failure to resume after closing the lid, are you guys having this issue? If so, do you know of any fix?

---

### Post by Slixt on 2013-04-01
Honestly, I just stripped out ubuntu for the billionth time and did what I could have to begin with. Reinstalled the 32bit version cause 64bit seemed to be acting weird from install anyways, and closed update manager. That's where all of the issues come from and from there I can look into which of the 362 updates were causing it. It works fine like this. So, probably no serious reason I absolutely must update and break it.

Edit: updated all but the kernel stuff. Seems to work fine, so I pinned the kernel as mentioned here before so that hopefully it can't be accidentally updated until i'm ready to with one that won't seem to break my wireless. Also, some of it seemed to be actually ubuntu's firefox extensions causing what looks like my wifi is goofing. It would hang a bit and take ages to load a page that takes 2 seconds and grey the window out. So, disabling them brought it back up to how it should be. Finally! Thanks for all the help you guys. :)

---

### Post by Marc1988 on 2013-04-03
Hey there,
I'm a absolute noob to Ubuntu, i've just played around with it the since 2 weeks... i faced the problem that both of my graphiccards (ATI 6490m and Intel HD 3000) were running at the same time. This resulted in ernomous overheating, so I decided to disable the ATI and run Ubuntu with the integrated one, what is ok, cause of battery saving and i wont use any intense graphics anyway. So now the laptop wont get hot anymore and the fans aren't going wild all the time. But now I receive these above mentioned apport errors, freezes, lacks, and so on.
can u please discribe the step by step moves what to do for a dummy like me.
I'm using Ubuntu 12.10 in an HP Probook 4530s.

thanks in advance+
Marc

Edit: another bug appeared after waking up from suspend the computer start but the screen keeps black. any suggestions?

---

