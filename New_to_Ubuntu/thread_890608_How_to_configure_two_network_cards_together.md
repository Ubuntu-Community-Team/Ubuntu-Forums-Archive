---
title: "How to configure two network cards together?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-08-15
I have two network cards on my ubuntu...

How to configure both together?
One is for Broadband internet and other for office intranet.

---

### Post by ilrudie on 2008-08-15
You will have to add another stanza to the /etc/network/interfaces file.
You will need to use sudo (or gksudo for graphical editors) to edit the file.
The new interface should be on a different subnet.
Don't forget the auto statement if you want the interface to come up automatically at boot.
You will need to restart networking with sudo /etc/init.d/networking restart (if its an auto interface) or bring up the new interface with ifup otherwise.
After this you may have to make changes to the routing tables in order to access both networks.  I'm not sure if Ubuntu will add a route to the other subnet or not.

---

