---
title: "Problem apt-getting pygame"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by jjclonker on 2013-12-04
Well I tried sudo apt-get install pygame and I got this error.:confused:

jj@jj-Latitude-D610:~$ sudo apt-get install pygame
[sudo] password for jj: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
jj@jj-Latitude-D610:~$ 

P.S: Is there a spacific way that I should post code?:-s

---

### Post by Bashing-om on 2013-12-04
jjclonker; Hi ! Welcome to the forum .

That error generally indicates that you have more than one instance of a package manager opening. One can only have one open.
As in the Software Center, or synaptic (if you installed that tool) or an instance of "dpkg".

Close all out and reboot the operating system.
Now try and install "pygame"

Code tags: see:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]it's all in the process of learning[/INDENT][/INDENT]

---

### Post by jjclonker on 2013-12-06
Thanks!:KS

Hmm... I tried what you said and I got this:

```
jj@jj-Latitude-D610:~$ sudo apt-get install pygame
[sudo] password for jj: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
jj@jj-Latitude-D610:~$ sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process
jj@jj-Latitude-D610:~$ 
```

---

### Post by jjclonker on 2013-12-06
Thanks!:KS

Hmm... I tried what you said and I got this:

```
jj@jj-Latitude-D610:~$ sudo apt-get install pygame
[sudo] password for jj: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
jj@jj-Latitude-D610:~$ sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process
jj@jj-Latitude-D610:~$ 
```

---

### Post by Bashing-om on 2013-12-06
jjclonker; Well,

Going deeper, let's try and remove the lock;
```

sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock

```
Now try and install the package:
```

sudo apt-get install pygame

```

