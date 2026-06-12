---
title: "Setting up my Domain - Ubuntu 12.04.2"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by sakuraba on 2013-05-30
Hi everyone,

Recently I bought a domain name from crazy domains.com.au
I also purchased the dns service option.
Yes I am using a dynamic IP at present but I had intended to get it working and test it before paying $ per month for a static. (also bigpond adsl 2 IPs remain the same for quite some time)

I am running Ubuntu Server 12.04.2
My router IP is set to 192.168.0.1
My network card IP is set to 192.168.0.3
My internet IP set by telstra is 60.xx.xx.xx.xx
I am also using a Thomson TG782T with a telstra bigpond adsl 2 account.

I made an A and AAA record on crazy domains.com.au and pointed it to my dynamic IP address assigned to my bigpond account internet 60.xx.xx.xx.xx

I installed apache2 and also bind9

I can point resolv.conf to my local server either 127.0.0.1 or 192.168.0.3 and host names WILL resolve so Im guessing my bind setup worked.

now the router - Thomson TG782T uses 10.0.0.138 usually but I changed that to 192.168.0.1 

so when I put 192.168.0.1 into my web browser it brings up the Thomson TG782T admin page where I can change settings.

The problem Im having is when I enter my domain name or my Internet IP 60.xx.xx.xx it actually brings up the Thomson TG782T admin page.

Im guessing thats not a good thing for security reasons :-P But what am I doing wrong?

So basically I think anyone could enter my domain name in there web browser and get to my modem configuration page.

Sometimes It will take me to [http://search.bigpond.net.au](http://search.bigpond.net.au)

What am I not doing?

Is anyone willing to help me get this sorted out?

Thank you.

---

### Post by SlugSlug on 2013-05-30
You need to access your external IP from outside your network

hidemyass.com is a free proxy you could use to test (don't send any usernames/ passwords through it)

You'll also need to set up portforwarding on your router 

portforward.com

---

### Post by sakuraba on 2013-05-30
hrmmm when I use hidemyass.com as a web browser proxy It still takes me to my routers admin page :-P

---

### Post by SlugSlug on 2013-05-30
look through router settings for remote access and disable it. Also setup port forwarding

---

