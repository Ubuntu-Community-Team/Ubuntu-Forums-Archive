---
title: "remote desktop to ubuntu rdp or vnc client"
date: 2012-10-10
forum: New to Ubuntu
---

### Post by fachhoch on 2012-10-10
Please advice I have a remote  ubuntu workstation  ,  what is the best way to connect to this for remote desktop through   xp? is it vnc or rdp ?
rdp is really easy I dont need any client , why should I use vnc over rdp ?
Please advice.

---

### Post by UrielCantarero on 2012-10-10
sudo apt-get install xrdp

This will install the xrdp server, you then use Windows Remote Desktop to connect.

---

### Post by fachhoch on 2012-10-10
> **UrielCantarero said:**
> sudo apt-get install xrdp

This will install the xrdp server, you then use Windows Remote Desktop to connect.

Thanks for the reply I tried this but I facing some problems.

I cannot see session menu.

which one is recommended and widely used   xrdp or vnc please advice ?

---

### Post by UrielCantarero on 2012-10-11
Explain what you mean by "cannot see session menu".

Did xrdp install ok?
Did you see if the xrdp server service started after the installation?
What happens when you try to connect to that machine from your windows machine?

xrdp and vnc are different.  It really depends on what you want to do.  You should read up on both.

---

