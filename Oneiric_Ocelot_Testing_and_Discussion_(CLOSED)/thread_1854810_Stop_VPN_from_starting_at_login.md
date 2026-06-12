---
title: "Stop VPN from starting at login"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by frailotis on 2011-10-05
Hello,

I'm currently using 11.10 Beta2 and I installed the network-manager-openvpn package.  I then imported the configuration file for my VPN and everything seems to work fine. 

Yet now I see that the VPN is started everytime I log in and I don't really want that.  I've unchecked the Connect Automatically checkbox and also the Available to all users checkbox. 

I realize that this could just be a "beta" issue, but I was wondering if anybody had any ideas on how to fix this if it wasn't.

Thanks

---

### Post by howefield on 2011-10-05
Thread moved to the development forum "Ubuntu +1 (Oneiric Ocelot)"

---

### Post by sonicb00m on 2011-10-05
> **frailotis said:**
> Hello,

I'm currently using 11.10 Beta2 and I installed the network-manager-openvpn package.  I then imported the configuration file for my VPN and everything seems to work fine. 

Yet now I see that the VPN is started everytime I log in and I don't really want that.  I've unchecked the Connect Automatically checkbox and also the Available to all users checkbox. 

I realize that this could just be a "beta" issue, but I was wondering if anybody had any ideas on how to fix this if it wasn't.

Thanks

That's hilarious because I have to build my own auto startup scripts to start my VPN every time I log in!

It's possible your configuration is set in /etc/openvpn directory and is auto loading?

---

### Post by frailotis on 2011-10-11
> **sonicb00m said:**
> That's hilarious because I have to build my own auto startup scripts to start my VPN every time I log in!

It's possible your configuration is set in /etc/openvpn directory and is auto loading?

Yes, I do realize, especially after a forum search, that I am in the minority on this issue.  :)  My wife and I share a VPN account and it's just easier to turn it on and off when needed as opposed to leaving it on all the time.  If I'm on the VPN, she can't use it...one of those deals.

Anyway, I just moved the config files from /etc/openvpn to my home folder and now everything works as it should.  Thanks for your help sonicb00m!

---

