---
title: "Hostname not reachable from Windows"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by 88keyz on 2012-01-05
I have an ubuntu 10.04 LTS server running on an ASUS P5P43TD motherboard.  The ASUS motherboard has an onboard Atheros gigabit NIC which I decided to upgrade to a dedicated Intel gigabit NIC.  The NIC installation and detection went fine but the new NIC (as expected) is detected as eth1 (onboard was/is eth0).  The new NIC has a statically assigned IP that matched the old NIC.  My server runs headless and is managed over the network via Webmin.  Using the onboard NIC I was able to browse to [http://hostname:10000/](http://hostname:10000/) to access my Webmin interface.  Once I changed the NIC to the Intel card I could no longer access the server by hostname.  The system is accessible only by IP now (ie. 192.168.1.2).  If I switch back to the onboard NIC, everything works as before, I can browse my Samba shares by hostname and connect to Webmin by hostname.  Is there anyway to make the system see the eth1 connection as the same hostname as eth0.  I tried disabling the onboard connection in the bios but the system still sees my new Intel NIC as eth1?  Linux problems like this are beyond me, my solution would be to reload the server, but that is a PITA.  Any suggestions?

---

### Post by 88keyz on 2012-01-06
Seems I found a solution.  Or at least what seems like a solution.  In the /etc/nsswitch.conf file there was a line like this.

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Seemed a little weird so I changed the line to read like this.

```
hosts: files mdns4_minimal dns mdns4
```

Now even when my server box is given an IP on either eth0 or eth1 I am able to browse it by hostname.  Worth a try for anyone else having hostname resolving issues.

On a side note, after testing with iperf the Intel NIC provides almost 100 Mbps less bandwidth than the onboard Atheros NIC (843 Mbps vs. 940 Mbps).  So much for Intel NIC's being faster.

---

### Post by CharlesA on 2012-01-06
I just checked my 10.04 box and that file says the same thing as your first post.

I have my router set up as a DNS server, so name resolution works fine.

If it works, if works, I suppose.

---

### Post by 88keyz on 2012-01-06
I'm not an ubuntu guru, I can do basics and follow instructions.  I'm not sure if that was the solution but that seems to be the only difference from what I tried yesterday when it wasn't working.  If that is not the answer and there is a more definitive answer then I'd be glad to hear it.  Based on the wide variety of hostname issues out there I'm sure other users would be glad to hear it as well.  I only posted my question because no other posts seemed related to switching from one NIC to another (and it seemed weird to me that it worked fine the second I switched back to the onboard NIC).

---

### Post by CharlesA on 2012-01-07
> **88keyz said:**
> I'm not an ubuntu guru, I can do basics and follow instructions.  I'm not sure if that was the solution but that seems to be the only difference from what I tried yesterday when it wasn't working.  If that is not the answer and there is a more definitive answer then I'd be glad to hear it.  Based on the wide variety of hostname issues out there I'm sure other users would be glad to hear it as well.  I only posted my question because no other posts seemed related to switching from one NIC to another (and it seemed weird to me that it worked fine the second I switched back to the onboard NIC).
Whatever works. ;)

---

