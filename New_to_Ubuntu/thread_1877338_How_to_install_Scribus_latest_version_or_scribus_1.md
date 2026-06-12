---
title: "How to install Scribus latest version or scribus 1.5  in ubuntu 11.10"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by anandharaja on 2011-11-07
hi,
i want to install scribus in my system but unfortunately scribus 1.4rc3 is available in software center, rc6 is the latest version, what is the procedure to install latest scribus build. i found this ppa for scribus 1.5 version
> deb [http://ppa.launchpad.net/scribus/ppa/ubuntu](http://ppa.launchpad.net/scribus/ppa/ubuntu) oneiric main 
deb-src [http://ppa.launchpad.net/scribus/ppa/ubuntu](http://ppa.launchpad.net/scribus/ppa/ubuntu) oneiric main 
 
but i got lots of error this ppa not working.

anyone using scribus 1.5 or 1.4rc6, please tell the procedure to install.

---

### Post by rushikesh988 on 2011-11-07
> **anandharaja said:**
> hi,
i want to install scribus in my system but unfortunately scribus 1.4rc3 is available in software center, rc6 is the latest version, what is the procedure to install latest scribus build. i found this ppa for scribus 1.5 version

but i got lots of error this ppa not working.

anyone using scribus 1.5 or 1.4rc6, please tell the procedure to install.
try this in terminal
> sudo apt-get update
sudo apt-get install scribus


This will install Scribus

---

### Post by fantab on 2011-11-07
> **anandharaja said:**
> hi,
i want to install scribus in my system but unfortunately scribus 1.4rc3 is available in software center, rc6 is the latest version, what is the procedure to install latest scribus build. i found this ppa for scribus 1.5 version

**but i got lots of error **this ppa not working.

anyone using scribus 1.5 or 1.4rc6, please tell the procedure to install.

What kind of errors do you get.

It is generally safe to use one in the Software-downloads, for one it is known to work.

---

### Post by BBQdave on 2011-11-07
> **anandharaja said:**
> hi,
i want to install scribus in my system but unfortunately scribus 1.4rc3 is available in software center, rc6 is the latest version, what is the procedure to install latest scribus build. i found this ppa for scribus 1.5 version

but i got lots of error this ppa not working.

anyone using scribus 1.5 or 1.4rc6, please tell the procedure to install.

Is there a reason that you need 1.4 rc6, 1.4x should be fine.

I am running Debian6 with Scribus 1.4 (for awhile now).  And through all the rc updates (currently I am at 1.4 rc6), I have noticed little change, functionality of Scribus has stayed the same.:)

---

### Post by anandharaja on 2011-11-08
> **BBQdave said:**
> Is there a reason that you need 1.4 rc6, 1.4x should be fine.


in software center Scribus 1.4rc3 is available but 1.4rc6 is the latest official release. and also 1.5 version have picture manager its easy to manage the pictures used in the document.

---

### Post by beew on 2011-11-08
Well without telling us what errors you get it is hard for people to help you. How did you add the ppa exactly? 
 
 Try this
 ```
sudo apt-add-repository ppa:scribus/ppa
 sudo apt-get update
 sudo apt-get install scribus
```

---

### Post by beew on 2011-11-08
> **fantab said:**
> 
It is generally safe to use one in the Software-downloads, for one it is known to work.

Not necessarily, there are things in the software center that don't work, or only partially.

---

### Post by rolandixor on 2011-11-29
Add the ppa (using sudo apt-add-repository ppa:scribus/ppa) then run sudo apt-get update and sudo apt-get install scribus-trunk.

---

