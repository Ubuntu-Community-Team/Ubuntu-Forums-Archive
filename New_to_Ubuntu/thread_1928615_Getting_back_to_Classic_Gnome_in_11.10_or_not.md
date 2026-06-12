---
title: "Getting back to Classic Gnome in 11.10 or not???"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-02-20
CharlesA posted a thread on how to do this, and it worked great on my last install. He says to simply:

sudo apt-get install gnome-session-fallback
Reboot and then select "Gnome Classic" on the login screen.

Unfortunately I get this result from the terminal: 

josh@josh-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get install gnome-session-fallback
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-fallback is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not
josh@josh-Compaq-Presario-CQ60-Notebook-PC:~$

but when I turn on the computer it goes straight into unity and does not give me an option? Could this be because my laptop is setup to load automatically into my profile?

---

### Post by philinux on 2012-02-20
> **theducksfan2010 said:**
> 

but when I turn on the computer it goes straight into unity and does not give me an option? Could this be because my laptop is setup to load automatically into my profile?

If you've got auto login then yes thats why.

---

### Post by theducksfan2010 on 2012-02-20
How do I change it to require password to login?? 

Also how do I change to Gnome from inside Unity??

---

### Post by blueshead on 2012-02-20
> **theducksfan2010 said:**
> How do I change it to require password to login?? 

Also how do I change to Gnome from inside Unity??


Sytem Settings/User Accounts

After you log back in open up the cogwheel icon and select gnome classic..

---

### Post by theducksfan2010 on 2012-02-20
You guys rock! Thank you so much, thread is solved.

---

