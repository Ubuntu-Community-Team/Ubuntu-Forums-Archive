---
title: "Apache server problem"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by mamut0o1 on 2008-10-06
Good morning all; I have a linux server at home running apache. I am able to access the server by typing the ip from my other PC and access the apache server. I have port fowarding 80 enable from Linsys switch pointing at my linux box. It seems like apache it's only allowing LAN traffic; How could I check and allow traffic from the internet (WWW).

please let me know if you guys have any ideas. thanks!

---

### Post by hyper_ch on 2008-10-06
so what does not work?

You can access the server by entering the lan-ip and you forwarded port 80 from the router to the server.

So what does not work?

---

### Post by leg on 2008-10-06
I think he might be suggesting connecting to it from outside his network. This can be a pain as you need a static ip which most dsl providers do not give you. There are ways of redirecting but I am unsure of how to do it.

---

### Post by Joeb454 on 2008-10-06
[http://www.dyndns.com](http://www.dyndns.com)

That's how I redirect traffic to my domain.

It helps if your router supports updating it. If not I think you can get clients to do it automatically also :)

---

### Post by superprash2003 on 2008-10-06
and you would also need to open port 80 in your modem or router..

---

### Post by mamut0o1 on 2008-10-06
Hello all thanks for your replies; 
>what does not work?
I can't access my apache server from the internet.

---

### Post by mamut0o1 on 2008-10-06
> **leg said:**
> I think he might be suggesting connecting to it from outside his network. This can be a pain as you need a static ip which most dsl providers do not give you. There are ways of redirecting but I am unsure of how to do it.
I have an account with dyndns.com and my ip gets updated autmatically so from that end I don't have a problem.

thanks

---

### Post by drubin on 2008-10-06
> **Joeb454 said:**
> [http://www.dyndns.com](http://www.dyndns.com)

That's how I redirect traffic to my domain.

It helps if your router supports updating it. If not I think you can get clients to do it automatically also :)

I have had nothing but issues with routers....
```
sudo apt-get install ddclient
```

Configure it once(it is the username,password, update interval) and you are sorted.

---

### Post by mamut0o1 on 2008-10-06
Thank you all but after all I found out the router I was using was defective. Port Fowarding was not taking the changes blocking everything but web management for the switch itself. I just pulled an old router I had and it worked great.
Thanks again!

---

### Post by hyper_ch on 2008-10-07
dyndns or noip is also nice to have... that way can always get access to your computer (especially when using ssh). The noip client in the repos is called "noip2".

---

