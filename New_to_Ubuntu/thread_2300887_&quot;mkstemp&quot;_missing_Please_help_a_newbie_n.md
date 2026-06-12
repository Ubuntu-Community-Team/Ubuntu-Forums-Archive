---
title: "&quot;mkstemp&quot; missing? Please help a newbie nitwit!!"
date: 2015-10-29
forum: New to Ubuntu
---

### Post by owen15 on 2015-10-29
Hello!

To cut a long, dull story short, I've only been using Lubuntu 15 Wily-something since Saturday. I like it, but now get this error message:

*E: Couldn't create temporary file to work with /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_wily_InRelease - mkstemp (2: No such file or directory)*
*E: The package lists or status file could not be parsed or opened.*
*E: _cache->open() failed, please report.*

Could somebody please tell me (in idiot-speak) what this means and what I should do? I can't install anything anymore, and I'm about as fluent in Linux "computer language" as I am in Eskimo.

THANKS VERY MUCH IN ADVANCE!!!!

---

### Post by ajgreeny on 2015-10-29
Open a terminal and run command ```
sudo apt-get update
``` and post the output back here in code tags (see my signature below for a "how-to").

If there are no errors from that you may find that command ```
sudo apt-get upgrade
``` will run and leave you with a fully updated system with no ongoing problems.

---

