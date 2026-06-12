---
title: "AWN cannot access internet"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by hammad1337 on 2008-04-27
My problem is that, the applets in AWN cannot access the internet.
Some applets, like weather, and last.fm need internet access.
Even though I m connected and everything else works fine, AWN applets cannot connect.
I use internet through an http proxy server. I m guessing maybe i have missed out on some proxy server settings, specific to AWN.
I have setup the proxy in Firefox as well as the network proxy (for system wide proxy server) still, it does not work with AWN. I also have the same problem with screenlets.

---

### Post by pieisgood4589 on 2008-04-27
> **hammad1337 said:**
> My problem is that, the applets in AWN cannot access the internet.
Some applets, like weather, and last.fm need internet access.
Even though I m connected and everything else works fine, AWN applets cannot connect.
I use internet through an http proxy server. I m guessing maybe i have missed out on some proxy server settings, specific to AWN.
I have setup the proxy in Firefox as well as the network proxy (for system wide proxy server) still, it does not work with AWN. I also have the same problem with screenlets.

Could you use DCHP instead of a proxy? That might help...

---

### Post by moonbeam on 2008-04-27
> **hammad1337 said:**
> My problem is that, the applets in AWN cannot access the internet.
Some applets, like weather, and last.fm need internet access.
Even though I m connected and everything else works fine, AWN applets cannot connect.
I use internet through an http proxy server. I m guessing maybe i have missed out on some proxy server settings, specific to AWN.
I have setup the proxy in Firefox as well as the network proxy (for system wide proxy server) still, it does not work with AWN. I also have the same problem with screenlets.

In general awn applets are not aware of how to use a proxy server.  It's a known issue though I can't say that a decision has been made on how to address it.

---

### Post by hammad1337 on 2008-04-28
does anybody know of a temporary workaround?
I m thinking on the lines of setting up a DHCP on localhost, which forwards to the proxy.
May be a solution using iptables? i dont exactly know much about iptables, but if sum1 can tell me how 2 forward packets for the internet from localhost to a proxy server, it would be apreciated.
The same workaround could also be used for screenlets.

---

