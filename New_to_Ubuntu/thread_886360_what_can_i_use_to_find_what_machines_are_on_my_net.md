---
title: "what can i use to find what machines are on my network?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by leemajors on 2008-08-11
i have freenas installed, sharing up my files.

trouble is, because it uses dhcp, every time i make a change and boot up it assigns a new ip address and i have to get the monitor and keyboard out, plug it in to the freenas box and find out what ip address its using this time.

is there a command i can use that will show me what ip address it has been connected on without having to plug the monitor in all the time?

---

### Post by halitech on 2008-08-11
there was just a discussion about this the other day. check out this thread, post #2

[http://ubuntuforums.org/showthread.php?t=881714](http://ubuntuforums.org/showthread.php?t=881714)

---

### Post by decoherence on 2008-08-11
zenmap is a graphical front end for nmap, available from the repositories. You basically sepcify a host or block for it to scan then set it loose.

For instance if your address range is 192.168.1.whatever and your netmask is 255.255.255.0, you would type 192.168.1.* to see all the hosts whose IP starts with 192.168.1

---

