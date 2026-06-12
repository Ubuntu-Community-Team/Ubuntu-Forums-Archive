---
title: "SSH to specific host within a home network without dns?"
date: 2016-10-01
forum: New to Ubuntu
---

### Post by Aphexlog on 2016-10-01
So, I have multiple ssh servers within my home network leaving me with only one external IP address. I need to know if there is a way to specify which one of the many ssh servers from my single IP that I want to access.

---

### Post by steeldriver on 2016-10-01
That would be a matter of setting up appropriate port forwarding rules on your router

---

### Post by efflandt on 2016-10-02
You would need to configure each ssh server, except one, to some port other than port 22 and specify the port when connecting (or in ~/.ssh/config of client computer) and in port forwarding on your router. For example Linux based ip-cop uses port 222 for its sshd, but you can configure sshd for most any port not being used.

---

