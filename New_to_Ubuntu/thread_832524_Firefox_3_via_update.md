---
title: "Firefox 3 via update"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by richg on 2008-06-17
A few days ago I saw that I have Firefox 3b5 when using Ubuntu 8.04. Late this morning when I powered up the PC I saw that I had updates available. I looked at About and now I see Firefox 3.0. Am I to assume that I have the latest release of Firefox? 
The official download is today and I thought that my update was much quicker than I expectd. Just wondering. Thanks.
[IMG]http://i98.photobucket.com/albums/l267/richg1998/Computers/Screenshot.png[/IMG]

Rich

---

### Post by Zenze on 2008-06-17
Yes it should be the latest release.

---

### Post by coolbrook on 2008-06-17
The Gecko date string I have is 2008061015.

In terminal...

```
sudo apt-get update
```

and see if anything new pops up.

---

### Post by richg on 2008-06-17
Thanks. This is what I got. What do I do with it, what does it mean? Thanks.

lexon@lexon-desktop:~$ sudo apt-get update
[sudo] password for lexon: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release     
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [28.0kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [249kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6156B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [7291B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [906B]      
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [12.7kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [1984B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [3465B]   
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]      
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6623B]  
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [73.3kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [910B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [48.7kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [8028B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [8054B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [1433B]
Fetched 574kB in 3s (187kB/s)                      
Reading package lists... Done


Rich

---

### Post by billgoldberg on 2008-06-17
Those are just updates the repositories.

If something new is found, the update manager should pop up.

Those are just the sources the update manager downloads from.

---

### Post by rzrgenesys187 on 2008-06-17
```
sudo apt-get upgrade
```
This should download any available updates

---

### Post by richg on 2008-06-17
coolbrook has this. The Gecko date string coolbrook has is 2008061015.

I have Gecko 2008060309. What is the difference? Anything significant?

Thanks all for the quick replies.

Rich

---

### Post by Happy_Man on 2008-06-17
Well, as of today, 6/17/2008, it seems that the Ubuntu version of Firefox 3 is the final (at least as far as I can tell).

---

### Post by richg on 2008-06-17
Thank you happy man. I will go wih what I have. It looks very good. Better than Freespire 2.0.
I am in the process of switching over from Freespire. Ubuntu is taking some getting use to, plus the forums are great.

Rich

---

