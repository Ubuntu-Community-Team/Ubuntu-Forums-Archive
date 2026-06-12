---
title: "a problem with vpnc"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by x88a on 2008-05-30
i am trying to run vpnc on my Ubuntu 8.04.
each time i type "sudo vpnc" in the terminal, i get this message:-
vpnc: no response from target

in my uni, i can connect to vpn.
but at home, i get this problem

pls help
tq

---

### Post by quelx on 2008-05-30
If you are sure you are connected to the Internet, then it looks like vpnc is trying to ping the hostname of your university's vpn server and failing.  There should be an option to disable ICMP (or pings) to check that the hostmachine is available.  Try disabling that and connecting.

---

### Post by x88a on 2008-05-31
> **quelx said:**
> If you are sure you are connected to the Internet, then it looks like vpnc is trying to ping the hostname of your university's vpn server and failing.  There should be an option to disable ICMP (or pings) to check that the hostmachine is available.  Try disabling that and connecting.

how do i do that?

tq

---

### Post by x88a on 2008-06-01
anyone else can help me?

---

