---
title: "How can i configure public ip"
date: 2018-09-05
forum: New to Ubuntu
---

### Post by asdreni on 2018-09-05
I want to configure public ip in my Ubuntu 18.04.1 LTS bionic
I connect my ubuntu PC in mikrotik router with Ethernet cable. In mikrotik i've configured public ip which is 185.192.164.121/29, and dhcp pool 192.168.88.1 Now my ubuntu have local ip 192.168.88.12
How can i configure my public ip in ubuntu to connect/access from everywhere.
Thank you in advance!

---

### Post by SeijiSensei on 2018-09-05
Short answer is you cannot.

If you have a router in front of the machine, you must forward traffic from it to the target machine using "port forwarding."  So, for instance, if you wanted to support remote SSH connections to the machine, you need to have port 22 on the router open, and a rule in the router's software to forward that traffic to port 22 on the destination machine.

The whole point of the router is to block incoming traffic from seeing any of the machines behind it unless specific exceptions are put in place in the firewalling rules.

The methods to set this up vary from router to router, so you'll need to consult the Mikrotik documentation.

---

### Post by sporksrule on 2018-09-05
You might want to consider using DDNS: [https://www.noip.com/](https://www.noip.com/)

---

