---
title: "Some keys on keyboard not working"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by utuser on 2012-03-21
New to ubuntu and like it!

Since I tried to update my software 11.1 some keys on the keyboard stopped working and then they worked again and now have stopped working...


Went through some help posts here but was unable to get anything to work- please help


this is the output I get when I try apt-get update

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Dreamer Fithp Apprentice on 2012-03-21
Anytime you get those kind of error messages about permission and so on, try the same command again, prefixed with "sudo".

---

### Post by utuser on 2012-03-21
> **Dreamer Fithp Apprentice said:**
> Anytime you get those kind of error messages about permission and so on, try the same command again, prefixed with &quot;sudo&quot;.

 thanks tried that and works!  still having the keyboard problems  

when i try to update i get this

[INDENT]W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
[/INDENT]and i am unable to run apt-get update

---

### Post by Dreamer Fithp Apprentice on 2012-03-22
Did you try "sudo apt-get update"? System error messages often take for granted the "sudo". That's probably because they are from Debian and the Ubuntu devs haven't bothered to modify them. A Debian user would probably be executing the commands from "su", i.e., the "root" account and wouldn't need sudo. Also, I believe you can do this through synaptic, settings menu, repositories. From there you can look for the duplicate entries and delete them. I don't think they do any harm though. I'm not sure how they creep in.

---

### Post by utuser on 2012-03-22
I can do sudo apt-get update, or was able to, but now the update function is acting funny  the repositories button in synaptic is unrepsponsive  and when i try to update with software manager, i get:  Not all updates can be installed  then click on partial upgrade  and i get this:  Can not Upgrade:  An upgrade from 'lisa' to 'oneiric' is not supported with this tool.  this is the same prompt i get whether i try to update in ubuntu or mint mate  and the keyboard on laptop still not working :(

---

