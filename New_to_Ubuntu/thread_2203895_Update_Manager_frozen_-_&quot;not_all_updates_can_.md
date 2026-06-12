---
title: "Update Manager frozen - &quot;not all updates can be installed&quot;"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by Herndon_Jeffreys on 2014-02-05
I have Ubuntu 12.04LTS.  When I was running the update manager, it was interrupted.  When I restarted the computer, and tried to run the update manger, I received the message "Not all updates can be instralled."  It gives me the option for a partial upgrade.  When I click the button, I am asked for a password, I am told "unable to get exclusive lock."  When I click OK, the update manager shuts down.

When I try to update through the terminal (sudo apt-get update) I get the following message: "E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

When I run sudo fuser /var/lib/dpkg/lock the response is: 

/var/lib/dpkg/lock:   2256

When I run sudo lsof -P /var/lib/dpkg/lock the response is:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/herndon/.gvfs
Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF    NODE NAME
dpkg    2256 root    3uW  REG    8,1        0 1311667 /var/lib/dpkg/lock

I have tried restarting the computer and running sudo killall. but without success.  Please Help

---

### Post by PotatoHead007 on 2014-02-06
Hey :)
Did you try this ([https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)) link? Troubleshooting is often the answer :)
But you could try this:
Open terminal, type 
```
ps aux | grep apt
```
This will list all processes running that have "apt" in them. If you see "apt-get" or "aptitude", run
```
kill <processnumber>
```
and if that does not work, run
```
kill -9 processnumber
```
That should kill the process and may remove the lock :) If not, ask away.

---

### Post by Herndon_Jeffreys on 2014-02-06
Thanks!  When I ran ps aux | grep apt nothing showed up with aptitude or get-apt in it.  I ran update manager just to double check and got the message when I clicked "no" to parital upgrade "software index is broken - It is impossible to add or remove any software.Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."  I tried it and got "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"  Any suggestions?  Should I try to uninstall and reinstall the software manager?

---

### Post by MoebusNet on 2014-02-06
When I had a similar situation I used:

```
sudo apt-get clean

sudo rm /var/lib/apt/lists/*

sudo rm /var/lib/apt/lists/partial/*

sudo apt-get clean

sudo apt-get update
```

For a more complete discussion of what was wrong and what the recommended fixes were, look at: [http://ubuntuforums.org/showthread.php?t=2049780&p=12217855#post12217855](http://ubuntuforums.org/showthread.php?t=2049780&p=12217855#post12217855)

---

### Post by Herndon_Jeffreys on 2014-02-06
Thanks!  I am grateful... I tried it, got a little further, but it still came up with an error:

Dell-DE051:~$ sudo apt-get clean

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
herndon@herndon-Dell-DE051:~$ sudo rm /var/lib/apt/lists/*
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
herndon@herndon-Dell-DE051:~$ sudo rm /var/lib/apt/lists/partial/*
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
herndon@herndon-Dell-DE051:~$ sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory

Dell-DE051:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]      
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]    
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                       
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [8,130 B]                 
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [10.8 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [97.1 kB]      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.9 kB]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,791 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [378 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [94.7 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,639 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [168 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [1,299 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [1,253 B]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [56.3 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex [3,706 B]    
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex [2,676 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex [2,596 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex [2,922 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [451 kB]      
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [8,028 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [104 kB]  
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,482 B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [769 kB]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [12.2 kB]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [240 kB]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.7 kB]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [4,226 B]   
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [36.4 kB]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [4,811 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [37.7 kB]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex [73 B]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en [726 kB]       
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en [2,395 B]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en [3,341 kB] 
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [335 kB]
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [8,473 B]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en [2,988 B]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [137 kB]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en [4,235 B]
Get:74 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en [4,610 B]
Get:75 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en [14 B]
Get:76 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en [27.7 kB]
Fetched 19.8 MB in 6min 40s (49.4 kB/s)                                        
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Dell-DE051:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any help would be greatly appreciated.

---

### Post by Herndon_Jeffreys on 2014-02-06
OK - I just noticed something...  The Ubuntu Software Center has been trying to install something called "searching" for a couple of days.  I hit "cancel" and it has been trying to cancel all day now (the "Progress" button has a 1 by it and is "circling."  I think this may be interfering with the update manager.  Is there a way in the terminal to cancel this?

---

### Post by Herndon_Jeffreys on 2014-02-06
Thanks to everyone!  The problem has been solved!  I went into the Gnome system monitor through the terminal.  I clicked the processes tab.  I closed process dkpg 2256 (the result of running sudo fuser /var/lib/dpkg/lock)  and exited out.  In the terminal, I typed sudo apt-get update.  It started updating, but stopped partially through the update saying I needed to restart the process I had closed.  I restarted the computer, thinking that would restart the process that I just closed.  When I tried to update in the terminal, it worked.  When I tried to update using the update manager, it worked.  Thanks again for your patience with a "newbie."

---

