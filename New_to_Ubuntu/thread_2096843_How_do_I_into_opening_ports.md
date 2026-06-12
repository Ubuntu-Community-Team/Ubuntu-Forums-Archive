---
title: "How do I into opening ports"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by Kyluke on 2012-12-21
So I have just installed Ubuntu 12.10.
I do I open ports on it?
I check ufw and the firewall is off, yet I cannot access the web server even on a LAN.
Localhost works.

---

### Post by mcduck on 2012-12-21
There are no closed ports unless you have closed them yourself somehow.

Can you ping the machine from your network? If not, check the router's configuration.

And if yes, then check your web server's settings. Perhaps it's set to only allow connections from localhost?

---

### Post by 3rdalbum on 2012-12-21
> **Kyluke said:**
> So I have just installed Ubuntu 12.10.
I do I open ports on it?
I check ufw and the firewall is off, yet I cannot access the web server even on a LAN.
Localhost works.

Ubuntu does not block any ports by default.

What IP address are you using to access your computer? Check Network Manager to see your internal IP address (only computers on the LAN will be able to access your machine with that). If you are trying to access the machine with your external IP address (as reported by whatismyip.com), then you must forward the port on your router.

---

