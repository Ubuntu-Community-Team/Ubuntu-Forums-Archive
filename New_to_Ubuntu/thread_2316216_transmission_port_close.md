---
title: "transmission port close"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by flex567 on 2016-03-06
My transmission is not working. When I go to its settings and press test port I get 'port is closed'. How can I fix this ?

---

### Post by flex567 on 2016-03-06
Now for some strange reason works on port 57558.

---

### Post by yetimon_64 on 2016-03-06
> **flex567 said:**
> My transmission is not working. When I go to its settings and press test port I get 'port is closed'. How can I fix this ?
First I log into the interface for my modem router ...
[ [IMG]https://dl.dropboxusercontent.com/u/30874719/UF/Router-login_thm.png[/IMG] ]("https://dl.dropboxusercontent.com/u/30874719/UF/Router-login.png")

Then in there I set a port forwarding rule for the IP of my linux installation allowing port 51413 through the firewall for my IP ...
[ [IMG]https://dl.dropboxusercontent.com/u/30874719/UF/virt-server_thm.png[/IMG]]("https://dl.dropboxusercontent.com/u/30874719/UF/virt-server.png")
When this is set to enabled for my installs lan IP I can test the port and have the port show as "open".

How do you connect to the internet ? Are you behind a hardware firewall like shown in the pics ?

---

