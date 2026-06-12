---
title: "Setup Hostname instead of IP on local network"
date: 2014-06-24
forum: New to Ubuntu
---

### Post by philip7 on 2014-06-24
I'm currently playing around with Ubuntu Server setup on VirtualBox, I've been able to install a virtual instance of Ubuntu server without a problem, I've also been able to web content hosted on that server using the host machine by going to the IP address.

But I want to use the hostname instead of the IP address as its a little easier, I thought this would be as easy as writing the server name in my browser (I have Mythbuntu on another machine and this works in this way)

I've done some googling but get some very complex answers, sure there must be an easier option. I have also read about modifying the host files on my host machine but I'd like to try and not use this approach if I can.

Sure this is really obvious, but really seem to be struggling.

Thanks in advance.

---

### Post by SeijiSensei on 2014-06-24
Your choices are either to add the name/IP pair to the [hosts file]("http://en.wikipedia.org/wiki/Hosts_%28file%29") on every potential client, or install a DNS server.  The former is easier if you just have a couple of machines to maintain.  

It's also possible that your router functions as a DNS server.  If so, you may be able to add an entry to it there and make it available to every user.

---

### Post by cmcanulty on 2014-06-25
I am also interested in this could you post details and whether this only works with a static ip

---

### Post by Morbius1 on 2014-06-25
I'm not sure I understand the original post.

Are you trying to connect to a http server on the local lan by name not ip address?

What operating systems are the clients running?

If they are running Linux or OSX you already have mDNS buit in. From either you can access this way:
```
http://host-name.local
```
Just make sure you add the ".local" at the end of the host name of the server.

Won't work with Windows clients but you can use that as a justification to replace them all with Linux or MacBooks.

---

