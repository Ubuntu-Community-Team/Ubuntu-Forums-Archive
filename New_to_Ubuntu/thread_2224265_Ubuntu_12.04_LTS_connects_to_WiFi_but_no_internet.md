---
title: "Ubuntu 12.04 LTS connects to WiFi but no internet"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by FelixKlein98 on 2014-05-15
Hi people,

I have Ubuntu 12.04 LTS installed on my Dell laptop. Some extremely strange things are happening with the connection to internet. I can connect to the router at home but I can not then open any webpage in the browser. But when I make a VPN with my university network using (Cisco Anyconnect Secure Mobility Client) then I can open any website. I have tried it many times, nothing opens without a VPN connection. What makes everything stranger, is that when I go to the university and connect with the university WiFi, it connects very normally. Also I was before in another residence and it had connected to the WiFi router in that residence, but it cicked me sometimes out, and I had to deactivate and reactivate wireless. But in all cases, it loses the connection in time periods, and they vary, but it does not tell me, I just notice it, when I cannot open Webpages anymore.

Any help will be appreciated, and thanks in advance!! :) :)

Salah

---

### Post by sandyd on 2014-05-15
Can you post the output of
```

cat /etc/resolv.conf
```

You can access the terminal by going to the dash -> typing terminal, and clicking on terminal.

---

### Post by FelixKlein98 on 2014-05-15
This is in the university:

domain triple-a.uni-kl.de
nameserver 131.246.9.116
nameserver 131.246.1.116
search triple-a.uni-kl.de hitronhub.home


I will post the output again when I am home :)

---

### Post by FelixKlein98 on 2014-05-15
and this output, I got at home 
once without being with VPN connected:

domain triple-a.uni-kl.de
nameserver 131.246.9.116
nameserver 131.246.1.116
search triple-a.uni-kl.de hitronhub.home

and once more after connecting to VPN:

domain triple-a.uni-kl.de
nameserver 131.246.9.116
nameserver 131.246.1.116
search triple-a.uni-kl.de triple-a.uni-kl.de hitronhub.home

---

