---
title: "[SOLVED] Error message in synaptic and add/remove"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by misswham on 2008-07-29
I am trying to install some software and when I go to Add or Remove i find it and click when i hit install i get this message

An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


that is the one i keep getting in synaptic 


this is the one in add/remove

An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This has been happening for 2 days.  I have hit a road block.  I haven't a clue on what to do to correct this. 

Can someone pleazzze help!:(

---

### Post by lisati on 2008-07-29
You need to go to the terminal and do what it says to do, namely,
```
sudo dpkg --configure -a
```

---

### Post by misswham on 2008-07-29
I just did what u said now I got this message


You have 1 broken package on your system!

Use the "Broken" filter to locate it.


what does this mean?

---

### Post by misswham on 2008-07-29
I just did what u said now I got this message


You have 1 broken package on your system!

Use the "Broken" filter to locate it.


what does this mean?

---

### Post by misswham on 2008-07-29
Thank You.  

SOLVED

---

