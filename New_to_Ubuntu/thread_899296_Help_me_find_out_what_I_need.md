---
title: "Help me find out what I need"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by shafin on 2008-08-24
I need to do the following:

I have a setup of multiple pc's, one of them would act as the central pc and the other as secondary pc's. The person at the central pc should be able to see what others at the secondary pc's are doing. He should be able to access the desktop of all other pc's in real time, more like in a cctv application and should be able to see what the user is doing. Being able to run a program on the secondary pc is not necessary for the user at the central pc. His primary aim is to see what others are doing. Like the desktops are recorded and streamed in live to the central pc. the user sat central pc should also be able to see multiple pc's simutaneously.The pc's are connected via LAN or WAN.

What do I need to do in order to achieve this? A linux based setup is much much preferable, but even if you know a windows based solution, please mention it.

Thanks in advance.

---

### Post by iKevin on 2008-08-24
Have you taken a look at VNC?  You should be able to set up all of the "secondary" PCs to allow a connection from the "main" PC.

Kev

---

### Post by cwsnyder on 2008-08-24
In order to accomplish what you wish, you almost need a server/virtual thin-client approach where the execution of programs for the clients actually occurs on the server.  As iKevin said, VNC should allow the execution on the server, but you probably want to set up the clients on the server under virtual machines, as in Sun xVM Virtual Box, to keep the clients from messing each other up.

A normal client/server approach would not allow the central computer to monitor the operation of the clients, even with thin clients.

cwsnyder

---

