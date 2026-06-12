---
title: "Help about domain name ek ek"
date: 2011-05-16
forum: Philippine Team
---

### Post by eSPiYa on 2011-05-16
Sorry mga boss kung hindi ko alam ang term nito kaya hindi ko ma-search sa google. Hehehe!

Anyway, ito 'yung gusto kong mangyari; declare a dummy domain name like "facebookapplocalhost.com" then magpo-point sa local machine ko(127.0.0.1:80 or 127.0.0.1:8080)

Thanks!

---

### Post by angheloko on 2011-05-16
Check mo yun host file mo

---

### Post by eSPiYa on 2011-05-16
Saan po 'yun mahahanap? Thanks!

---

### Post by dsdeiz on 2011-05-16
/etc/hosts ? Hehehe

---

### Post by eSPiYa on 2011-05-16
Thanks boss. Will try it later. ^_^

---

### Post by JCyberinux on 2011-05-16
domain name is like for example (jcyberinux.com), the question is do you bought or own that domain? then next question wat type of internet connection you have? static or dynamic? answer these then the next questions or answer will follow up.

---

### Post by eSPiYa on 2011-05-16
Nope, it is just a dummy domain name for debugging my Facebook app locally. FB doesn't allow debugging on localhost and this is a trick I'm using during the time I'm still on MS Windows. :D

---

### Post by JCyberinux on 2011-05-16
i see, i suggest you might change your subject or your topic. :) by the way, do you solved your own concern? do you own a router or wireless router?

---

### Post by eSPiYa on 2011-05-16
Not yet, will try it when I got home. I think I need to restart the network part para mai-apply 'yung changes. 

About the router ay I think irrelevant na 'yang part na 'yan dahil sa localhost(127.0.0.1) lang naman ang kailangan kong tingnan while developing my Web-app and perform debugging.

As of now, wala akong maisip na term para sa problema na ito dahil hindi ko alam ang proper terminology so will leave it as it is. Hehehe!

---

### Post by pinoyskull on 2011-05-16
> **eSPiYa said:**
> Not yet, will try it when I got home. I think I need to restart the network part para mai-apply 'yung changes. 

About the router ay I think irrelevant na 'yang part na 'yan dahil sa localhost(127.0.0.1) lang naman ang kailangan kong tingnan while developing my Web-app and perform debugging.

As of now, wala akong maisip na term para sa problema na ito dahil hindi ko alam ang proper terminology so will leave it as it is. Hehehe!
changes in /etc/hosts is instant, no need to restart network

---

### Post by eSPiYa on 2011-05-16
Ah, ok. Nakita kong pattern d'un ay ganito:

> [IP Address] [Domain name]

ex:
> 127.0.1.1 MyMachine


Kung ang target ko ay may specific port like 8081, tama ba ang entry na ito:
> 
127.0.0.1:8081 facebookapplocalhost.com

Thanks!

---

### Post by pinoyskull on 2011-05-18
> **eSPiYa said:**
> Ah, ok. Nakita kong pattern d'un ay ganito:



ex:



Kung ang target ko ay may specific port like 8081, tama ba ang entry na ito:


Thanks!

ports should be handled by the webserver

---

### Post by eSPiYa on 2011-05-21
I know it already but what I mean is ima-mask ko 'yung port number with the ip address.

'Yung domain name na 'facebookapplocalhost.com' ay automatically pupunta sa '127.0.0.1:8081'.

So kung pupuntahan ko 'yung 'facebookapplocalhost.com' ay automatically naka-point pala yan sa localhost ko na ang port number ay 8081.

Thanks!

---

