---
title: "game servers and firewalls"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-09
i have a bunch of games that i recently downloaded

(AssaultCube, Nexuiz, OpenArena, Sauerbraten, and Warsow)

all of theese games work awesome 

the only problem is that i cant connect to any servers in any of theese games

some have a list of IP's that it is trying to connect to, but it just says waiting for response and it never gets one

others just dont have anything in the list at all

and at the same time other games connect fine, like Spring or  (NVM i guess spring is the only one that connects)


i am using hardy and i have firestarter installed   

also i am connected through a firewalled router  

so basically my question is,  how do i know what ports i should open up?

also is there some way of adding servers to the lists if theese wont work?

---

### Post by nowshining on 2008-07-10
stop the GUI/iptables firewall and try again, this lets us know which is most likely blocking the ports, etc.. either the router or software firewall. [color=#FFFF66]:)[/color]

---

### Post by tjwoosta on 2008-07-10
> stop the GUI/iptables firewall and try again, this lets us know which is most likely blocking the ports, etc.. either the router or software firewall. 

sounds like a good idea, but how do i do that?

---

### Post by Fire_Chief on 2008-07-10
To disable the default firewall in 8.04 (Hardy)```
sudo ufw disable
```

---

### Post by tjwoosta on 2008-07-10
> To disable the default firewall in 8.04 (Hardy)


sudo ufw disable



thanks

can i use sudo ufw enable to turn it back on?

---

### Post by Fire_Chief on 2008-07-10
Yup, all the options for ufw are available by looking at the help.
```
sudo ufw --help
```

:)

---

### Post by Fire_Chief on 2008-07-14
Did you ever get the original problem resolved (connecting to game servers)?

---

### Post by tjwoosta on 2008-07-14
no, sorry,  ive been distracted 


i will try though tonight when i get home and post back

---

### Post by tjwoosta on 2008-07-16
hmm.. well i cant figure it out


i tried disabling the firewall on both ubuntu and on my router but nothing seems to work


i think im just gonna give up on multiplayer

---

