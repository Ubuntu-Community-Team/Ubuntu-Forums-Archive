---
title: "samba and shorewall 4.5"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by duceduc on 2012-02-20
I have upgraded my shorewall to 4.5 and now my samba will not work. I am unable to see my network from my other pc. Looking at the [doc at shorewall.net](http://www.shorewall.net/samba.htm). It says we need to apply some rules; however, I am not sure where to apply the second set of rules containing z1.

---

### Post by Gone fishing on 2012-02-21
Is this a server? If it is Webmin has a module for controlling shorewall. If this is a personal PC maybe Shorewall is a bit of an overkill and you might be better off with Firestarter, which is a GUI frontend for IP tables [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

---

### Post by duceduc on 2012-02-21
This is for a server (11.10). That link I provided says to put the rules in the rules file. It is not working though. I know it is shorewall that is blocking it. If I shutoff shorewall completely, samba works

---

### Post by Gone fishing on 2012-02-21
I'd have a look at Webmin and the shorewall module, I've used the Webmin linux firewall module that helps writing rules for IP tables and it was quite simple.

---

