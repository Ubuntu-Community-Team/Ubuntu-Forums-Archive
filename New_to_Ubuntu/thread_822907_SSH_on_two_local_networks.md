---
title: "SSH on two local networks"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by cane1832 on 2008-06-08
Ok so im running into difficulty trying to connect computer to computer on two local networks. Maybe there is something im overlooking but when i try to connect it gives me Name or Service not know. Log in command im using is : ssh XXX.XXX.XXX.149:2222

 Modem
   |
Router 1 - ssh -2222  
   |
Router 2 - ssh 22

Since both computers are running ssh one is on port 22 and the other 2222 
for port forwarding. So im lost i don't know why i can't connect internally.

All suggestions appreciated.

---

### Post by Rocket2DMn on 2008-06-08
It helps to have one router act as the DHCP server and the other router act as a gateway/switch.  This way you only have to configure one router in your network to forward ports.  
With your current setup, you want to access the IP of the router that has the SSH server on it that you are trying to contact, and use that server's port to connect.

---

### Post by cane1832 on 2008-06-08
I have both of them as dhcp gatways for security purposes.
can't change that

---

### Post by Rocket2DMn on 2008-06-08
It sounds like you need to setup Port Triggering on your routers so that you can forward specific ports on one router to specific ports on the other.  How you go about this depends on the specifics of your network setup and router make/models.

---

### Post by cane1832 on 2008-06-09
not to sure what port triggering would do how it would be setup

---

### Post by Rocket2DMn on 2008-06-10
Port triggering allows you to access a port or range of ports from an outside location (like the web) and have your router accept those ports but talk to a machine on your network on different ports (rather than just passing the ports through with port forwarding).  Wikipedia has a little info on it - [http://en.wikipedia.org/wiki/Port_triggering](http://en.wikipedia.org/wiki/Port_triggering)

How you go about setting it up depends on your router make/model.  You should reference the documentation for that.  If you don't have a physical copy, googling your router's make/model should help you find the manufacturer's website where they likely have .pdf copies available for download.

---

### Post by cdtech on 2008-06-10
Why would you need to do any port forwarding? Isn't the IP address enough to determine which computer connects via ssh? And are you able to ping the computer via the IP address?

---

