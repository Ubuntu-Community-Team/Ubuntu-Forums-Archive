---
title: "Running programs at startup"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by mr-woof on 2008-10-23
Firestarter isn't starting automatically when ubuntu starts up, any ideas on how i can this and other programs to start up automatically?

---

### Post by Sarmacid on 2008-10-23
Search in System->Preferences->Sessions, there you can add anything you want to start when you log in.

---

### Post by oldos2er on 2008-10-23
> **mr-woof said:**
> Firestarter isn't starting automatically when ubuntu starts up, any ideas on how i can this and other programs to start up automatically?

 Why do you need Firestarter to start automatically? Usually you'd use it to change settings for iptables once, and wouldn't need to run it again.

---

### Post by prematurebaby on 2008-10-23
Yeah do sessions I wont question your logic in Firestarter to start automatically.

---

### Post by tuxxy on 2008-10-23
Also its discontinued and should be using ufw really and there is GUI's available if you like that kind of thing =p

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

---

### Post by mr-woof on 2008-10-24
so use ubuntu firewall instead of firestarter? Sorry i'm still in windows xp mode :)

---

### Post by porchrat on 2008-10-24
mr-woof what they are trying to tell you is that firestarter is not a firewall.

Firestarter is a program that alters a table called iptables. 
 
Iptables is a routing table that decides which ports are open, which ports are closed and basically decides where each connection should go (it is similar to the concept of a firewall under windows).

Once you have used firestarter to give iptables the instructions once (i.e. told it to open the ports you need etc.) you don't need to start firestarter again as iptables starts everytime and IT does the actual protecting.

iptables also remembers what firestarter has told it and so firestarter doesn't need to be started again unless you need to give a new instruction (called a rule) to iptables.

I hope this clears up any confusion.

---