### Post by owen15 on 2015-10-29
[COLOR=#000000]```
[/COLOR]
Ign http://dl.google.com stable InRelease
Ign http://ppa.launchpad.net wily InRelease                                    
Hit http://gb.archive.ubuntu.com wily InRelease                                
Get:1 http://gb.archive.ubuntu.com wily-updates InRelease [64.4 kB]         
Hit http://gb.archive.ubuntu.com wily-backports InRelease
Get:2 http://security.ubuntu.com wily-security InRelease [64.4 kB]
Hit http://dl.google.com stable Release.gpg           
Ign http://ppa.launchpad.net wily Release.gpg         
Ign http://ppa.launchpad.net wily Release                    
Hit http://dl.google.com stable Release                                        
Err http://ppa.launchpad.net wily/main i386 Packages                           
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-en_GB
Ign http://ppa.launchpad.net wily/main Translation-en
Hit http://dl.google.com stable/main i386 Packages                         
Get:3 http://security.ubuntu.com wily-security/main Sources [6,896 B]          
Hit http://gb.archive.ubuntu.com wily/main Sources                             
Get:4 http://gb.archive.ubuntu.com wily-updates/main Sources [7,733 B]         
Get:5 http://gb.archive.ubuntu.com wily-updates/restricted Sources [28 B]      
Get:6 http://gb.archive.ubuntu.com wily-updates/universe Sources [1,578 B]     
Get:7 http://security.ubuntu.com wily-security/restricted Sources [28 B]       
Get:8 http://gb.archive.ubuntu.com wily-updates/multiverse Sources [28 B]      
Get:9 http://gb.archive.ubuntu.com wily-updates/main i386 Packages [15.3 kB]   
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://dl.google.com stable/main Translation-en                            
Get:10 http://gb.archive.ubuntu.com wily-updates/restricted i386 Packages [28 B]
Get:11 http://security.ubuntu.com wily-security/universe Sources [1,578 B]     
Get:12 http://gb.archive.ubuntu.com wily-updates/universe i386 Packages [7,194 B]
Get:13 http://gb.archive.ubuntu.com wily-updates/multiverse i386 Packages [28 B]
Get:14 http://gb.archive.ubuntu.com wily-updates/main Translation-en [8,454 B] 
Get:15 http://security.ubuntu.com wily-security/multiverse Sources [28 B] 
Get:16 http://security.ubuntu.com wily-security/main i386 Packages [13.3 kB]   
Get:17 http://gb.archive.ubuntu.com wily-updates/multiverse Translation-en [28 B]
Get:18 http://gb.archive.ubuntu.com wily-updates/restricted Translation-en [28 B]
Get:19 http://gb.archive.ubuntu.com wily-updates/universe Translation-en [4,784 B]
Get:20 http://security.ubuntu.com wily-security/restricted i386 Packages [28 B]
Hit http://gb.archive.ubuntu.com wily/restricted Sources                       
Hit http://gb.archive.ubuntu.com wily/universe Sources             
Get:21 http://security.ubuntu.com wily-security/universe i386 Packages [6,923 B]
Hit http://gb.archive.ubuntu.com wily/multiverse Sources                       
Hit http://gb.archive.ubuntu.com wily/main i386 Packages           
Hit http://gb.archive.ubuntu.com wily-backports/main Sources       
Get:22 http://security.ubuntu.com wily-security/multiverse i386 Packages [28 B]
Hit http://gb.archive.ubuntu.com wily-backports/restricted Sources 
Hit http://gb.archive.ubuntu.com wily-backports/universe Sources   
Hit http://gb.archive.ubuntu.com wily-backports/multiverse Sources 
Hit http://gb.archive.ubuntu.com wily-backports/main i386 Packages 
Hit http://gb.archive.ubuntu.com wily-backports/restricted i386 Packages
Get:23 http://security.ubuntu.com wily-security/main Translation-en [7,738 B]
Hit http://gb.archive.ubuntu.com wily-backports/universe i386 Packages         
Hit http://gb.archive.ubuntu.com wily-backports/multiverse i386 Packages       
Hit http://gb.archive.ubuntu.com wily-backports/main Translation-en
Hit http://gb.archive.ubuntu.com wily-backports/multiverse Translation-en
Get:24 http://security.ubuntu.com wily-security/multiverse Translation-en [28 B]
Hit http://gb.archive.ubuntu.com wily-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com wily-backports/universe Translation-en
Hit http://gb.archive.ubuntu.com wily/restricted i386 Packages     
Hit http://gb.archive.ubuntu.com wily/universe i386 Packages       
Get:25 http://security.ubuntu.com wily-security/restricted Translation-en [28 B]
Hit http://gb.archive.ubuntu.com wily/multiverse i386 Packages     
Hit http://gb.archive.ubuntu.com wily/main Translation-en_GB       
Get:26 http://security.ubuntu.com wily-security/universe Translation-en [4,715 B]
Hit http://gb.archive.ubuntu.com wily/main Translation-en                      
Hit http://gb.archive.ubuntu.com wily/multiverse Translation-en_GB         
Hit http://gb.archive.ubuntu.com wily/multiverse Translation-en
Hit http://gb.archive.ubuntu.com wily/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com wily/restricted Translation-en
Hit http://gb.archive.ubuntu.com wily/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com wily/universe Translation-en
Fetched 215 kB in 29s (7,368 B/s)                                              
W: Failed to fetch http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.


[COLOR=#000000]
```
[/COLOR][COLOR=#000000]
[/COLOR]

Thanks so much for your reply, sir!! Even though there was an error (see above), I ran the sudo apt-get upgrade command anyway, and that completed without an error message. Everything seems hunky dory now. You're a hero :)

---

### Post by ajgreeny on 2015-10-30
Great.

The problem error is probably because that ppa is not yet available yet for wily.  Open software-sources and disable that ppa from the Other Software tab, refresh the repos and all should be well.

---

### Post by grahammechanical on 2015-10-30
I do see this

> W: Failed to fetch [http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu/dists/wily/main/binary-i386/Packages](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu/dists/wily/main/binary-i386/Packages)  404  Not Found

I have used audio-recorder for about 2 years. It is an excellent utility. It does not have a PPA for wily. Instead there is a new PPA that we can use.


[https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa)

Installation:
0) Remove the OLD, PRIVATE PPA that belonged to the developer.  Run:

```
sudo add-apt-repository --remove ppa:osmoma/audio-recorder
```

1) Add new PPA.
Then update your package list and Install the latest version of audio-recorder.  Run:
```
sudo add-apt-repository ppa:audio-recorder/ppa
sudo apt-get -y update
sudo apt-get install --reinstall audio-recorder
```

Regards.

---

