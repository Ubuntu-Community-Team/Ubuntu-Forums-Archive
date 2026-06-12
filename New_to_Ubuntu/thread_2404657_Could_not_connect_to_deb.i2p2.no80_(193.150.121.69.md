---
title: "Could not connect to deb.i2p2.no:80 (193.150.121.69), connection timed out"
date: 2018-10-26
forum: New to Ubuntu
---

### Post by raakh5 on 2018-10-26
Hello,

When I ran the update then its not updating deb.i2p2.no and throwing error connection time out. Previously It was working fine but suddenly what happened. Please advise

```
# apt update -yHit:1 http://ppa.launchpad.net/webupd8team/brackets/ubuntu bionic InRelease                                                              
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                                                                             
Hit:3 http://linux.teamviewer.com/deb stable InRelease                                                                                   
Hit:4 http://downloads.metasploit.com/data/releases/metasploit-framework/apt lucid InRelease                                             
Hit:5 http://ir.archive.ubuntu.com/ubuntu bionic InRelease                                                                               
Hit:6 http://security.ubuntu.com/ubuntu bionic-security InRelease                                                                        
Hit:7 http://dl.google.com/linux/chrome/deb stable Release                                                                               
Hit:8 http://linux.teamviewer.com/deb preview InRelease                                                                                  
Get:9 http://ir.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                                             
Hit:10 https://repo.skype.com/deb stable InRelease                                                                                       
Hit:12 https://repo.windscribe.com/ubuntu zesty InRelease                                                                                
Get:13 http://ir.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                              
Err:14 http://deb.i2p2.no unstable InRelease                                                                                             
  Could not connect to deb.i2p2.no:80 (193.150.121.69), connection timed out
Fetched 163 kB in 31s (5,314 B/s)              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: Failed to fetch http://deb.i2p2.no/dists/unstable/InRelease  Could not connect to deb.i2p2.no:80 (193.150.121.69), connection timed out
W: Some index files failed to download. They have been ignored, or old ones used instead.
root@sti /h/l/Downloads# 

```
Thanks in anticipation

```
uname -aLinux sti 4.15.0-38-generic #41-Ubuntu SMP Wed Oct 10 10:59:38 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux



```

---

### Post by DuckHook on 2018-10-27
Are you new to Linux and Ubuntu?

Assuming that you are, there are a number of questionable practices that are noticeable in your output:

[LIST=1]
[*]Have you activated your root account? If so, this is not a good idea. It's best to leave root deactivated and elevate yourself into root only one command at a time, using *sudo*.
[*]You have a ton of PPAs loaded, which is not a good idea either, unless you are absolutely positive about the developer. PPAs are a known source of malware. Adding PPAs indiscriminately is a bad habit that Windows users often bring with them to Linux. For new users, I always recommend sticking strictly with repo apps except for those that one simply cannot do without.
[*]You have added the chrome PPA twice. You need to get rid of one of them.
[*]You have two PPAs that are outdated. Assuming that you are running Bionic, both Lucid and Zesty are obsolete for your version. Neither are any longer being supported. These PPAs need to be deleted.
[*]What, exactly, is deb.i2p2.no? If I were in your shoes, there is no way I would add such a PPA to my sources. And without knowing more details (like what this app is and what it is supposed to do), we would just be guessing as to why you cannot connect.
[/LIST]
If you don't mind a bit of more general advice, I would recommend that you refrain from adding PPAs quite so haphazardly. Your collection of third party apps is obscure and—dare I say—dangerous. Aside from possibly breaking your system, adding obsolete/obscure PPAs compromises your security.

---

### Post by raakh5 on 2018-11-01
Hello,

Thanks for your reply

The root is not accessable with password but I am using a sudo user. at that time I was in root by login as `su -'

I am trying to remove PPAs but update output and sources.list output is not same. Please check following:
```
root@sti ~/.ssh# apt update -y
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                         
Hit:2 http://downloads.metasploit.com/data/releases/metasploit-framework/apt lucid InRelease                                                         
Hit:3 http://linux.teamviewer.com/deb stable InRelease                                                                                               
Hit:4 http://deb.i2p2.no unstable InRelease                                                                                                          
Hit:5 http://ppa.launchpad.net/webupd8team/brackets/ubuntu bionic InRelease                                                                          
Get:6 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]                                                                          
Hit:7 http://ir.archive.ubuntu.com/ubuntu bionic InRelease                                                                                           
Hit:8 http://linux.teamviewer.com/deb preview InRelease                                                                                              
Hit:9 http://dl.google.com/linux/chrome/deb stable Release                                                                                           
Get:10 http://ir.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                                                        
Hit:11 https://repo.skype.com/deb stable InRelease                                                                                                   
Hit:13 https://repo.windscribe.com/ubuntu zesty InRelease                                                                                     
Get:14 http://ir.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Fetched 247 kB in 2s (104 kB/s)      
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
root@sti ~/.ssh# nano /etc/apt/sources.list
root@sti ~/.ssh# cat /etc/apt/sources.list 
deb http://ir.archive.ubuntu.com/ubuntu/ bionic main restricted
deb http://ir.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb http://ir.archive.ubuntu.com/ubuntu/ bionic universe
deb http://ir.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb http://ir.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://ir.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb http://ir.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
root@sti ~/.ssh# 



```

Thanks again

---

### Post by dino99 on 2018-11-01
Seems to be down: [https://ipinfo.io/AS57423](https://ipinfo.io/AS57423)

but why using third unknown/unsecure source ?   

I feel you are trying everything you have found  :confused:

---

### Post by raakh5 on 2018-11-01
I have edited GUI=> Software & Updates and now this is what I have when I update:

sudo apt update -y
Hit:1 [http://downloads.metasploit.com/data/releases/metasploit-framework/apt](http://downloads.metasploit.com/data/releases/metasploit-framework/apt) lucid InRelease                                                         
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]                                                                          
Hit:3 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                                                                                               
Hit:4 [http://deb.i2p2.no](http://deb.i2p2.no) unstable InRelease                                                                                                          
Hit:5 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) bionic InRelease                                                                                           
Hit:6 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) preview InRelease                                                                                              
Get:7 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]                                                                         
Hit:8 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                                                                                           
Hit:9 [https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) zesty InRelease                                                                                    
Get:10 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Fetched 247 kB in 3s (91.1 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.


Is the following important or can I remove them?
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [83.2 kB]        
Hit:5 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) bionic InRelease                    
Get:7 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]     
Get:10 [http://ir.archive.ubuntu.com/ubuntu](http://ir.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]

---

### Post by dino99 on 2018-11-01
[https://github.com/rapid7/metasploit-framework/wiki/Nightly-Installers](https://github.com/rapid7/metasploit-framework/wiki/Nightly-Installers)
[https://null-byte.wonderhowto.com/forum/use-anonsurf-hack-anonymous-0180832/](https://null-byte.wonderhowto.com/forum/use-anonsurf-hack-anonymous-0180832/)

---

