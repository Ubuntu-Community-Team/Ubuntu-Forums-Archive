---
title: "Outgoing IP Packages"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by eldoctor on 2008-05-03
Hi this is my first post here!! Great forum btw, lots of information ^^
Well the problem is this:

I want to know the amount of outgoing IP packages on my PC, is there any command that shows this?? or a file in the /proc directory that shows this kind of information??

Thanks!!

---

### Post by schwascore on 2008-06-28
wireshark is a great network sniffer that will allow you to do this.  It's in the repositories.

---

### Post by svk on 2008-06-28
Depending on what exactly you mean, you may find the System Monitor applet to be useful.  If you're using Gnome, right click on the panel, select "Add to panel", and look for "System Monitor".  When it shows up in the panel, right click, select "Preferences", and check the box next to "Network".

---

### Post by jordanmthomas on 2008-06-28
cat /sys/class/net/**eth1**/statistics/tx_packets

where eth1 is the interface you want to check.

---

