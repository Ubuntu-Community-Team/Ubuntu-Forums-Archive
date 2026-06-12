---
title: "How can i connect to another comp using vnc if the computer is behind a router"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Kedster on 2008-11-15
ok so i want to connect to a comp, and help my friend. he has a wireless router so how would i connect to him. like umm what do i have to do

---

### Post by jimmy the saint on 2008-11-15
asking him to look into port forwarding for his router.  That way when you attempt to access his computer it will forward the connection.

---

### Post by Kedster on 2008-11-15
how would he go about doing that
and then what would i do and whot would he have to do

---

### Post by lisati on 2008-11-15
You'll need some kind of access to his network (with his permission, of course) and you'll need to know the IP address of his computer on his network.

---

### Post by Kedster on 2008-11-15
ok 1 how would i get accses to his network
2 how  do i get his IP (doesnt it change all the time) and i can get the network ip i think (using "http://www.ipchicken.com" right)
(the guys i am trying to help is a beginer)(lol so am i but i am a bit better then him)
 
3 what do i do with that info

---

### Post by Mardoct909 on 2008-11-15
> **Kedster said:**
> ok 1 how would i get accses to his network
2 how  do i get his IP (doesnt it change all the time) and i can get the network ip i think (using "http://www.ipchicken.com" right)
(the guys i am trying to help is a beginer)(lol so am i but i am a bit better then him)
 
3 what do i do with that info

With software for remote access, like the desktop sharing utility.

Ask him for it, perhaps? It' easy enough for him to get it. (Your external IP and internal one are different. You want the external one, and it is static.

This data lets you set up a remote connection to his computer so you can manipulate his computer through yours. Isn't that what you were looking for?

---

### Post by Kedster on 2008-11-15
i get the asking thing :lolflag: but like how would he get his external IP

---

### Post by jimmy the saint on 2008-11-15
I really don't mean to sound unsupportive, but this is a pretty complex task and it sounds like you may have an easier time walking him through what he needs to do.  Either way, you are going to need to walk him through getting his own ip.  
some basics are located here: [http://compnetworking.about.com/od/homenetworking/Home_Networking_Setting_Up_a_Home_Network.htm](http://compnetworking.about.com/od/homenetworking/Home_Networking_Setting_Up_a_Home_Network.htm)

and as for getting the ip in linux: [http://www.reallylinux.com/docs/admin.shtml](http://www.reallylinux.com/docs/admin.shtml)

if you have already installed rsync, then type
```
man rsync
```
in the console to find out about its specific uses, or if you are using a gui, check out its guide.  This is just too much information for someone to completely walk you through every step.

he could easily get his ip from ipchicken.

---

### Post by Kedster on 2008-11-15
so like if he goes to ipchicken then give me that ill be able to connect to him( like he has it enabled)

---

### Post by jimmy the saint on 2008-11-15
no, because you will be stopped at his router.  you need to connection to be forwarded to his machine, which will have a different ip address.

---

### Post by Kedster on 2008-11-15
ok so how do i get past his router
like  can he just do it easily or is it hard

---

### Post by m_l17 on 2008-11-15
Go to: [http://portforward.com/english/routers/port_forwarding/routerindex.htm]("http://portforward.com/english/routers/port_forwarding/routerindex.htm")

Select your friends router, in the new page select what you want to port forward. After that is setup on your friends router, then you will be able to connect to him. If you don't know what where are talking about, I suggest you read:

[http://www.portforward.com/help/pfprogression.htm]("http://www.portforward.com/help/pfprogression.htm")

[http://www.portforward.com/help/portforwarding.htm]("http://www.portforward.com/help/portforwarding.htm")

---

