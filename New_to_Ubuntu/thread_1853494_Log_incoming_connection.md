---
title: "Log incoming connection"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Tabu.it on 2011-10-02
Hi, 
how could I log all incoming connection to 2 specific port (8100 and 8101)?. I have 1 webgui on each port (8100 for Jdownloader and 8101 for Vuze webplugin).
With "grep -r -i DPT=8100 /var/log" i have no match, the same for 8101 port.

Thank you

---

### Post by 2F4U on 2011-10-02
Are you using a firewall? Logging would be included (but probably not activated) by default in the firewall.

---

### Post by Tabu.it on 2011-10-02
I use ufw but i have no log of connection on that ports. I have log only for ssh port

---

### Post by Tabu.it on 2011-10-02
> **2F4U said:**
> Are you using a firewall? Logging would be included (but probably not activated) by default in the firewall.

I read all the ufw manual and i found a command to log connection on that port

ufw allow log 8100

Now i have to write a script to avoid brute force

---

