---
title: "Port-forwarding help?"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-11-25
So I've successfully set up a Minecraft server, using the basic server download off of minecraft.net. And it runs fine; but only on my computer.

I've seen numerous places that say I need to port-forward my server, but I can't seem to find any useful/noob-friendly instructions on how to go about this whole port-forwarding business, not even on the Minecraft forums.
So I decided to come here, since I can, time and time again, get reliable, quick, and (most importantly) noob-friendly help.

So can anyone tell me how to port-forward?

Useful Info?:
I'm using a 2Wire Gateway Router/Modem, 2701HG, provided by Windstream. No, I don't connect directly by cable, it's a wireless network.

P.S. It probably doesn't help that I hardly understand what port-forwarding is; I've read a bit about it, and I basically get what it is, but I still find it a little confusing.

---

### Post by haqking on 2011-11-25
> **DaimyoKirby said:**
> So I've successfully set up a Minecraft server, using the basic server download off of minecraft.net. And it runs fine; but only on my computer.

I've seen numerous places that say I need to port-forward my server, but I can't seem to find any useful/noob-friendly instructions on how to go about this whole port-forwarding business, not even on the Minecraft forums.
So I decided to come here, since I can, time and time again, get reliable, quick, and (most importantly) noob-friendly help.

So can anyone tell me how to port-forward?

Useful Info?:
I'm using a 2Wire Gateway Router/Modem, 2701HG, provided by Windstream. No, I don't connect directly by cable, it's a wireless network.

P.S. It probably doesn't help that I hardly understand what port-forwarding is; I've read a bit about it, and I basically get what it is, but I still find it a little confusing.

It means whatevers ports that Minecraft use (i dont know and will let you find that out) you need to make sure any firewall allows the traffic on those ports.  Portforwarding is to make sure that your router/modem takes traffic destined for those ports and forwards it to your machine/server.

So for example:

your router is 192.168.0.1 and your machine is 192.168.0.2

on your router 192.168.0.1 you need to make sure than any traffic that comes into it on its WAN interface (the bit facing the internet) to say port 80 is forwarded to your machine/server 192.168.0.2 which in this example would be if your server/machine is running a website (port 80)

you need to do this for the minecraft ports and will depend on your router/modem, somewhere on its interface there will be a port forwarding section/applications etc.

here is a guide using your modem/router forwarding limewire [http://portforward.com/english/routers/port_forwarding/2wire/2701HG-B/Limewire.htm](http://portforward.com/english/routers/port_forwarding/2wire/2701HG-B/Limewire.htm)

you need to change the ports to suit minecraft and not limewire

Enjoy

---

### Post by DaimyoKirby on 2011-11-25
Sorry, accidental post:oops:...

---

