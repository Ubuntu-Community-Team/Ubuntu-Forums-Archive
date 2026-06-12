---
title: "Set up Nameservers for GoDaddy?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by justinram22 on 2008-11-29
Ok, im confused as to how this all works (sorry if this is the wrong forum for this!). Basically i just bought a domain from [www.godaddy.com](www.godaddy.com) .  They require to "NameServers".  I'm running apache off of a old desktop i have and would like to use the desktop as my web server.  I have set up 2 DNS things (what ever you want to call them) pointing to my IP address from dynDNS.com  When i put them into the nameserver spot on godaddy, it just says "Nameservers not registered"  Sorry, but i have spent the past 3 hours looking at this, any and all help is greatly appreciated!!!!

---

### Post by Xiong Chiamiov on 2008-11-29
DynDNS will take care of all of the DNS routing.  If you go to Add Zone Services, you can transfer your domain to them and have it pointing at your computer.

---

### Post by justinram22 on 2008-11-29
Is there a free way to do this? Because dynDNS wants $52 to do it? Is there a different way? Thanks for any help

---

### Post by scribbles on 2008-11-29
For what you need it to do DynDNS is actually free. Poke around the site and you'll see. The other part is that you will need a client to update the DynDNS server every time your IP changes, that client is ddclient among others. You can find the guide to set all of this up [HERE]("https://help.ubuntu.com/community/DynamicDNS").

---

