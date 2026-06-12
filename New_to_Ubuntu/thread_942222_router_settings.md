---
title: "router settings"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-10-09
Alright, so I'm setting up a web server and I've finally got it to where when you type in my ip address it opens up the panel to where you login to my router and change settings. now all I have to do is get it to just forward directly to my web server. How do I do that?:confused:

---

### Post by iaculallad on 2008-10-09
From outside to inside? You just have to port-forward port 80/8080 to the private IP number of your local web server.

---

### Post by lazyart on 2008-10-09
Without knowing the brand and model of your router it's tough to say.  You'll generally want to look for Port Forwarding or Virtual Servers.  From there, forward incoming port 80 to port 80 of the internal ip address of your server.

You likely won't be able to test it.  You would need to be outside of your network to do that.  Call a friend, give them your external ip address (hint, go to whatismyip.com to see what it is right now), and tell them to enter that address into their browser.  If everything is set up correctly, they will see your web page.

---

### Post by crispy_420 on 2008-10-09
Also you may want to setup a dynamic dns service to get a real address that will work regardless if your ISP changes your IP. That as well can be setup in your router.

But first, let us know what your router make/model is to help you proceed.

---

### Post by cariboo on 2008-10-09
First a question. Are you accessing the router control utility from outside your local network? If so turn of remote access.

To port forward, you should set a static ip address for your web server, the ip address should be outside the range of the dhcp address the router provides, then go it the management utility on your router and set it so that port 80 is forwarded from the static ip address you just set on your server. 

To check to see if you have done everything correctly go to [canyouseeme]("http://www.canyouseeme.org/") and check to see if 80 is open.

To set a staic ip address, (this is assuming you have a gui on your web server) press Alt-F2 then type:

```
gksu gedit /etc/network/interfaces
```

enter your password when asked. the file you just opened should look something like this:

```
auto lo
iface lo inet loopback
```

Add the following lines:

```
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

The above ip address should reflect the ip addresses in your local network, the two that you probably will have to change  are the address and the gateway. Save and close gedit.

Now you have to restart the network, open a terminal and type the following:

```
sudo /etc/init.d/networking restart
```

For instructions on setting up port forwarding in your router refer to the documentation that came with your router as there are way to many routers to cover in an answer like this.

Jim

---

### Post by RadiationHazard on 2008-10-09
I have a wireless Netgear router. I'm pretty sure It's a W model and it has 614 somewhere in the model number but I'm not at home right this second so I can't give the exact model number sorry. I know that I need to go to port forwarding/ port triggering I just don't know what to do once I get there. It already has a port set up with the name being HTTP the port being 80 and the ip or something being something like 192.**.1.1 or something sorry I can't remember. If my details are bad I appologize I'll give better ones when I get home if these aren't good enough to tell me what I need to do.

[SIZE="2"]**[COLOR="Red"]EDIT:[/COLOR]**[/SIZE] I found my router. Here is a link.
[http://www.google.com/products/catalog?q=WGR614&oe=utf-8&cid=10256100175040107864#ps-sellers](http://www.google.com/products/catalog?q=WGR614&oe=utf-8&cid=10256100175040107864#ps-sellers)

also, I'm thinking about installing Tomato Firmware on my router. I've heard good things about it. Do you think it's a good idea?

---

