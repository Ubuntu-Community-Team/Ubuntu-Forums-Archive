---
title: "new to apache"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Smatt454 on 2008-04-29
I'm relatively skilled with Linux, but have VERY little skill in apache.  I have a sever set up, which i can use on my intranet by pointing my internet browser to my ipaddress.  However, beyond that there really isnt much i know.

I was thinking of buying a domain and trying this out. However Id on;t know where to begin to configure my apache server.

I've never bought a domain before, so I don't know how it works. I'd like to know how I would configure apache if I bought a domain...i dont know much at all so all the info anyone could give is appreciate.

I've tried to google it, and the sites i did find i dont entirely understand.

the 3 things i really want to know is

1)If i registered a domain how would i configure apache
2)is there a way to configure apache to use a domain on my internal network without registering that domain(so if i wanted to go to like [www.whatever.com](www.whatever.com) on my other computer)
3)if there is a way to make it so i could access my web server though my global ipaddress without registering a domain?

i do want to learn anything else I can about apache. I am planning on going into the field and I need to know where to start.

THANKS MUCH! :guitar:

---

### Post by lwvmobile on 2008-04-29
It just depends on how and what you want to do. If you only want one site running on your Apache2 server, then you can just use its IP address without configuring a virtual host. This is what I would recommend at least to test things out.

With registered domain names, you can either simply forward them to another address, such as a dynamic dns address name or an ip address, or you can configure an @ name or A name, depending on your provider, to run the FQDN to the server so that Apache2 can route it to the correct virtual host.

For access to your server from the outside world, it is just a matter of opening the correct ports on your router(s).
:popcorn:
Here is a question: Do you have a static wan ip address?

Anyways, here is a great startup guide for Ubuntu Server 8.04, with Apache2 configuration instructions: [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by Smatt454 on 2008-04-29
how do i check if my wan ip is static or dynamic =/ (i dont know much about configuring routers, im going to be taking a class on it)


> With registered domain names, you can either simply forward them to another address, such as a dynamic dns address name or an ip address, or you can configure an @ name or A name, depending on your provider, to run the FQDN to the server so that Apache2 can route it to the correct virtual host. and im trying to figure out how to do that

---

### Post by lwvmobile on 2008-04-29
To check whether you have a static or dynamic wan ip address, it is probably easiest to contact your ISP and ask them. How exactly do you connect to the Internet and who is your provider? Most people have dynamic, so it presents an additional challenge to over come for setting up a webserver on your own Internet connection.

Ok, now let me give you an example.

I have a website, diy-linux.info which I purchased from godaddy.com for .99 cents American + registration fees, so in total $1.20 or so. After setting it up, I can log into godaddy and go to their domain control panel and specify things I want to do to my diy-linux.info domain name. I can tell it to either foward all traffic to a specific ip address or alternate name like myname.gotdns.com called a standard forward or I can setup an @ name that will forward the fully qualified domaiin name diy-linux.info to my designated static IP address 70.0.0.xxx and ultimately to my ubuntu server running apache who will determine what to do with the request once a web browser puts in the address diy-linux.info. Apache will take the FQDN and forward it to the correct folder on my ubuntu machine and serve up webpages.

Hope the explanation helps. I'm not very good at them though, I am afraid. BTW, if you do go to diy-linux.info, its nothing special, and just for fun. Very incomplete and more of a test bed than anything.

---

