---
title: "[SOLVED] live web server?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by melrom on 2008-07-30
Hi-

I know this is a dumb question, but I can't even find the documentation for this kind of thing. I'm new to server stuff, and I wanted to test some software, and was able to have [http://localhost](http://localhost) work and everything. But now I want that to be accessible to other machines via the IP address of the machine. I can't figure out how to do this. And all of the guides I've found seem to end with "Setting it up to run locally".

If anyone could help or point me in the direction of documentation, it would be much appreciated.

-Melissa

---

### Post by decoherence on 2008-07-30
There aren't any particular steps you have to take to make the apache server accessible to other computers, assuming you installed it in a fairly typical way (synaptic, apt-get, etc.) All you should need is a working network.

What currently happens if you type in the IP address of the server from another machine? If you get a connection refused type error, can you confirm that the machines can ping each other?

If they can't, can you confirm that the computers are on the same subnet? Use ifconfig on linux and ipconfig on windows. If your network mask is 255.255.255.0, make sure that the IP address of each computer differs only in the last number (ie, 192.168.1.1 and 192.168.1.2 but NOT 192.168.1.1 and 192.168.0.2)

I gotta go smack down a photocopier now. I'll be back.

---

### Post by ibutho on 2008-07-30
If you want to access the webserver from another machine, just enter the IP address of the server in a web browser from the other computers.

---

### Post by Dr Small on 2008-07-30
You can install XAMMP:
[http://php.8ez.com/drsmall/blog/?p=96](http://php.8ez.com/drsmall/blog/?p=96)

But as long as it is running locally and you have a firewall with rules set, you just meerly need to open port 80 inbound in the firewall rules, and then others on your network should be able to connect.

---

### Post by melrom on 2008-07-30
I can't access it by using the IP of the machine on another box. It might be because of the security measures at work.

---

### Post by Nitrolinken on 2008-07-30
The issue you are most likely to experience problems with would be port forwarding (if you have a router, that is).

Take a look at [http://www.portforward.com/english/routers/port_forwarding/routerindex.htm](http://www.portforward.com/english/routers/port_forwarding/routerindex.htm) for various guides for your router (if you have one).

---

### Post by Dr Small on 2008-07-30
> **melrom said:**
> I can't access it by using the IP of the machine on another box. It might be because of the security measures at work.
Is port 80 opened on your machine?

---

### Post by melrom on 2008-07-30
thanks. sounds good.

turns out http wasn't trusted via my firewall.

thanks for your help everyone!

---

### Post by Seisen on 2008-07-30
Are you wanting to access the server from outside the network, like access the server at home from work?

---

### Post by melrom on 2008-07-30
> **Seisen said:**
> Are you wanting to access the server from outside the network, like access the server at home from work?

no, no. just inside the network. i got it though, so it's working now.

---

