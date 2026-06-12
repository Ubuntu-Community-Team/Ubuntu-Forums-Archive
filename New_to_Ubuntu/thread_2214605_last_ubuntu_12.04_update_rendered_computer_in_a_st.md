---
title: "last ubuntu 12.04 update rendered computer in a state of disrepair and useless.Progre"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by okkie on 2014-04-02
This has now become part of my life.Update, lose everything and start all over again. 
If I click on the progress wheel that just keeps on running it says dpkg is used by another program and that program must be stopped first.
Is there some code I can put into A terminal to stop the unknown program please. Rebooting does'nt help.
Thanks

---

### Post by Impavidus on 2014-04-02
If rebooting doesn't help it means that no other package manager is running, but the lock wasn't released properly. One of the package managers probably crashed or was killed. You can remove the lock manually.

---

### Post by mastablasta on 2014-04-02
that shouldn't happen. are you updating via terminal? are all other applications closed?

---

### Post by okkie on 2014-04-02
Thanks for replying.
Normal Ubuntu update notification via the internet which did not complete.Looks like it is still trying to complete the update and that is why the progress arrows are spinning.
Prior to that I had problems with Thunderbird and tried to uninstall it also with no luck.
If Impavidus is right, how does the manual unlock work?

---

### Post by Impavidus on 2014-04-02
[http://ubuntuforums.org/showthread.php?t=2134172](http://ubuntuforums.org/showthread.php?t=2134172) (I think you need post #2).

---

### Post by okkie on 2014-04-03
I tried everything in the above post with no success.
It now appears that instead of doing an update I accidentally asked for an upgrade which in 12.04 is not possible as it is a lts and it got stuck trying to download the .. .. .. 60 image which is probably the latest.
Computer will also not read the install cd so I can reinstall.
Surely there must be a terminal code to stop the ongoing process.If not, how can i GET THE COMPUTER TO READ THE CD?

---

### Post by Impavidus on 2014-04-03
Kernel image 3.2.0-60 is indeed the latest for 12.04.

It's a bit complicated to communicate the input and output of a GUI program using forum posts, so let's forget about the software centre and try the command line. Besides, that also gives clearer error messages. Let the computer finish what it's doing, close the software centre if open, open a terminal and use these commands```
sudo apt-get update
sudo apt-get upgrade
```Post the output here. It should make clear in what state your computer is right now.

I think reinstalling now would be overkill.

---

### Post by mastablasta on 2014-04-03
what does it say if you run the mentioned command?:
sudo rm /var/lib/dpkg/lock

---

### Post by okkie on 2014-04-03
madeleine@madeleine-Inspiron-1501:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
madeleine@madeleine-Inspiron-1501:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
madeleine@madeleine-Inspiron-1501:~$ sudo rm /var/lib/dpkg/lock 
madeleine@madeleine-Inspiron-1501:~$ sudo rm /var/lib/dpkg/lock 
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory
madeleine@madeleine-Inspiron-1501:~$ 

I have also run all the rm commands, no go

---

### Post by Impavidus on 2014-04-03
So there is a second lock stuck. Apart from the lock on the package installation there is also the one on the list. Try removing it with```
sudo rm /var/lib/apt/lists/lock
```Then try again```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by deadflowr on 2014-04-03
> **okkie said:**
> madeleine@madeleine-Inspiron-1501:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
madeleine@madeleine-Inspiron-1501:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
madeleine@madeleine-Inspiron-1501:~$ sudo rm /var/lib/dpkg/lock 
madeleine@madeleine-Inspiron-1501:~$ sudo rm /var/lib/dpkg/lock 
rm: cannot remove `/var/lib/dpkg/lock': No such file or directory
madeleine@madeleine-Inspiron-1501:~$ 

I have also run all the rm commands, no go

Run the
```
sudo dpkg --configure -a
```
command

---

### Post by okkie on 2014-04-06
```
madeleine@madeleine-Inspiron-1501:~$ sudo apt-get update
[sudo] password for madeleine: 
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise Release.gpg
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise Release
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en_ZA
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/main Translation-en
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en_ZA
Ign cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3) precise/restricted Translation-en
Get:1 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise Release.gpg [198 B]                         
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:3 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates Release.gpg [198 B]                 
Get:4 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:5 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security Release.gpg [198 B]                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Get:13 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:14 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise Release [49,6 kB]                          
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11,9 kB]                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11,9 kB]                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates Release                               
Get:17 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg [836 B]            
Get:18 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [8*130 B]                 
Get:19 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [10,8 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Hit [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security Release                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:20 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/main Sources [934 kB]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:21 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release [7*262 B]              
Get:22 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/restricted Sources [5*470 B]               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_ZA             
Get:23 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/universe Sources [5*019 kB]                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_ZA                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:24 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps i386 Packages [67,1 kB]   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Get:25 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games i386 Packages [89,4 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_ZA                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps TranslationIndex             
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games TranslationIndex            
Get:26 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/multiverse Sources [155 kB]                
Get:27 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/main i386 Packages [1*274 kB]              
Get:28 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/restricted i386 Packages [8*431 B]         
Get:29 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/universe i386 Packages [4*796 kB]          
Get:30 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/multiverse i386 Packages [121 kB]          
Get:31 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/main TranslationIndex [3*706 B]            
Get:32 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/multiverse TranslationIndex [2*676 B]      
Get:33 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/restricted TranslationIndex [2*596 B]      
Get:34 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/universe TranslationIndex [2*922 B]        
Get:35 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/main Sources [453 kB]              
Get:36 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/restricted Sources [8*028 B]       
Get:37 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/universe Sources [105 kB]          
Get:38 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/multiverse Sources [8*900 B]       
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en_ZA            
Get:39 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/main i386 Packages [785 kB]        
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en_ZA           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en              
Get:40 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/restricted i386 Packages [12,2 kB] 
Get:41 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/universe i386 Packages [243 kB]    
Get:42 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/multiverse i386 Packages [15,5 kB] 
Get:43 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/main TranslationIndex [3*564 B]    
Get:44 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/multiverse TranslationIndex [2*605 B]
Get:45 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/restricted TranslationIndex [2*461 B]
Get:46 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/universe TranslationIndex [2*850 B]
Get:47 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/main Sources [102 kB]             
Get:48 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/restricted Sources [2*494 B]      
Get:49 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/universe Sources [30,9 kB]        
Get:50 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/multiverse Sources [1*789 B]      
Get:51 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/main i386 Packages [402 kB]       
Get:52 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/restricted i386 Packages [4*620 B]
Get:53 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/universe i386 Packages [96,5 kB]  
Get:54 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/multiverse i386 Packages [2*646 B]
Get:55 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/main TranslationIndex [74 B]      
Get:56 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/multiverse TranslationIndex [72 B]
Get:57 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/restricted TranslationIndex [72 B]
Get:58 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/universe TranslationIndex [73 B]  
Get:59 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/main Translation-en [726 kB]               
Get:60 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/multiverse Translation-en [93,4 kB]        
Get:61 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/restricted Translation-en [2*395 B]        
Get:62 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise/universe Translation-en [3*341 kB]         
Get:63 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/main Translation-en [340 kB]       
Get:64 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/multiverse Translation-en [9*010 B]
Get:65 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/restricted Translation-en [2*988 B]
Get:66 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-updates/universe Translation-en [138 kB]   
Get:67 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/main Translation-en [175 kB]      
Get:68 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/multiverse Translation-en [1*299 B]
Get:69 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/restricted Translation-en [1*253 B]
Get:70 [http://ftp.sun.ac.za](http://ftp.sun.ac.za) precise-security/universe Translation-en [56,7 kB] 
Fetched 19,4 MB in 1min 12s (268 kB/s)                                         
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
madeleine@madeleine-Inspiron-1501:~$ 
```

This is the output of the update. Looks like there is still something wrong.
sorry I took some time but had to go away.What do you want me to do next? Thanks

---

### Post by oldfred on 2014-04-06
My sources does not have extras and it looks like yours may have issues with that. 
Even if you still want that, I might comment out at least until issue is resolved.
You just may need to add # at beginning of line to comment out again. 
This is my default sources.list:

gksudo gedit /etc/apt/sources.list
> ## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


And if getting lock issue see post #10. Make sure terminal is not still running an update, software center and synaptic are not open or any other app that might open and create lock. Then remove lock.

---

### Post by okkie on 2014-04-08
Am I having a hard time here! I cannot find my apt sources list at all. If I understand correct I must go to the sources list and uncomment the two lines above by adding a hash to each line upfront? I notice Ican also not add or remove software packages, Is that also linked to the existing problem?
Sorry but I have never encountered this before.
Thanks

---

### Post by mastablasta on 2014-04-08
yes it's linked. the soruces file tells software center where to get the packages from. you could open software center and go to software sources and oyu should be able to untick the line with aforementioned links.

so what does it do if you run the command form terminal to edit source file manually:
```
gksudo gedit /etc/apt/sources.list


```what error does it report?

Sorry if we are jumping on you with all these commands, but it's because the terminal gives a very good and more in depth error descriptions. you can just copy and paste them into terminal.

otherwise you understand correctly: you need to add the hash (#) in front of extras link line so it looks like oldfreds.
this will comment out the line - meaning the line/link won't be read when the computer is connecting to repository servers. it will be ignored. and we want that for the moment, as it seems it is giving you problems.

---

### Post by okkie on 2014-04-08
This is the gksudo output

deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
d## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receiveeb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise main restricted
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates main restricted
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates main restricted

 any
## review or updates from the Ubuntu security team.
deb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise universe
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise universe
deb [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates universe
deb-src [http://ftp.sun.ac.za/ftp/ubuntu/](http://ftp.sun.ac.za/ftp/ubuntu/) precise-updates universe

looks like my sources list is totally messed-up. Can it be reloaded correctly?

---

### Post by oldfred on 2014-04-08
You may just need to add a # on first line for CD.
And remove d in front of ## on 4th line.

I have this in my notes, but never have used it.
I would backup current sources if you do try to create a new one.
       sudo cp /etc/apt/sources.list ~/sources.list.backup
     The ~ will put backup in your /home.

 You can regenerate new sources file
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

---

### Post by okkie on 2014-04-16
Sorry for the delay, had no internet connection.
I cannot open software centre at all. It appears for a few seconds as if loading and then disappears. My entire problem started with an update. Surely someone knows about this problem or takes responsibility. Thinking back over the years, all my problems started with or as a result of an update.
Is there a way to reinstall 12.04 or to upgrade just to get a working system of some kind.I can then just cancel all updates permanently.
This computer is my daughter's, I talked her into Ubuntu just like many others.

---

### Post by 23dornot23d on 2014-04-16
I have edited your sources list and put it here in a pastebin

[http://paste.ubuntu.com/7261242/](http://paste.ubuntu.com/7261242/)

Some one else may want to check it is ok .......... but all I have removed is CDROM and d and any as they
were probably causing part of the problems.

You can change your own to look like the one I did  and then try

**sudo apt-get update**

after wards ........ post back the results and we can go from there - there is not too much wrong
it just needs a few more steps ...........

---

### Post by Canterwood on 2014-04-16
Yeah, the above sources.list seems fine although you deleted the entire CD line instead of commenting it out. Not that that's wrong or a problem, but it is important to realize if you ever want to update from CD again.

---

### Post by 23dornot23d on 2014-04-16
By the way the 14.04 comes out tomorrow ........ why not try the most up to date version as a install alongside
what you have now .......... just check that there is room on the hard drive for it ...... all problems may be solved.
__________________________________________

As regards fixing the errors in the sources.list

I have done as Fred said and altered your sources.list for you .....  altered one line where the d had come from 

( the pastebin contents can be used as a full file by copying them into /etc/apt/ ) but this is only needed if you cannot edit the one you
already have ........

  - edited to reflect what as now been put in there to correct the original one .

This is one method - if gedit is installed ......... ( on some systems it might be **kate** instead of **gedit** )

**sudo gedit /etc/apt/sources.list**

> 
You may just need to add a # on first line for CD.
And remove d in front of ## on 4th line.



Here is a updated one ......... 

[http://paste.ubuntu.com/7261313/](http://paste.ubuntu.com/7261313/)

---

### Post by GrouchyGaijin on 2014-04-23
I found this thread and thought I am not alone!

I'm running 12.04.
Today there were updates available so I clicked install.
I got a message that some of the updates could not be installed and I should run a partial distribution upgrade.
I've seen that a couple of times over the years so I wasn't concerned.
I did the partial upgrade and went about my business.  
Everything was fine until I rebooted the machine.

[COLOR=#ff0000]**KERNEL PANIC**[/COLOR]

In the end I reinstalled 12.04 from a USB stick I had made then restored my home with Deja-Dup.

Everything *seems* to be OK now and subsequent updates have not crashed my machine. 

I have no idea what happened.  Thank goodness I had a recent backup of home!

---

