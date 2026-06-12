---
title: "SNMP Agent"
date: 2008-03-21
forum: Programming Talk
---

### Post by neugen on 2008-03-21
Hi guys ! I would like to write in C a  SNMP agent.Can anyone  help me please by supplying some web links about snmp programming ? 
   Thank you !

---

### Post by supirman on 2008-03-21
You'll need to use the net-snmp library.  They have some tutorials on their site ([http://www.net-snmp.org/wiki/index.php/Tutorials](http://www.net-snmp.org/wiki/index.php/Tutorials)).  Near the bottom is a section for snmp agent coding tutorials.

---

### Post by schmendrick on 2008-09-25
can anyone recommend a good book on SNMP for developers? 

i am a bit indecisive on which to take...


my aim is to write an SNMP agent for the project i am doing at work, and most books seem to be written for network administrators.

some more info:
the agent i will write is in c++. basically i do not plan to use use net-snmp. at the moment i am thinking of using Agent++.

---

### Post by dwhitney67 on 2008-09-25
> **schmendrick said:**
> ...
 at the moment i am thinking of using Agent++.
You are on the right track!

If your company needs help, send me a PM.

---

### Post by schmendrick on 2008-10-02
thanks dwhitney67, but if i recommend the company to get external help they will ask why they need me  ;)

and agent++ seems really cool. without any real knowledge and about 40 lines of code i was able to create an agent with 2 dynamically changeable properties that can be read in an snmp manager. 

as for the book, for anyone interested i now decided on

"Understanding SNMP MIBs" by "David T. Perkins". 

after much search on the net. 

unfortunately like i already said, the books out there are mostly for network administrators, but that book also seems fine for my needs as an agent writer.

---

### Post by dwhitney67 on 2008-10-02
> **schmendrick said:**
> thanks dwhitney67, but if i recommend the company to get external help they will ask why they need me  ;)

and agent++ seems really cool. without any real knowledge and about 40 lines of code i was able to create an agent with 2 dynamically changeable properties that can be read in an snmp manager. 

as for the book, for anyone interested i now decided on

"Understanding SNMP MIBs" by "David T. Perkins". 

after much search on the net. 

unfortunately like i already said, the books out there are mostly for network administrators, but that book also seems fine for my needs as an agent writer.

Maybe you "contacted" a different group than I did.  Agent++, if memory serves me right, was developed by HP, and is free (GPL or whatever nonsense).  Their site is [here]("http://www.agentpp.com/").

One of my colleagues at the time, improved on the Agent++ design, but that was back in 1999.  Presumably the design has changed since then.

The HP effort is a sound design, thus obviating the need for individuals to redesign something new.  SNMP is not that difficult, but its acceptance in technological "toys" has been.  This it is not widely used.  One area of usage is in Network Operation Centers (NOCs), which are used to managed one ore more satellite systems.

---

### Post by schmendrick on 2008-10-03
> **dwhitney67 said:**
> Maybe you "contacted" a different group than I did.  Agent++, if memory serves me right, was developed by HP, and is free (GPL or whatever nonsense).  Their site is [here]("http://www.agentpp.com/").


not quite. SNMP++ was created by HP, while Agent++ is based upon the SNMP++ library, it is not done by HP. To use Agent++ you will need SNMP++ though.

---