Where there is a will there is a way -> workie ?
[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by jjclonker on 2013-12-06
It seems like I have some deeper isues... I tried the first code and my screen blacked out and said that I had a broken pipe.

When I try to shut down my computer it fails.

When I start it back up it shows about a page worth of text and errors, but then it works just fine exept for the unexplanitory system error that dose not efect anything, but gets anoying after some time.

This has happend to me twice and only happens after I update my ubuntu 12.04.

I re-installed my ubuntu and it cleared the problems up, but when I updated my system they came back.

Sorry if this is supper vage. :(

P.S.: The double post was because of my slow internet.#-o

---

### Post by Bashing-om on 2013-12-06
jjclonker;
To be vague when you do not know is understanadable, we can work through that !
OK, Background: Is this a fresh install we are working with at this time ?

Show me the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d

``` As a place to start and see what is happening.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by jjclonker on 2013-12-06
Ok. It is a fresh install, but I did install some ubuntu apps. I have not installed updates untill now. Ubutu is the only operating system on my computer.

```
jj@jj-Latitude-D610:~$ sudo apt-get update
[sudo] password for jj: 
Sorry, try again.
[sudo] password for jj: 
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://br.archive.ubuntu.com precise Release.gpg                 
Get:2 http://br.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://br.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://extras.ubuntu.com precise Release                         
Hit http://ppa.launchpad.net precise Release                                   
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://br.archive.ubuntu.com precise Release                               
Get:4 http://br.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://br.archive.ubuntu.com precise-backports Release                     
Get:5 http://security.ubuntu.com precise-security/main Sources [93.9 kB]       
Hit http://br.archive.ubuntu.com precise/main Sources                          
Hit http://br.archive.ubuntu.com precise/restricted Sources                    
Hit http://br.archive.ubuntu.com precise/universe Sources                      
Hit http://br.archive.ubuntu.com precise/multiverse Sources                    
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Hit http://br.archive.ubuntu.com precise/main i386 Packages                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://br.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://br.archive.ubuntu.com precise/universe i386 Packages                
Hit http://br.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://br.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://br.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://br.archive.ubuntu.com precise/restricted TranslationIndex           
Get:6 http://security.ubuntu.com precise-security/restricted Sources [2,494 B] 
Hit http://br.archive.ubuntu.com precise/universe TranslationIndex             
Get:7 http://security.ubuntu.com precise-security/universe Sources [29.9 kB]   
Get:8 http://br.archive.ubuntu.com precise-updates/main Sources [428 kB]       
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,797 B] 
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [367 kB] 
Get:11 http://br.archive.ubuntu.com precise-updates/restricted Sources [7,006 B]
Get:12 http://br.archive.ubuntu.com precise-updates/universe Sources [101 kB]  
Get:13 http://br.archive.ubuntu.com precise-updates/multiverse Sources [8,812 B]
Get:14 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:15 http://br.archive.ubuntu.com precise-updates/main i386 Packages [737 kB]
Get:16 http://security.ubuntu.com precise-security/universe i386 Packages [89.5 kB]
Get:17 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,635 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Get:18 http://br.archive.ubuntu.com precise-updates/restricted i386 Packages [11.4 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:19 http://br.archive.ubuntu.com precise-updates/universe i386 Packages [229 kB]
Get:20 http://br.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.4 kB]
Hit http://br.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://br.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://br.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://br.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://br.archive.ubuntu.com precise-backports/main Sources                
Hit http://br.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://br.archive.ubuntu.com precise-backports/universe Sources            
Hit http://br.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://br.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://br.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://br.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://br.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://br.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://br.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://br.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://br.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://br.archive.ubuntu.com precise/main Translation-en
Hit http://br.archive.ubuntu.com precise/multiverse Translation-en
Hit http://br.archive.ubuntu.com precise/restricted Translation-en
Hit http://br.archive.ubuntu.com precise/universe Translation-en
Hit http://br.archive.ubuntu.com precise-updates/main Translation-en
Hit http://br.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://br.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://br.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://br.archive.ubuntu.com precise-backports/main Translation-en
Hit http://br.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://br.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://br.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 2,227 kB in 2min 30s (14.8 kB/s)
Reading package lists... Done
jj@jj-Latitude-D610:~$ 

```

By the way thanks so much for your hellp!:D

---

### Post by kostkon on 2013-12-07
You could use the Software centre to install it. Anyway, the name of the package is python-pygame, so you'll need to give:
```
sudo apt-get install python-pygame
```

Hope that helps.

---

### Post by jjclonker on 2013-12-07
OH! Your right it is python-pygame! :grin:

Now if I get the rest of my system cleaned up I will be supper happy. :KS

---

### Post by Bashing-om on 2013-12-07
jjclonker; Hey,

See kostkon's last advisement .

So far so good, "update' runs clean.

what results now from:
```

sudo apt-get upgrade

```
And then we can look at installing - "python-pygame" .

[INDENT][INDENT]my pleasure to help[/INDENT][/INDENT]

---

### Post by jjclonker on 2013-12-07
Ok. I just installed python-pygame before I saw your post I hope that does not mess stuff up.

I ran your code and got this:

```
jj@jj-Latitude-D610:~$ sudo apt-get upgrade
[sudo] password for jj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jj@jj-Latitude-D610:~$ 
```

That's what's wierd it seems updated, but it is having shut-down errors and system errors. I have to say I'm at a loss as to what might be causing the problems. :confused:

---

### Post by Bashing-om on 2013-12-07
jjclonker; That too looks good !
Package manager appears to be in a happy state, reporting no errors.
If "python-pygame" is functional, then the original quest is resolved. Please mark this thread as solved; 1st post -> thread tools.
AND open a new thread with the descriptive title "having shut-down errors and system errors",

A new thread will get a much broader viewing and a better response rate. For now take a read through the log file " /var/log/syslog " and see if there are any serious errors and warnings logged . As a place to start looking.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by jjclonker on 2013-12-08
Ok. The thread is marked as [SOLVED]!:KS

I will open another thread for my other problems like you said.

Thanks again Bashing-om! ;)

You have been a joy to work with.:D

---

### Post by Bashing-om on 2013-12-08
jjclonker; Good deal .

Will look for your new thread, see how I might be of assistance,

hey !
[INDENT][INDENT]it's open source
[INDENT][INDENT][INDENT]we are all in this together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

