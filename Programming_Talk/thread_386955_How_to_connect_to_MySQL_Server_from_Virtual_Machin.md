---
title: "How to connect to MySQL Server from Virtual Machine?"
date: 2007-03-17
forum: Programming Talk
---

### Post by HighD on 2007-03-17
Hello! 

I need to connect to MySQL Server (installed on my Ubuntu box) using a Virtual Machine running a Windows XP Guest OS (of course on the same Ubuntu box). What do I need to do this? I can currently share files between host and guest using the VMWare provided tool. Is that enough? Do I need to build a network? How can I make this possible?

Please ask as much as you want. Thanks in advance for your anwers! :)

---

### Post by MikeDX on 2007-03-17
This wil be down to two things

1. Firewall permissions on the host maching - make sure the mysql port is accessible across the local network

2. Make sure that the mysql databases user settings allow your user to connect from the ip of the guest machine

Also its worth considering that you will get the best results using the virtual bridge network, this makes the guest effectively on the same lan subnet as the host (dependant on dhcp of course)

---

### Post by HighD on 2007-03-17
> **MikeDX said:**
> 

This wil be down to two things

1. Firewall permissions on the host maching - make sure the mysql port is accessible across the local network



How do I figure which port is MySQL server using?

Thanks MikeDX! :mrgreen:

---

### Post by MikeDX on 2007-03-17
I believe the default port is 3306. netstat may yield more information...

---

