---
title: "Samba Tip (Routers!)"
date: 2006-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by kleeman on 2006-01-12
I was having a lot of problems getting a Windows XP computer to see a samba server on my Ubuntu box. It needed to see the server so that I could share files between the boxes and so that the Windows XP box could use printers attached to the linux box. 

The Windows XP box was on a wireless connection with dhcp obtained from a router. I would constantly lose connection with this box and it would not print. :confused: :confused: :confused: 

Finally discovered that the wireless connection would often drop out and then the router would assign it a new ip address. This seems to badly confuse samba and the connection is then lost.

Solved the problem finally by using a STATIC DHCP on my router (D-Link DI-624). Not only does this fix the IP address in stone but it also enables you to name your Windows Box. Both these things seem to make Samba a lot happier.

Hope this helps someone.

---

