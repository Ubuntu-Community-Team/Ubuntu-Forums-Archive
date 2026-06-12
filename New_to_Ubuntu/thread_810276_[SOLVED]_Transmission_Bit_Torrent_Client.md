---
title: "[SOLVED] Transmission Bit Torrent Client"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by btermeli on 2008-05-28
Hey guys,

I use default torrent client (transmission bit torrent client) on Ubuntu. But download speed kills me its like 5 kb/s sometimes it is b/s. And I only download one by one... 

Do u know any way to make it faster???
Thanx in advance...

---

### Post by shifty_powers on 2008-05-28
use a better client? ;)

e.g. utorrent in wine, (which is what i sue), or deluge in the repo's is very popular.

plus, does your router/modem have an inbuilt firewall?

---

### Post by jjgomera on 2008-05-28
if you use router, you must open port for it

I use transmission too with good transfers, it depends too the torrent file.

---

### Post by kpkeerthi on 2008-05-28
> **btermeli said:**
> Hey guys,

I use default torrent client (transmission bit torrent client) on Ubuntu. But download speed kills me its like 5 kb/s sometimes it is b/s. And I only download one by one... 

Do u know any way to make it faster???
Thanx in advance...

Did you forward the ports from your router and/or firewall (ufw/iptables) to the port transmission is listening on?

---

### Post by Scyron on 2008-05-28
There are four steps needed to get good speeds with Bittorent.

1. Setting up a Static IP Address
2. Opening a Router Port
3. Opening a Firewall Port
4. Editing Client Prefs

Some tips in the right direction

1. System > Administration > Network > Unlock > Properties (Wireless or Wired) -- Turn off Roaming Mode, select Static IP Address under Connections Settings, and enter the data. Your Gateway Address and Subnet Mask can be found in Connection Information (from the right-click menu of your desktop network icon next to the date). For the IP address field, change the last digit of the Gateway Address (should be a 1) to something between 1 and 254. In example, a Gateway Address XXX.XXX.X.1 allows a Static IP XXX.XXX.X.193 or XXX.XXX.X.46 or whatever.

2. Go to Portforward's [Router Index Guide](http://portforward.com/english/routers/port_forwarding/routerindex.htm). Select your router from the list. Select Utorrent. Then follow the instructions EXCEPT replacing Utor1 with Unknown if you're using another client.

3. Easiest way is Firestarter. Install, Setup, go to the Policy Tab and open up the port you did in Step 2 in the Allow Services area.

4. Dependent on your client. Basically, set the max upload speed a little under your connection's capability.

---

### Post by btermeli on 2008-05-28
Thanx guys,
I share the internet  connection from my neighbour, may be I have to ask him about firewall settings. In the preferences Automatically map port is choosen and Incoming TCP port 51413 sometimes it shows like "Testing port" sometimes "Port is closed".
One more question, which website do u use for searching torrents???
thanx...

---

### Post by Joeb454 on 2008-05-28
Due to the forum codes of conduct I don't think that we can discuss any more than this. Torrenting Linux distro's - no problem, we can talk about that all day. But talking about torrenting copyrighted/illegal material is against the CoC

---

### Post by LaRoza on 2008-05-28
> **btermeli said:**
> 
One more question, which website do u use for searching torrents???
thanx...

Most of the time, you'll find torrent links from the distro pages themselves. There are a few Linux torrent trackers, but in general, I just go to the project page.

---

