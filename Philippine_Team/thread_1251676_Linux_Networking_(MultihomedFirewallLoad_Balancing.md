---
title: "Linux Networking (Multihomed/Firewall/Load Balancing/etc...)"
date: 2009-08-27
forum: Philippine Team
---

### Post by kiminaiseah on 2009-08-27
hello, everyone ask ko lang lang sana kung sino fanatic ng shorewall dito? me kaunting katanungan lang sana ako... una sa lahat madali lang mag configure ng shorewall sa loob ng linux and its derivatives. at madaling magconfigure ng inbound and outbound routing and balancing, kaso may kaunting sabit sa outgoing balancing kasi for example in my case one linux router connected with 4 major isp providers for high traffic outgoing connection kaya apat sila kasi load balanced round-robin scheme. kaso ang problema pag isa sa mga gateway sa mga apat ng provider hindi na distinguished kung buhay pa yung route sa certain gateway so included pa siya sa routing table ng network. in this case sempre load balanced round robin may papasok na outgoing doon sa gateway na patay ang kalalabasan nito no connection kung sino man yung nag browse na yun.. any ideas paano ito ma iresolba.. 

sinubukan ko yung concept ni taragana dun sa sinasabing nyan gwping, effective naman pero hindi accurate mag palit ng routing table at supported nya lang dalawang isp providers, 

sinubukan ko rin ang freebsd which nabubusy na ako sakanya ngayon which me advantages sya versus linux in the way of networking and stability.. sinubukan ko dito same concept nung shorewall multi-wan + taragana gwping concept, at flawless ang resulta accurate parang naka appliance router or switch ang quality.. 

any ideas?

---

### Post by jmazaredo on 2009-09-01
use vyatta

---

### Post by kiminaiseah on 2009-09-03
same as ubuntu, vyatta is also debian child distro.. hehehe

thanks anyway, na provoke ako gumawa ng script hehehe

---

