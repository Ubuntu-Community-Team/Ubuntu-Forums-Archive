---
title: "[SOLVED] Network Printer Hangs on networked laptops"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by edog76 on 2008-08-06
I have an HP Laserjet 5P wired to a desktop running Hardy. I have successfully printed from the desktop with no problem. I selected the share printer option, and both my laptops (one running OS X and the other Hardy) detect the printer when connected to my wireless network. However, if I try to print to the printer, both laptops will hang up (spinning beach ball of death for one and nothing on the other).  What's going on here and how do I fix it?

TIA

I'm currently monitorless on the desktop (though I should have that rectified in the next couple days).

---

### Post by edog76 on 2008-08-08
Bump

---

### Post by bdfoster on 2008-08-08
This might have something to do with it. 

UNSHARE the printer. There is no need to share it. It is already on the network. Try that first.

---

### Post by edog76 on 2008-08-09
Unsharing the printer makes it invisible to the laptops.

---

### Post by berksted on 2008-08-09
Are you running a firewall (e.g. Firestarter) on the desktop? I had a similar problem and it turned out to be the firewall settings.

---

### Post by edog76 on 2008-08-09
Yes, I am running firestarter on the desktop. Can I change some settings and still keep firestarter running?

---

### Post by berksted on 2008-08-09
Stop the firewall on the desktop and test to see if you are able to print from the other computers. If that works, then add a rule under the policy tab that allows inbound traffic from the other computers IP address or host name and restart Firestarter. Hopefully that will work.

---

### Post by edog76 on 2008-08-09
That was it. Thank you very much!

---

