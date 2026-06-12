---
title: "medibuntu signature key"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by viswanathan on 2008-05-16
well i accidentally removed my signature key of medibuntu any 1 knows how to reinstall the key coz every time i run sudo apt-get update i get this error```
 maplye@maplye-desktop:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg           
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release.gpg                   
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN        
Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]         
Ign http://packages.medibuntu.org hardy/free Translation-en_IN       
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN
Hit http://security.ubuntu.com hardy-security Release                
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN  
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy-updates Release.gpg          
Ign http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
Ign http://packages.medibuntu.org hardy/non-free Translation-en_IN
Get:2 http://packages.medibuntu.org hardy Release [5590B]
Ign http://packages.medibuntu.org hardy Release
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages          
Hit http://in.archive.ubuntu.com hardy-updates Release               
Hit http://packages.medibuntu.org hardy/free Packages                          
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://in.archive.ubuntu.com hardy/main Packages                 
Hit http://in.archive.ubuntu.com hardy/restricted Packages           
Hit http://in.archive.ubuntu.com hardy/restricted Sources            
Hit http://packages.medibuntu.org hardy/non-free Packages            
Hit http://security.ubuntu.com hardy-security/multiverse Sources     
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://in.archive.ubuntu.com hardy/main Sources
Hit http://in.archive.ubuntu.com hardy/multiverse Sources
Hit http://in.archive.ubuntu.com hardy/universe Sources
Hit http://in.archive.ubuntu.com hardy/universe Packages
Hit http://in.archive.ubuntu.com hardy/multiverse Packages
Hit http://in.archive.ubuntu.com hardy-updates/main Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://in.archive.ubuntu.com hardy-updates/main Sources
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Packages
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Fetched 190B in 3s (61B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```
[IMG]http://file:///home/maplye/Desktop/Screenshot-Software%20Sources.png[/IMG]

---

### Post by HotShotDJ on 2008-05-16
```
sudo apt-get install medibuntu-keyring
```

---

### Post by viswanathan on 2008-05-16
> **HotShotDJ said:**
> ```
sudo apt-get install medibuntu-keyring
```

```
maplye@maplye-desktop:~$ sudo apt-get install medibuntu-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
maplye@maplye-desktop:~$ 

```

sir if i check authection in software sources there i cant find medibuntu key

---

### Post by kesman on 2008-05-16
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by HotShotDJ on 2008-05-16
> **viswanathan said:**
> sir if i check authection in software sources there i cant find medibuntu keyOk.. I suspected that might happen.  Try this:```
sudo apt-get install --reinstall medibuntu-keyring
```

---

