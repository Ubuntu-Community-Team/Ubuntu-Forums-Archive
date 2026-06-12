---
title: "Updates getting 404 error"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by amidude on 2008-07-01
I have 40 updates that are getting the 404 error when trying to connect. How do I get the updates or purge the update manager of them?

I am on an HP Pavilion zd7010us and I think one of the updates fixes my wifi as it is currently not operational.

Any assistance would be greatly appreciated.

---

### Post by kpkeerthi on 2008-07-01
May be the mirror you are using is down. Switch to the main download site under System -> Admin -> Software sources and try the update process again.

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by amidude on 2008-07-01
Thanks for your help. This is what I got:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release     
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [29.0kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources           
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6156B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [7567B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [906B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [19.4kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [264kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [2980B]       
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3465B]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]       
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6623B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [62.3kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [77.3kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [910B]
Fetched 598kB in 2s (242kB/s)                       
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache

---

### Post by plucky on 2008-07-01
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache 

Do you have a Package manager open? i.e is Synaptic or ADD/Remove open.That would cause this error.Close the package managers and try those commands again.

Good Luck

---

### Post by amidude on 2008-07-01
Thank you so much. It worked.

The wild thing is that after all that it went from 40 updates to 173. Thanks again for all of your help.

---

