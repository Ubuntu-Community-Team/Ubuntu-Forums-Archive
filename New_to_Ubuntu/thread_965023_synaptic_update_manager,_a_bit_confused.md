---
title: "synaptic update manager, a bit confused?"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by matthewbrave on 2008-10-31
i am running ubuntu 8.04

i am trying to update my system, but when i try it says all the updates status is 'hit'  what does this mean.

i am also getting a few failed. i am on a good internet connection. what do you think the problem is??

---

### Post by _sAm_ on 2008-10-31
I think its hard for the more advanced users to answer your question without more info. 

Open a terminal(Applications> Accessories > Terminal ) and run:
sudo aptitude update 

Post the output here.

---

### Post by matthewbrave on 2008-10-31
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB            
Err [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_GB                
  Could not connect to wine.budgetdedicated.com:80 (81.171.111.184). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources                
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg                              
  Could not connect to gb.archive.ubuntu.com:80 (194.169.254.10), connection timed out
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
  Unable to connect to gb.archive.ubuntu.com http:
Reading package lists... Done

---

### Post by roger_1960 on 2008-10-31
Hi

This might be just overloaded servers.  I couldn't download a small apptoday either.

---

### Post by Paqman on 2008-10-31
The system can hunt down a good server for you. System > Admin > Software Sources > Download from: > Other > select best server.

Things are bound to be a little hairy right now, with Intrepid just released.

---

### Post by matthewbrave on 2008-10-31
ok i will go and do that then


thanks

---

