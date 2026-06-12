---
title: "Ubuntu -firefox  cannot connect to cPanel"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by bohica on 2012-01-11
Hello
   I have a dual boot pc win7 and Ubuntu. I can go to cPanel and login from windows-firefox but not from ubuntu-firefox. I get the message 
Firefox can't establish a connection to the server at mathematica.net.au:2082. But I can go to mathematica.net.au, no problems.
I do not have a fire wall set up on the pc I've had a look using gufw.
ANy ideas any one?

TIA

Bo

---

### Post by lovinglinux on 2012-01-20
Try these, to make sure you iptables are accepting any connection:

```
sudo iptables -F
sudo iptables -X
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

---

