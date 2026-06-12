---
title: "ufw rationale for blocking ip addresses"
date: 2016-09-22
forum: New to Ubuntu
---

### Post by mafialord on 2016-09-22
What criteria does ufw follow while blocking certain ip addresses on its own. The reason I am interested is that our squid server has recently started crashing recently on a regular basis. After investigation we realized that, certain IP's were constantly being blocked by ufw on a regular basis. We also realised that after a certain point of time squid crashed. To remedy this we blocked the ip addresses by adding them to the rules in the iptables.  We also blocked associated mac addresses. That seems to have helped since our server hasn't crashed now for a day:o. I did not find anything on the ufw FAQ which says why certain traffic is blocked on its own by ufw. I would grateful if anybody can provide me the answer for the same

---

### Post by mcduck on 2016-09-23
As far as I'm aware, none. UFW doesn't come up with any kind of rules on it's own, it only controls traffic based on the rules you give it. So if you had UFW blocking some IP, it would have been because of some rule you've added to UFW.

(also you are saying that you solved the problem by blocking the addresses, which kind of seems to contradict the idea that addresses being blocked by UFW could have been the issue in the first place?)

Edit: You might want to post the rules you are using here (or in the security subforum) if you want somebody to be able to say what could be the problem.

---

### Post by Kris_M on 2016-09-24
It's my understanding that UFW is built in to 16.04.1 and comes with a default set of iptables, figured out and set up by Canonical, assuming you use the default Incoming Deny, Outgoing Allow. That are activated once you enable UFW.  They are supposed to be good for a home end user.

---

### Post by mcduck on 2016-09-25
those rules are just basic setup you can be assumed to want if you enable a firewall in the first place. So no filtering based on IP or MAC at all, simply "deny all incoming connections & allow all outgoing connections". So using those, UFW will definitely not "block certain IP addresses on it's own".

---

### Post by mafialord on 2016-09-25
No, what is happening is that we allow outgoing and incoming tcp connections as well as ssh connections. So with these rules certain Ip addresses repeatedly show up in the block list. After 15 minutes or so squid crashes and we cannot ssh into it. The moment we add the Ip addresses in the block list, squid doesn't crash till some other IP starts doing the same. Thus my question is on what basis does UFW block these offending IP addresses

---

