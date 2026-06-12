---
title: "Samba with windows XP over Internet"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by K-Jtan on 2011-12-23
Hi,

I got a server at home running Ubuntu (11.10). I recently configure/install Samba/smb so that I could share document with my laptop running Windows. In Windows, I connecte using a Network Drive and everything works perfectly. (didn't set all the security has I should but I will do it when I get back home in January).

So now, I'm on a visite to my parents and I try to access my shared folder through Internet and it's not working. What could be the problem(s)?

This is what I though that could be the problem
- Port are not opened
-- so I opened the port 137, 138, 139 and 445 (didn't work)

did I forgot to open a port or it's not possible to create a network drive over the internet.

p.-s. in windows I try to create a network drive this way : \\MyDomainAddr\SharedForlder

Thank you for your time
K-Jtan

---

### Post by wyliecoyoteuk on 2011-12-23
Netbios (SMB) is not routable, so if you want to access it over the internet, you need to set up a VPN connection.
Which you really should do anyway really, opening port 139 to the internet is like opening your front door, waving a red flag to a burglar and shouting "please steal my data"

---

### Post by K-Jtan on 2011-12-23
Thank you very much, I will document myself on how to do a VPN connection.

I'll open an other Thread if I need help on that.

---

