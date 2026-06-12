---
title: "Wireshark"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by xaegis on 2008-05-08
I just migrated from Kubuntu 7.10 to Kubuntu 8.04 x86 I love it so far but wireshark is no longer detecting any (wireless ath0 etc) interfaces. Is there anyone else wrestling with this problem? 
I need to be able to use wireshark for my cisco class so this is pretty important to me.

Any Ideas? 

Thanks in advance.

-e

---

### Post by Monicker on 2008-05-08
One bug with 8.04 is there is not a menu option to start Wireshark as root any longer.  Without root access you can't view all of the interfaces in Wireshark.  The workaround is to use the gksu command.

ALT + F2
gksu wireshark

Then you will be able to view all of the network interfaces.  You can also edit the menu and add an entry containing "gksu wireshark" to launch it.

---

### Post by xaegis on 2008-05-08
Thank You very much I will attempt this when I get home.
-e

---

### Post by nowshining on 2008-05-08
or add a menu entry with gksu in front of the word wireshark :)

---

### Post by xaegis on 2008-05-08
ok I inserted into the startup command for the wireshark icon :"kdesu wireshark"
And its working now. Thank you!
:)


Solved and closed for now!

---

### Post by wareagle on 2008-05-13
When I run it, Wireshark says "running as user 'root' and group 'root.'  This could be dangerous."

Also, the themes I have selected don't show up (as they did when I was running Gutsy.

Is there a new "safer" way of running WS with elevated, but not root privilages?

---

