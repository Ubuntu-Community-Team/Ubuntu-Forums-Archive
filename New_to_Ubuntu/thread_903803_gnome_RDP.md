---
title: "gnome RDP"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by philk949 on 2008-08-28
Hi,
Could someone please tell me or point me in the direction of a guide, that will tell me if I can access,via the internet, my home PC (Hardy Heron),  from a remote PC running Windows XP SP2 on a Windows Server 2003 network?
I have gnomeRDP installed on my home PC.

Thank you

Phil

---

### Post by cariboo on 2008-08-28
You can use one of the VNC derivatives (RealVNC, TightVNC and others) on Windows to access your home pc. If you have a router you will have to give your Ubuntu pc a static ip address and set up port forwarding on your router to forward port 5900 from your pc to your router.

Jim

---

### Post by philk949 on 2008-08-28
Jim,

Thanks for the reply.By router, do you mean modem, or switch. All I have at home is a standard broadband modem (512 Mb/sec). Can this be configured, and if so, how?

Thanks,

Phil

---

### Post by halitech on 2008-08-28
how many systems do you have at home? what is the IP address of your computer?

---

### Post by philk949 on 2008-08-28
1 system - Ubuntu 8.04
Is it wise to be broadcasting my IP address? I wouldn't have thought so

---

### Post by halitech on 2008-08-28
ok, better way of asking, do you have an IP address that starts with 192.168.? or is it a "live" or routable IP address that can be reached from the internet?

if it's a 192.168.x.x then you have a router, if not you don't have a router

---

### Post by philk949 on 2008-08-28
No 'fraid not. Mine is a Class A address, beginning with 59.100

Thanks

---

### Post by halitech on 2008-08-28
ok so no router so makes it easier to configure. Should just be a matter of installing TightVNC or something similiar (tightvnc works great from a thumbdrive with no install needed) and making sure you have the right ports open on your home computer

---

