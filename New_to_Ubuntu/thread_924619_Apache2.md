---
title: "Apache2"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Spardra on 2008-09-19
Hello, I am having trouble accessing Apache from my public IP address I can access it fine from the private ip address but not from the public IP. Any idea why?

---

### Post by Cypher on 2008-09-19
What does your setup look like? Are you directly connecting your Ubuntu machine to the Internet or going through a firewall?

---

### Post by iansane on 2008-09-19
I think you need to set up dyndns and if it's through a router will have to open ports or set up your system IP static and set up DMZ in the router to route http requests to it

---

### Post by Spardra on 2008-09-19
It is connected to my router through my wireless Adapter, is no firewall on Ubuntu and I have the Ubuntu Machines IP DMZed from my router.

---

### Post by Spardra on 2008-09-19
Stupid me forgot to forward the ports, sorry for the trouble.

---

