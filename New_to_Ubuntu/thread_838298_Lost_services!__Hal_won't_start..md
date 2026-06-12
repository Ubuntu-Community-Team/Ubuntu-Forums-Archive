---
title: "Lost services!  Hal won't start."
date: 2008-06-23
forum: New to Ubuntu
---

### Post by sattruckmark on 2008-06-23
Running Gutsy for 6 months without many problems and learned to love it!  After a recent update I started getting a error whenever I attempted to install/uninstall anything: "Boa is trying to use port 80, another service is already bonded to port 80, please correct". 

So... I committed a newb mistake.  I started checking/disabling services, and accidentally killed one of them that I obviously needed... I've lost wifi and usb.  I can't even shut it down normally.  On startup I get "Hal can't initialize" in a small box then the desktop loads.  When I try to go to "Administration -> Services" I get a "You can't access this/You don't have permission" error.  I get the same error when I try to open pretty much anything in "Administration".  I did try to "sudo /usr/bin/services-admin" but it gives me the same error.  

I've had to load up my XP on dual boot for the first time in 4 months to write this.  I hate widows.:mad:

Please help me guys!  Things were going fine till I did something stupid.

---

### Post by sattruckmark on 2008-06-23
A shameful bump.:(

---

### Post by shae on 2008-06-23
I bet you disabled dbus or hal, both would cause MAJOR issues.  Unfortunately I am not sure how to re-enable them from comandline when you disable them the way you did.  Stay patient, perhaps someone else knows.

---

### Post by sattruckmark on 2008-06-24
Solved:  After some reading... A lot of reading... and trial and error.  I found this to work:  

sudo /etc/init.d/dbus start

So simple.  All is well now.

---

