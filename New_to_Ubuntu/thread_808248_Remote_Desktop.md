---
title: "Remote Desktop"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by guilly on 2008-05-26
Hi guy's / gal's,

I'm having an issue creating a remote desktop session to my file server running xfce. I have tried with the built remote app that comes on Kubuntu and with vnc with no luck. However, the funny thing is when I start a new session and try to connect remotely from the Kubuntu logon window it works fine? 

Would anyone know why it is working the one way but not the other way? Btw I'm getting connection refused error when I try to connect once I am logged onto my Kubuntu session.

Thanks

---

### Post by Inxsible on 2008-05-26
Have you opened the appropriate ports in your Firewall? You can use FireStarter or GuardDog to do it.

---

### Post by guilly on 2008-05-26
> **Inxsible said:**
> Have you opened the appropriate ports in your Firewall? You can use FireStarter or GuardDog to do it.

I've opened the ports on my router. But haven't touched Firestarter or anything else.

I don't think it'll matter, I didn't mention this but I am inside my LAN when trying to connect.

---

### Post by Inxsible on 2008-05-26
> **guilly said:**
> I've opened the ports on my router. But haven't touched Firestarter or anything else.

I don't think it'll matter, I didn't mention this but I am inside my LAN when trying to connect.
you would still have to open the ports on both computers, no? If the firewall blocks those ports then you are not going to get an incoming connection.

---

### Post by guilly on 2008-05-26
> **Inxsible said:**
> you would still have to open the ports on both computers, no? If the firewall blocks those ports then you are not going to get an incoming connection.

Possibly, you may be right I'll double check tonight just to make sure. I don't understand why I can connect if I create a new session but not from VNC or any other RD application.

---

