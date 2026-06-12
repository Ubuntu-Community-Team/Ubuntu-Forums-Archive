---
title: "setting up proxy"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-14
system>preferences>network_proxy I'm going to select "auto configuration" and so I'm going to input the "autoconfiguration url."  but what is that?  is that the url of the proxy server I want to use or what?

---

### Post by Vivaldi Gloria on 2008-07-14
> **adamogardner said:**
> system>preferences>network_proxy I'm going to select "auto configuration" and so I'm going to input the "autoconfiguration url."  but what is that?  is that the url of the proxy server I want to use or what?

No, you need to fill the above parts for proxy settings. So find out the adresses and the ports that the proxy you want to connect use and fill them in.

Some proxies actually have "auto configuration" adress which passes on all the adress & port info automatically and this saves you from entering them manually. But hardly any of them have one.

---

### Post by sayakb on 2008-07-14
Google for IP addresses of proxy servers. I have some names, but I'm not too sure whether I should post it here. You have to enter the IP address and port of the proxy server.

---

### Post by adamogardner on 2008-08-08
when choosing a proxie, how do I avoid a honeypot, or other ineffective proxy?
I need a role model or two to emulate during questions like this.  Are there any computer superstars that everyone admires?  What do they use?

---

### Post by mssever on 2008-08-08
> **adamogardner said:**
> when choosing a proxie, how do I avoid a honeypot, or other ineffective proxy?
I need a role model or two to emulate during questions like this.  Are there any computer superstars that everyone admires?  What do they use?
Many people use squid. ```
sudo aptitude install squid
``` tinyproxy is another option if your needs are basic.

---

### Post by adamogardner on 2008-08-08
> **mssever said:**
> Many people use squid. ```
sudo aptitude install squid
``` tinyproxy is another option if your needs are basic.

doesn't a proxy serve as an agent of anonymity?  how can it work if I install it? isn't it a server somewhere?

---

### Post by hansdown on 2008-08-09
This tread may help.  [http://ubuntuforums.org/showthread.php?t=884388](http://ubuntuforums.org/showthread.php?t=884388)

---

### Post by mssever on 2008-08-09
> **adamogardner said:**
> doesn't a proxy serve as an agent of anonymity?
Some can, to an extent. Of course, the proxy has to know your IP. But there are many uses for proxies. You can use them on your network for caching, to speed up browsing. You can use them for filtering. You can use a reverse proxy to present multiple machines to the world seamlessly as a single machine.

If you ask for a proxy without specifying what you want to do with it, it's reasonable to assume that you want to set up a proxy to use on your machine or network for some purpose, not that you're looking for some pre-existing proxy server.

---

### Post by adamogardner on 2008-08-09
> **mssever said:**
> .If you ask for a proxy without specifying what you want to do with it, it's reasonable to assume that you want to set up a proxy to use on your machine or network for some purpose, not that you're looking for some pre-existing proxy server.

Oh well to be quite clear, I just want to hide my IP address and never need to think about it again.  Those other uses you described sound interesting but out of my realm of operations right now.

---

