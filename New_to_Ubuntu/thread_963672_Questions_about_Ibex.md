---
title: "Questions about Ibex"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Neurosynapse on 2008-10-30
Afternoon All,

I'm just wondering, is it possible to connect remotely and manage a MySQL database on Ubuntu? Also, (this may seem like a stupid question, but I honestly don't know) is it possible to remote desktop connection with Windows Server 2003 under Ubuntu?

Thanks,
Neuro

---

### Post by Het Irv on 2008-10-30
Not sure about the MySQL, but I remote desktop to Win03 all the time using the built in application.  Look under Applications -> Internet -> Terminal Server Client

An IP address is all you really need the rest of the information is optional, and the RDPv5 works just fine.  Just click connect.

---

### Post by cariboo on 2008-10-30
Yes you can remotely administer mysql from any operating system. To remote operate Windows 2003 server you need to install a vnc server on the server and a viewer from which ever computer you want to control it from. There are several free variants of vnc that you can downloaded and installed on the server, Realvnc and Tightvncserver are two that I have used. There are several vnc viewers in the repository, got to SYstem-->Administration-->Synaptic PAckage Manager and search for vnc, select the one that suits you best.

Jim

---

### Post by Neurosynapse on 2008-10-30
Thanks guys, I do actually have the server setup for such things, vnc and all. I was just unsure if it was possible from Ubuntu, as I'm a total Linux noob.

Thanks again,
Neuro

---

