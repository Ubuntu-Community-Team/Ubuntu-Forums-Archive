---
title: "HELP NEEDED... other alternative to virtual box"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by afbuntu on 2008-11-11
although i have converted to linux (ubuntu) i still need some windows application for my work. so i search for linux app that allow me to run windows virtually and found virtual box. i manage to install virtual the app correctly but after i install windows xp its crashes so many time even when i was in the middle of work. 

1. what is the best app for work environment?

2. i've heard of wine. they say its more reliable. how do you install it?

all reply is much appreciated.

---

### Post by Zack McCool on 2008-11-11
> **afbuntu said:**
> although i have converted to linux (ubuntu) i still need some windows application for my work. so i search for linux app that allow me to run windows virtually and found virtual box. i manage to install virtual the app correctly but after i install windows xp its crashes so many time even when i was in the middle of work. 

1. what is the best app for work environment?

2. i've heard of wine. they say its more reliable. how do you install it?

all reply is much appreciated.


Wine is not a virtualized installation.  It is good at emulating Windows for many things, but it will not run all Windows apps.  To install it, simply search for wine in Synaptic Package manager and install it.

As to the virtualization, VirtualBox should work fine.  If you are not having luck with it, you could try VMWare Server, though it is not in the Repos.  Go to VMWare.com, get a free license, and download the installer.

It is a little more complex to set up than VirtualBox, though...

---

### Post by afbuntu on 2008-11-11
i have manage to install wine correctly. you're right. i does difficult to configure. i want to install windows office but cannot. why?

---

### Post by afbuntu on 2008-11-11
i would appreciate if the is wine manual available for easy reference.

---

### Post by cariboo on 2008-11-11
If you really need to use office I would suggest going here:

[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

and purchasing Crossover Linux. This product will walk you through installing MS Office.

Jim

---

### Post by afbuntu on 2008-11-11
thanx. i really appreciate it. i will try it. its the software supplied by my office so i have to use it.

---

### Post by Zack McCool on 2008-11-11
> **afbuntu said:**
> thanx. i really appreciate it. i will try it. its the software supplied by my office so i have to use it.

On your home or office PC?  If it is home, you should be just fine running OO.  It reads and writes MS Office files fine...

If you really do need MS Office, Crossover is the best way to go...

---

### Post by bodhi.zazen on 2008-11-12
As an alternate to VirtualBox you could consider VMWare.

VMWare server is freely available.

---

### Post by Karilex on 2008-11-12
I know this seems really obvious but have you tried dual booting?
If not for the wine manual just go to application>accesories>terminal and type in man wine.

---

