---
title: "&quot;pppoeconf&quot; does not find any LAN ports"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by ronbarak on 2008-05-18
Hi,

I installed Ubuntu 7.10 on an IBM ThinkPad T43 and wanted to config it to connect to the Internet via (bezeq int) ADSL.
However, the "[FONT="Courier New"]sudo pppoeconf[/FONT]" script could not recognise any of the three LAN ports on the T43 (two real Ethernet and one on a USB adapter).

Note that the ADSL works just fine on same T43 from Windows XP.

Any ideas how can I debug this problem ?

Thanks,
Ron.

---

### Post by nicedude on 2008-05-18
try installing "pppoe" from the repositories and read the man page to see how to use it ( To load the manual page type or paste this in terminal "man pppoe") 

I use DSL with pppoe and would advise you to aquire a router and then let that handle your pppoe login to your ISP allowing you to only have to use simple networking to access your router and then the internet via ISP. A router will have built in firewall and also usually has other blocking and filtering features you can set to protect yourself and all computers on your side of connection from bad people. They are not expensive I recently saw newegg.com has both a linksys & a netgear model for $39.99US with wired and wireless networking so that is a pittance for the protection you get from it. If you get a router in future and need help configuring it just PM me and I can give you some advice on that :-) .

Hope this helps you out and have fun with your ubuntu.

---

### Post by zvacet on 2008-05-18
[this#6"]Here #6]("http://ubuntuforums.org/showthread.php?t=704585&highlight=pppoe) I hope it will work for you.

---

