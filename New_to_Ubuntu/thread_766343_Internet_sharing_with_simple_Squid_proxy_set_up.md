---
title: "Internet sharing with simple Squid proxy set up"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by noswal on 2008-04-25
I have a simple network setup, internet comes in to Ubuntu pc (dual boot XP) through a switch and shares the internet with the other 2 xp pc's by way of a proxy, using squid.
 

```

	      modem
		|
	-----switch--------
	|	|	  |
	|    Ubuntu pc    |
	|   (dual boot)	  |
	XPpc2           XPpc3
```



Because I dual boot and I'm using a proxy when main pc is running windows I wanted the service to be available when swapping. I downloaded squid in synaptic with these 2 files squid3 and squid-common.

then 
```
sudo gedit /etc/squid3/squid.conf
```
and start editing lines per this guide

[http://www.tutorial5.com/content/view/118/51/](http://www.tutorial5.com/content/view/118/51/)
		
my pc's use 192.168.1.100, 101 & 102 so fitted in with that guide

I changed http_port to 6588 as that is the same port windows uses and the other 2 pc's have that set in Firefox connection settings

so its only about 4 lines I actually edited in squid.conf
in firestarter firewall, have incoming allow rule for port 6588 - lan

once set up and saved 
```
sudo /etc/init.d/squid3 start
```


checked cache.log in /var/log/squid3 and all seemed to be there. 


Opened webpage in other xp pc so it worked

---

### Post by dark_harmonics on 2008-11-29
So is your problem that the other pc will not connect? Typically the setup for a proxy server is like this:


Computer1-----  s ------DHCP and Routing Server ---- Cable Modem
Computer2-----  w                  |       |
computer3-----  i                  |       |
computer4-----  t               Squid Proxy Server
                c
                h

On my setup i just wanted a transparent server (no putting static numbers in each connection based program) So i configured my server as a transparent proxy and redirected port 80 from my router to my proxy. Since i had all this running on one box i really just pointed it at itself for port 80 requests. Squid then picks up the connection, and will serve a local webpage if it is available. If not it will grab from the internet and serve.

---

