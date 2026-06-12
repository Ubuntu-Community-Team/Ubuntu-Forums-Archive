---
title: "Everytime i install/uninstall a package i get an error message &quot;Texlive-Pictures&quot;"
date: 2013-11-02
forum: New to Ubuntu
---

### Post by glynnd on 2013-11-02
Hi folks, complete noob to linux and ubuntu. just got fed up with the security (lack of) within windows so thought id try something new.
as the title says, i get an error message saying something along the lines of "inconsistent package in Texlive-Pictures", it first started when i updated my system from 13.04 to 13.10, at first it stopped me installing anymore packages, i tried updating and upgrading via terminal and a few other commands i saw on the forum from searches. now i can install apps ok but still get the error. more annoying than anything. if anyone wants to help this noobie out id be more than grateful

thanks,
Glynn

---

### Post by Bashing-om on 2013-11-02
glynnd; Hi Welcome to the forum.

Helping is what we do !
Post back - between code (#) tags - the output of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```

And we will pick up the ball and run.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by glynnd on 2013-11-02
Hi Bashing-om,
heres the outputs

#glynn@glynn-K50IJ:~$ sudo apt-get update[sudo] password for glynn: 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) raring InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring Release                                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates InRelease                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security InRelease                      
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed InRelease                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) raring/main Sources                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release.gpg                             
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release.gpg [933 B]           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy InRelease                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security Release.gpg                    
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy Release                                 
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed Release.gpg [933 B]          
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy Release                        
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg [72 B]               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                    
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates Release [49.6 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner amd64 Packages                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) saucy/partner i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main amd64 Packages                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports Release                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security Release                        
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed Release [49.6 kB]            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Sources                            
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en_GB               
Ign [http://archive.canonical.com](http://archive.canonical.com) saucy/partner Translation-en                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Sources             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_GB             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Get:6 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy InRelease [353 B]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Sources             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main amd64 Packages            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted amd64 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe amd64 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse amd64 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy InRelease
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main i386 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe i386 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en_GB
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en_GB
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/multiverse Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en_GB
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/restricted Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en_GB
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy Release
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy/universe Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main i386 Packages
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Sources [3,861 B]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Sources [18.3 kB]
Get:9 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB [375 B]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Sources [14 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main amd64 Packages
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Sources [14 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main i386 Packages
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main amd64 Packages [49.4 kB]
Get:13 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB [388 B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted amd64 Packages [14 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main amd64 Packages
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe amd64 Packages [18.1 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main i386 Packages
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse amd64 Packages [14 B]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main i386 Packages [49.1 kB]
Get:18 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB [381 B]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted i386 Packages [14 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main amd64 Packages
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe i386 Packages [18.1 kB]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main i386 Packages
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse i386 Packages [14 B]
Get:22 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB [373 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main amd64 Packages  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main i386 Packages
Get:23 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB [384 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/multiverse amd64 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/main i386 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/universe i386 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/multiverse i386 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/multiverse Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) saucy/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/universe Translation-en
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/multiverse Sources [14 B]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/restricted Sources [14 B]
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/main Sources [18.3 kB]
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/universe Sources [7,145 B]
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/multiverse amd64 Packages [14 B]
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/restricted amd64 Packages [14 B]
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/main amd64 Packages [38.2 kB]
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/universe amd64 Packages [26.3 kB]
Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/multiverse i386 Packages [14 B]
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/restricted i386 Packages [14 B]
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/main i386 Packages [37.7 kB]
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/universe i386 Packages [25.5 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-proposed/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) saucy-security/universe Translation-en_GB
Fetched 411 kB in 5s (71.1 kB/s)
Reading package lists... Done
glynn@glynn-K50IJ:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/2,341 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing texlive-pictures (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 texlive-pictures
E: Sub-process /usr/bin/dpkg returned an error code (1)
glynn@glynn-K50IJ:~$ #

thanks for your help

---

### Post by Bashing-om on 2013-11-02
glynnd; Hey,

Let's take the package manager's advise at face value and see what results.
```

sudo apt-get install --reinstall texlive-pictures

```
as per:
> 
dpkg: error processing texlive-pictures (--configure):
Package is in a very bad inconsistent state - you should
reinstall it before attempting configuration.


[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by glynnd on 2013-11-03
hi mate, 
your a star. as i said im a noob but after this convo i know one more command lol. just have to keep reading (and doing). again, thank you
just confirms i made the right choice moving frm MS to Linux, the Linux community as a whole is fantastic and im glad to be a part of it (small i may be but ill learn)

---

### Post by Bashing-om on 2013-11-03
glynnd; Welcome to open source !

One for all and all for one ! -> We are all in this together.

As you have resolution, please mark this thread as solved from the 1st post -> thread tools .

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

