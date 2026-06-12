---
title: "How to configure BitTorrent and/or Transmission"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by nightwatch1954 on 2008-07-24
I have DSL (Actiontec router/modem). Need to figure out port setting and am apparently clueless. Browser connects to internet with no problem. When I try to download a torrent it seems that ports are closed. Suggestions would be appreciated.

---

### Post by RomeReactor on 2008-07-24
Hi. Enter **192.168.0.1** as the address in Firefox; look around for firewall settings so you can open port **51413** for Transmission or ports **6881** through **6889** for BitTorrent.

---

### Post by cozmicharlie on 2008-07-24
This should help [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

Your router is in the list so it should have step by step instructions that will walk you through the entire process.  Post back if you have problems or you aren't sure how to do something.  

Enjoy

---

### Post by prshah on 2008-07-24
> **nightwatch1954 said:**
> I have DSL (Actiontec router/modem). Need to figure out port setting and am apparently clueless. Browser connects to internet with no problem. When I try to download a torrent it seems that ports are closed. Suggestions would be appreciated.

If you are using Transmission, you should enable uPnP mode; this will automatically make the port opening adjustments.

Note that, especially in Transmission, uPnP port adjustments take some time to make/take effect. Start transmission, wait about 2~3 mins (not more than 5) then check the port state in Edit-Preferences. You can also check if uPnP is enabled from the same location.

---

### Post by El Conquistador on 2008-07-24
> **cozmicharlie said:**
> This should help [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm)

Your router is in the list so it should have step by step instructions that will walk you through the entire process.  Post back if you have problems or you aren't sure how to do something.  

Enjoy

Yeah go to that website find your router then it will tell you step by step how to configure it so that it allows you torrents to flow freely. 

Also make sure if you have a firewall running make sure to add the rules so that it opens up the ports. either that or turn it off (not recommended)

---

### Post by hyper_ch on 2008-07-24
> **RomeReactor said:**
> Hi. Enter **192.168.0.1** as the address in Firefox;

Why this address?

---

### Post by RomeReactor on 2008-07-24
> **hyper_ch said:**
> Why this address?

Going by Actiontec's [official documentation]("http://www.actiontec.com/support/product_details.php?pid=71&typ=all#q8"), most of their DSL modem/routers have this address. It could also be 192.168.1.1.

---

### Post by hyper_ch on 2008-07-24
or it could be another private ip range one ;)

---

