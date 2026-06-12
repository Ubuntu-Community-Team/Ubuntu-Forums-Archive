---
title: "Programming error in aptdaemon"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by tech over load on 2012-02-14
> **philinux said:**
> Or simply use this, just in case someone has tried and installed it incorrectly. This will sort it out.

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)


I have tried to install adobe flash but I keep getting errors things I have tried to install the one quoted others are ubuntu restricted extras, and adobe flash  

this is one of the error I get.

Error message as follows:

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Here are the details from the message:

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by oldos2er on 2012-02-15
Post moved to its own thread. Please start a new thread for your problems or questions, rather than hijacking someone else's.

---

### Post by sadaruwan12 on 2012-02-15
Could you please give use the exact error you get when you try to install a software.

---

### Post by tech over load on 2012-02-15
It wouldn't allow me to create my own post so I found one that was close to mine.


Please any help you could provide would be great thanks...

---

### Post by matt_symes on 2012-02-15
Hi

Open a terminal and type

```
sudo apt-get install htop
```

Enter your password. It will not be echoed to the screen.

Post back the errors from that command between code tags.

Kind regards

---

### Post by 23dornot23d on 2012-02-15
( beat me to it ..... was just going to get some basic info to get it started - will leave you with it )

What version of Firefox are you using ..... ?

also do this and cut and post back the list it gives ..... just so we can get an idea of what 
repos you have set up ......

**sudo apt-get update**

---

### Post by matt_symes on 2012-02-15
Hi

> **23dornot23d said:**
> ( beat me to it ..... was just going to get some basic info to get it started - will leave you with it )

What version of Firefox are you using ..... ?

also do this and cut and post back the list it gives ..... just so we can get an idea of what 
repos you have set up ......

**sudo apt-get update**

Good idea. However for a list of all  the sources...

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by tech over load on 2012-02-15
So after entering the code 
     Code:
     sudo apt-get install htop 
    I get this message for package configuration message and at the bottom it says ok but how do I click okay

ckage configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring ttf-mscorefonts-installer &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                             
 &#9474;                                                                              
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;

---

### Post by matt_symes on 2012-02-15
Hi

Hit the <tab> key to highlight the <OK> button and continue (hit <enter>).

Kind regards

---

