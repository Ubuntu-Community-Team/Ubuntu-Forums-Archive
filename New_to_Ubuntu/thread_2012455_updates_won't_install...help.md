---
title: "updates won't install...help???"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by ebonygeek45 on 2012-06-29
Update notifications keep popping up on the screen. When I try to install I come up with the following.   installArchives() failed: Selecting previously unselected package linux-image-3.2.0-26-generic-pae. (Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%%dpkg: unrecoverable fatal error, aborting:  files list file for package `ubuntu-docs' contains empty filename Error in function:    Anyone know what the problem could be,or what I can do to resolve this??

---

### Post by jmfal on 2012-06-29
Welcome to Ubuntu

Lets try some simple things first.

Open the "Update Manager" >> click on settings>>  in the Ubuntu Software section un-check  the CD-rom box if there is a check mark there.

Click on the "Other Software tab and un-check the two lines for CDrom

You will see that  each entry has one line and the line below it is (Source Code) if there is a check in one but not the other put a check in, or better yet put  a check in all boxes except for the CDrom.

Run this in a terminal
```
  sudo apt-get update     
```

If there are errors post them using the code tags "#" by copy/paste the out put between the code brackets.
If there are no errors run this in the terminal
```
 sudo apt-get upgrade   
```

If you are still having problems post them and somebody will help you other wise mark it as [SOLVED] using the forum tools.

---

### Post by afixane on 2012-06-29
```
sudo dpkg --configure -a
```

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ebonygeek45 on 2012-06-29
Thank you for the welcome.

I've done some things since I posted this thread. For a brief background I had ubuntu first, it was way to slow so I figured Xubuntu would be better. I am really loving it more than XP.  I thought that I had removed Ubuntu but through terminal, yet I was still logging in thru Ubuntu to get to Xubuntu. Someone from this forum told me that if I wanted it to work the way it was meant to, I had to uninstall Ubuntu completely. Then reinstall Xubuntu from by bootable disc. 

It solved a lot of my problems, but I am still having the update problem but not like it was before. I followed your instructions and the following is the results. Notification said there was six updates. Apparently 3 did update but 3 did not...that is if I am reading it right. 

> 
sd45@sd45-Aspire-one:~$ sudo apt-get update
[sudo] password for sd45: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [22.1 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]    
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7,120 B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [69.4 kB] 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [17.4 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 168 kB in 1s (88.3 kB/s)
Reading package lists... Done
sd45@sd45-Aspire-one:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
sd45@sd45-Aspire-one:~$ 



---

### Post by ebonygeek45 on 2012-06-29
Hi [Afixane, ]("http://ubuntuforums.org/member.php?u=1673499")

I tried what you suggested. I am still coming up with the same 6 updates as before. 

However your way did make more things happen in the terminal screen.

I don't get it why it won't do what it is supposed to do unless maybe it is a duplicate or something??
[]("http://ubuntuforums.org/member.php?u=1673499")

---

### Post by jmfal on 2012-06-29
Run these two commands Please:

```
  lsb_release -a    
```

```
    uname -a     
```

You can copy/paste them if you want

---

### Post by afixane on 2012-06-29
> **ebonygeek45 said:**
> Hi [Afixane, ]("http://ubuntuforums.org/member.php?u=1673499")

I tried what you suggested. I am still coming up with the same 6 updates as before. 

However your way did make more things happen in the terminal screen.

I don't get it why it won't do what it is supposed to do unless maybe it is a duplicate or something??


```
sudo dpkg --configure -a
```sudo = Super User Do (same as run as administrator in Windows)
dpkg --configure -a = Detect a DPKG problem, and fix the problem if the problem found or can be fixed.


I suggest you to type that, just for identifying your dpkg is broken or not, but since you still have the same update, it's mean the problem is not in dpkg....

---

### Post by drmrgd on 2012-06-29
> **ebonygeek45 said:**
> Thank you for the welcome.

I've done some things since I posted this thread. For a brief background I had ubuntu first, it was way to slow so I figured Xubuntu would be better. I am really loving it more than XP.  I thought that I had removed Ubuntu but through terminal, yet I was still logging in thru Ubuntu to get to Xubuntu. Someone from this forum told me that if I wanted it to work the way it was meant to, I had to uninstall Ubuntu completely. Then reinstall Xubuntu from by bootable disc. 

It solved a lot of my problems, but I am still having the update problem but not like it was before. I followed your instructions and the following is the results. Notification said there was six updates. Apparently 3 did update but 3 did not...that is if I am reading it right.

Everything is looking OK here.  By default, new Linux kernels are not installed by a simple upgrade.  In order to upgrade the kernel, you'll have to run:

```
sudo apt-get dist-upgrade
``` 

That will download and upgrade the last 3 packages.

---

### Post by ebonygeek45 on 2012-06-30
> **afixane said:**
> ```
sudo dpkg --configure -a
```sudo = Super User Do (same as run as administrator in Windows)
dpkg --configure -a = Detect a DPKG problem, and fix the problem if the problem found or can be fixed.


I suggest you to type that, just for identifying your dpkg is broken or not, but since you still have the same update, it's mean the problem is not in dpkg....

Just wanted to test it out my results were;

> 
sd45@sd45-Aspire-one:~$ sudo dpkg --configure -a
[sudo] password for sd45: 
sd45@sd45-Aspire-one:~$ 


Was that the results I was supposed to get.

Xubuntu is great I just learned you can make the terminal transparent. I am kicking myself for not trying it sooner.

---

### Post by ebonygeek45 on 2012-06-30
> **drmrgd said:**
> Everything is looking OK here.  By default, new Linux kernels are not installed by a simple upgrade.  In order to upgrade the kernel, you'll have to run:

```
sudo apt-get dist-upgrade
```That will download and upgrade the last 3 packages.


):P

That was it. 

```
sudo apt-get dist-upgrade
```It worked like a charm. This install is now a complete success. Thank you so much. 

jmfal I didn't get a chance to try what you suggested. A big Thank you to you for your input.

---