### Post by viswanathan on 2008-05-16
> **kesman said:**
> [https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

```
maplye@maplye-desktop:~$ sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
--10:37:16--  http://www.medibuntu.org/sources.list.d/hardy.list
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving www.medibuntu.org... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

100%[====================================>] 226           --.--K/s             

10:37:17 (25.32 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [226/226]

maplye@maplye-desktop:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]
Ign http://packages.medibuntu.org hardy/free Translation-en_IN       
Ign http://packages.medibuntu.org hardy/non-free Translation-en_IN   
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release.gpg                   
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN        
Get:2 http://packages.medibuntu.org hardy Release [5590B]            
Ign http://packages.medibuntu.org hardy Release                           
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN
Hit http://security.ubuntu.com hardy-security Release
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN 
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
Hit http://packages.medibuntu.org hardy/free Packages                
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://security.ubuntu.com hardy-security/main Packages
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://in.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/multiverse Sources    
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://in.archive.ubuntu.com hardy/main Packages
Hit http://in.archive.ubuntu.com hardy/restricted Packages
Hit http://in.archive.ubuntu.com hardy/restricted Sources
Hit http://in.archive.ubuntu.com hardy/main Sources
Hit http://in.archive.ubuntu.com hardy/multiverse Sources
Hit http://in.archive.ubuntu.com hardy/universe Sources
Hit http://in.archive.ubuntu.com hardy/universe Packages
Hit http://in.archive.ubuntu.com hardy/multiverse Packages
Hit http://in.archive.ubuntu.com hardy-updates/main Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://in.archive.ubuntu.com hardy-updates/main Sources
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Packages
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Fetched 5779B in 3s (1652B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
medibuntu-keyring is already the newest version.
The following packages were automatically installed and are no longer required:
  python2.4-minimal python2.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Hit http://security.ubuntu.com hardy-security Release.gpg           
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release.gpg                   
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN        
Get:1 http://packages.medibuntu.org hardy Release.gpg [189B]         
Ign http://packages.medibuntu.org hardy/free Translation-en_IN       
Ign http://packages.medibuntu.org hardy/non-free Translation-en_IN   
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN
Hit http://security.ubuntu.com hardy-security Release                
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN  
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy-updates Release.gpg          
Ign http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
Get:2 http://packages.medibuntu.org hardy Release [5590B]
Ign http://packages.medibuntu.org hardy Release
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://packages.medibuntu.org hardy/free Packages                
Hit http://in.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://packages.medibuntu.org hardy/non-free Packages            
Hit http://in.archive.ubuntu.com hardy/main Packages                 
Hit http://in.archive.ubuntu.com hardy/restricted Packages
Hit http://in.archive.ubuntu.com hardy/restricted Sources
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://in.archive.ubuntu.com hardy/main Sources
Hit http://in.archive.ubuntu.com hardy/multiverse Sources
Hit http://in.archive.ubuntu.com hardy/universe Sources
Hit http://in.archive.ubuntu.com hardy/universe Packages
Hit http://in.archive.ubuntu.com hardy/multiverse Packages
Hit http://in.archive.ubuntu.com hardy-updates/main Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://in.archive.ubuntu.com hardy-updates/main Sources
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Packages
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Fetched 190B in 3s (55B/s)
Reading package lists... Done
***_W: GPG error: http://packages.medibuntu.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783_***
W: You may want to run apt-get update to correct these problems
maplye@maplye-desktop:~$ 


```

sir check the last line out the problem still is there

---

### Post by viswanathan on 2008-05-16
> **HotShotDJ said:**
> Ok.. I suspected that might happen.  Try this:```
sudo apt-get install --reinstall medibuntu-keyring
```

[SIZE="7"]**thank u sir thanx a lot it worked ****[/SIZE]

---

### Post by viswanathan on 2008-05-16
sir b4 removing my signature key i think i have even removed every apt lines of repos from third-party software from software sources sir is there any way i can reinstall all those lines {the official hardy lists i guess }

---

### Post by HotShotDJ on 2008-05-16
> **viswanathan said:**
> sir b4 removing my signature key i think i have even removed every apt lines of repos from third-party software from software sources sir is there any way i can reinstall all those lines {the official hardy lists i guess }I just looked quickly at the output of your original apt-get update post, and it looks like everything that is supposed to be there is, in fact, there.  Take a look at System --> Administration --> Software Sources --> Third Party Software.  Can you tell me what is listed there?

---

### Post by viswanathan on 2008-05-16
> **HotShotDJ said:**
> I just looked quickly at the output of your original apt-get update post, and it looks like everything that is supposed to be there is, in fact, there.  Take a look at System --> Administration --> Software Sources --> Third Party Software.  Can you tell me what is listed there?

[http://pacakages.medibuntu.org/hardy](http://pacakages.medibuntu.org/hardy)
[http://pacakages.medibuntu.org/hardy](http://pacakages.medibuntu.org/hardy) 

former is free and later is non free sir i wouldn't be available for next hour going to my school to get my study certificate c u after an hour sir thanx for ur help

---

### Post by HotShotDJ on 2008-05-16
> **viswanathan said:**
> [http://pacakages.medibuntu.org/hardy](http://pacakages.medibuntu.org/hardy)
[http://pacakages.medibuntu.org/hardy](http://pacakages.medibuntu.org/hardy)Ok.  You probably deleted the the canonical.com archives.  They are available but not activated by default.  You probably don't need them, but if you want to add them back in, just click on the "Add" button and then add them back.  Use the following apt lines (one at a time, of course):
```
deb http://archive.canonical.com/ubuntu hardy partner
```
```
deb-src http://archive.canonical.com/ubuntu hardy partner
```

---

### Post by viswanathan on 2008-05-16
[SIZE="5"]thanx sir [/SIZE]

---

