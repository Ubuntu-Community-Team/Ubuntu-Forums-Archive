---
title: "Need help in setting up VPN Server"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Tech4rce on 2008-09-03
Hi, just wondering if anybody out there can help me out? 
I have a Ubuntu 7.10 Server (no GUI) running as a Router/DHCP/Firewall (Iptables) now I would like to set up a VPN on this machine (I need access to a Windows Machine on the LAN).

I'm using PopTop as the VPN, I believe I configured it properly (Remote IP address from DHCP - 20 users).  Each time I try to connect from work (to Home) from a Windows machine, the connection fails.  I believe it's my Iptables firewall (maybe?).  I have port 22 open for maintenance (I can connect remotely no problem).

Is there a "How-to" or a site that will walk me through??

Oh I have people who want to connect to this server and they use "Mac/Apple" machines, so I hope ppp will work (once I fix this).
Thanks for reading.

---

### Post by RealPSL on 2008-09-06
You can try these two (2) from the documentation site:

[OpenVPN]("https://help.ubuntu.com/community/OpenVPN")
[Open VPN Client]("https://help.ubuntu.com/community/OpenVPNClientMiniHowto")

---

### Post by The Cog on 2008-09-06
+1 for OpenVPN.

---

### Post by Tech4rce on 2008-09-06
Hey I got the dam thing up and running.  Yep it was my firewall, fixed that now it works.  Now to see if Apple/Mac can connect.

Thanks for your input.

---

