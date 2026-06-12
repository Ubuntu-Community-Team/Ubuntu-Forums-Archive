---
title: "Question about UFW"
date: 2022-07-15
forum: New to Ubuntu
---

### Post by bhubunt on 2022-07-15
Hi All,
On this helpful wiki link ([https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall)), there is a section about setting up transmission rules: 

[COLOR=#333333][FONT=&quot]Transmission rules[/FONT][/COLOR]

[LIST]
[*]sudo ufw allow out 51413/tcp
sudo ufw allow out 51413/udp
sudo ufw allow out 6969/tcp


What is the purpose of those rules and do I need them if I don't have a server set up, but am only using a laptop with a basic internet connection?
[/LIST]

---

### Post by mikewhatever on 2022-07-15
Transmission is a bittorrent client/server that needs to send a recieve packets through the specified ports. It has been preinstalled on all *buntu releases for years. 
So, the purpose of the above is to allow outgoing connections. You need them if UFW is enabled and if you use Transmission. 

PS: Not sure what "a basic internet connection" is.

---

### Post by bhubunt on 2022-07-15
Hi,
Thanks. I looked up Transmission and found a helpful wikipedia entry: [https://en.wikipedia.org/wiki/Transmission_(BitTorrent_client)](https://en.wikipedia.org/wiki/Transmission_(BitTorrent_client))

So, I did not add those rules as I do not need Transmission.

---

