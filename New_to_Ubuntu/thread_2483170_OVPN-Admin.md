---
title: "OVPN-Admin"
date: 2023-01-22
forum: New to Ubuntu
---

### Post by hubson018 on 2023-01-22
Hello.
Im completely new in Ubuntu. Sorry for probably that silly Thread.

I set up a OpenVpn server at ubuntu 20.04, its working fine when i create new user manually and i can connect to that server by my android phone.
I tried to install UI version for that server (OVPN-Admin), its "working" so i can go to the 0.0.0.0:8080 and can see the interface. But when i create a user i cannot connect to the server by .opvn file.
When i install OVPN-Admin i didnt setup anything. Probably that is the problem. When i create user manually i need to use cert and key to do it.
I dont know how to connect that OVPN-Admin to my OpenVpn server so its can working together fine.
Can somebody help me ?

OVPN-Admin repo : [https://github.com/flant/ovpn-admin](https://github.com/flant/ovpn-admin)
OpenVpn version : [COLOR=#002F34][FONT=Geomanist]2.5.8
[/FONT][/COLOR]VM with ubuntu is on the azure cloud.
Tutorial what is use for setup OpenVpn server : [https://simplificandoredes.com/en/install-open-vpn-on-linux/](https://simplificandoredes.com/en/install-open-vpn-on-linux/)

---

### Post by TheFu on 2023-01-24
Just so you know, I saw this thread a few days ago.  I used openvpn for a long time, but never with their added admin GUI, which is why I didn't respond.  It is a convenience, but not necessary.  The CA scripts work easy enough. I don't want to have the CA running ON the same system that has openvpn.  It's a security thing for me.

---

### Post by ActionParsnip on 2023-01-25
Did you read the readme file? It has options that you can set on the binary and may help
[https://github.com/flant/ovpn-admin/blob/master/README.md](https://github.com/flant/ovpn-admin/blob/master/README.md)

---

