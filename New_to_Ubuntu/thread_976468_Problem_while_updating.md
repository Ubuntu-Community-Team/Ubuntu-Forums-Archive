---
title: "Problem while updating ?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by anubhav2k on 2008-11-09
while i update in update manager , it searches some 48 items but later gives an error and no new updates come ........

ERROR is 

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

---

### Post by mapes12 on 2008-11-09
Try adding the key. In Terminal:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by anubhav2k on 2008-11-09
> **mapes12 said:**
> Try adding the key. In Terminal:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

when i add this it gives 



anubhav@MegaDeth:~$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
[sudo] password for anubhav: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [189B]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_IN       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release                                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_IN   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources                            
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [9335B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 190B in 4s (42B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?





what shud i do ??

---

### Post by anubhav2k on 2008-11-09
How can i corrct that medibuntu error ?? plz help

---

### Post by bumanie on 2008-11-09
May be try in a few hours or in a day or two - sometimes servers are down for maintenance or have crashed or whatever. It's a bit disconcerting when this happens, but I have found it usually works some time later.

---

### Post by PriceChild on 2008-11-09
Close synaptic/add remove programs/whatever other package manager you have then do it again.

You can only have one package manager running at once to prevent conflicts.

bumanie: please read the error before giving wishy-washy advice.

---

### Post by anubhav2k on 2008-11-09
I am not usin any othe r synaptic running . only package manager

---

### Post by PriceChild on 2008-11-09
Yes, close that then try again.

---

### Post by MasterSander on 2008-11-09
is the output you gave the only thing it says? Or does it also give some advice like, try running apt-get update or dpkg-reconfigure? If so try that in terminal, but close all synaptic first.

---

### Post by anubhav2k on 2008-11-09
Thanks a lot all, i am done now after closing everything .....

---

