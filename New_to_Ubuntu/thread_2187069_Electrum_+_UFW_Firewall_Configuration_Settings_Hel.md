---
title: "Electrum + UFW Firewall Configuration Settings Help?"
date: 2013-11-10
forum: New to Ubuntu
---

### Post by linuxguru43 on 2013-11-10
Hello. I'm running ubuntu 13.10 and I have installed Electrum Bitcoin Wallet. I'm trying to configure the UFW settings correctly.  Here are my current UFW settings (see attached pic)   It still gives me a red light and won't connect to the server.  I have openned port 50001 but it still won't connect until I disable ufw.   How do I open the ports for this software correctly at CL for UFW?   Any suggestions would be kindly welcomed.

---

### Post by Frogs Hair on 2013-11-10
I would start here until a more familiar user responds. I haven't had to open specific ports for specific programs before.  

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by linuxguru43 on 2013-11-10
Nevermind. I figured it out. The solution was to install GUFW and then click on Edit and Reset Configuration. Electrum works now and recieves a green light that it has successfully connected to the server on port 50001. Closing Thread.

---

