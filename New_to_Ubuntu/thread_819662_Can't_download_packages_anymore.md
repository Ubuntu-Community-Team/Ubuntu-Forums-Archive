---
title: "Can't download packages anymore"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by HaemoLacria on 2008-06-05
When I try to download something via Add/Remove or the Synaptic Package Manager it says this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And when I try to run ```
dpkg --configure -a
``` it says: dpkg: requested operation requires superuser privilege

When I type sudo and the code it says: sudo: dpkg:: command not found

I hope somebody can help, thanks

---

### Post by Oldsoldier2003 on 2008-06-05
> **HaemoLacria said:**
> When I try to download something via Add/Remove or the Synaptic Package Manager it says this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And when I try to run ```
dpkg --configure -a
``` it says: dpkg: requested operation requires superuser privilege

When I type sudo and the code it says: sudo: dpkg:: command not found

I hope somebody can help, thanks

edit misread the complete post

please run the following command and post its results

id <insert_your_username_here>

---

### Post by darth_indy on 2008-06-05
I don't mean to offend, but just to make sure, you did type it out as:

sudo dpkg --configure -a

correct? Like I said, no offense, but it's always best to check the simple things that are easy to overlook at first :)

---

### Post by Oldsoldier2003 on 2008-06-05
> **darth_indy said:**
> I don't mean to offend, but just to make sure, you did type it out as:

sudo dpkg --configure -a

correct? Like I said, no offense, but it's always best to check the simple things that are easy to overlook at first :)

based on his error messages (assuming he pasted them instead of manually typing them into his post) It looks like either he has managed to uninstall dpkg or doesn't have the proper permissions set. There are also some other explanations (including typoed commands) so we'll have to work through the possibilities and rule them out before we can fix the root of the problem with the package manager

---

### Post by Oldsoldier2003 on 2008-06-05
to the OP,
please see if dpkg is installed,and its version

apt-cache policy dpkg

---

### Post by HaemoLacria on 2008-06-06
It says: Setting up libc6 (2.6.1-1ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

when I type it manually. Nothing seems to happen actually

---

### Post by django0909 on 2008-06-06
*invalid post* :D

---

