---
title: "Help with installing flash"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by HumanSancho on 2008-10-28
Im new to Ubuntu. Im trying to install flash player on ubuntu 8.04.
I tryed a few things with no avail and now im trying to install it
through terminal using "sudo apt-get install flashplugin-nonfree".
But now when i try to run it I get this:


michael@computer:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for michael: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
michael@computer:~$ 

I want to know what i did wrong. Any help would be wonderful.

---

### Post by bumanie on 2008-10-28
Looks as though you may have synaptic or add/remove open at the same time as trying to input terminal commands - only one package manager is allowed open at the one time.

---

### Post by abeisgreat on 2008-10-28
Yep, something is definately locking that. Are you running the system updator or installing other programs? if your not try restarting.

---

### Post by HumanSancho on 2008-10-28
I'll try what you said but i already restarted and theres was nothing open
when I ran terminal.
thanks

---

### Post by abeisgreat on 2008-10-28
so your still having issueS?

---

