---
title: "SMART Board Drivers"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by austinious on 2011-10-03
Hi,

Tried to install the sutopackage drivers and got this message.

# Checking for SMART Install Frontend ... passed                                
## Preparing package: SMART Install Frontend                                    
## Checking for required C library versions ... failed   
## FAIL:                                                                        
## Your copy of glibc, a core system library, is too old for this package.
## You need at least the following symbols in glibc: .
## 
## This error normally means that whoever built the package did not build it correctly.
## Please report the contents of this message to the provider of this package, and
## ask them to rebuild it using apbuild.
## 
## Upgrading glibc is highly dangerous, so we recommend in this situation that you
## compile the app you want to install from the sources if possible. Sorry :(
FAIL: Unable to prepare package SMART Software.


?Help?

I've tried to follow the companies directions for the RPM and DEBIAN packages, but I'm too new to this OS.

This is the link to their instructions
[http://smarttech.com/us/Support/Browse+Support/Support+Documents/Notebook/10Linux/135949](http://smarttech.com/us/Support/Browse+Support/Support+Documents/Notebook/10Linux/135949)

Any help would be most appreciated.

Kunbuntu 11.? Too new to even find this for sure, just downloaded last week.
SMART drivers 10.4, 600 series board.

---

### Post by seawolf167 on 2011-10-03
Couple things:

[LIST=1]
[*]Are you using a 64bit OS? (x86_64) The link you provided mentioned that the 64bit isn't supported
[*]What happens if you download and attempt to install the Debian package (.deb file)? All you have to do there is double click the installer and it will automatically install
[/LIST]
Additionally, you might try installing

```
sudo apt-get install glibc-2.10-1
```

and see if that helps out.

---

### Post by austinious on 2011-10-03
I'll try that tomorrow.  With Debian and RPM I can't get them to verify the packages, let alone make a key.  I'm working on the whole key thing, it seems to be important in Linux.

I've tried Linux a couple times in the past, and everytime some damn driver thwarts me.  This time I'll persevere.

Thanks

---

### Post by austinious on 2011-10-04
She no workaustinious@Room200-Display:~$ sudo apt-get install glibc-2.10-1
[sudo] password for austinious: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package glibc-2.10-1
E: Couldn't find any package by regex 'glibc-2.10-1'
austinious@Room200-Display:~$ 

Any thoughts?

---

### Post by seawolf167 on 2011-10-04
It worked for me - though you may have a different sources.list file if you are on a different version. Try hitting [TAB] twice to get a listing of possible packages

```
sudo apt-get install glibc[TAB][TAB]
```

---

