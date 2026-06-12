---
title: "Port Fowarding"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by worthawg on 2008-11-15
I installed Joint Operations on 8.04 LTS and get a code nwec 15 within the game when I try to Play on line online. I forwaded The ports I need within the router and established a static IP adress using system> admin > network. Is there anything else I need to do in UBUNTU for port forwarding

---

### Post by Mardoct909 on 2008-11-15
Are you running a firewall?

---

### Post by worthawg on 2008-11-15
No firewall. I can connect to the internet through firefox and I can send and recieve e mail

---

### Post by MasterSander on 2008-11-15
That doesn't mean you don't have a firewall.

---

### Post by Mardoct909 on 2008-11-15
Things like email and web browsers are automatically setup to be able to get through the firewall. Online play? Not so much.

---

### Post by Tomatz on 2008-11-15
> **worthawg said:**
> I installed Joint Operations on 8.04 LTS and get a code nwec 15 within the game when I try to Play on line online. I forwaded The ports I need within the router and established a static IP adress using system> admin > network. Is there anything else I need to do in UBUNTU for port forwarding

Are you running it in wine?

---

### Post by worthawg on 2008-11-15
Yes running it through wine


If I unknowingly have a firewall up how can I determine that? I am a total noob here

---

### Post by InfectedWithDrew on 2008-11-15
You've made sure that your Network Manager has you connecting using that static IP address?

If so, try using a free, online port-checking tool, such as [http://www.canyouseeme.org/](http://www.canyouseeme.org/)

Personally, I've never gotten Ubuntu to accept a forwarded port.  But checking to see if the basic process was done right is the first step, so make sure that:
[LIST]
[*]Your router has that correct port forwarded.
[*]That port is forwarded for the static IP address you have chosen (i.e. 192.168.1.xxx, xxx being something like 130).
[*]You have set the Network Manager to connect to your specific wireless network with that static IP address.
[*]Your router accepts static IP addresses in that range that you have specified (some routers will not take more than x number of addresses).
[*]You have no firewall software running.
[/LIST]

---

### Post by Mardoct909 on 2008-11-15
Networking in WINE is rather... Well, games are a better idea in a real Windows install anyways.

---

### Post by worthawg on 2008-11-16
I tried a few of those port checking sites like you suggested and it seems all the ports I tried to test are blocked including ports like 80,25 110. Is there online tutorial I can walk myself through on this matter?

---

### Post by nu2this2 on 2008-11-16
> **worthawg said:**
> I tried a few of those port checking sites like you suggested and it seems all the ports I tried to test are blocked including ports like 80,25 110. Is there online tutorial I can walk myself through on this matter?



Try-----------www.portforward.com

---

### Post by worthawg on 2008-11-17
> **nu2this2 said:**
> Try-----------www.portforward.com

   Already went there and set up the router, I think I my have missed something in UBUBTU itself

---

### Post by worthawg on 2008-11-17
BTW I tried the port checking sites when in windows and tried the ports I forwarded and I KNOW work and these port checking sites still say the ports are blocked!
   I think those sites are BS and they are just trying to sell there software!


   So can ANYONE help me to ensure I did it correctly within UBUNTU?

---

