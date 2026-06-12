---
title: "Gateway/firewall"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by AB34125 on 2008-05-05
i would like to build a pc to act as a stand alone firewall/gateway.  I would like it to determine what website cant be reached.  i have looked around the web and the closest I have found is [http://howtoforge.com/ubuntu6.10_firewall_gateway](http://howtoforge.com/ubuntu6.10_firewall_gateway) but it is for 6.10.  is there any guides out there for 8.04?

thanks in Advance

---

### Post by Sparkalo on 2008-05-05
Wow, that sure is a long tutorial you linked to.  At the moment, I can't find an updated version of the tutorial, so the way I see it, you're left with a couple of options.

Option 1: The Easy Way
If all you're going to be doing with this machine is blocking websites, you may not need to be on the cutting edge of Ubuntu distributions.  Have you considered simply installing 6.10 and then following the tutorial? You can get the old release from [http://old-releases.ubuntu.com/releases/edgy/]("http://old-releases.ubuntu.com/releases/edgy/")

Option 2: The Fun Way!
Although the distribution has been updated, there's really no reason that you still can't make the tutorial work.  Sure, some things are going to be different, but the concept of the tutorial is the same.  Follow the tutorial until you run into trouble and then, if you find yourself stumped, ask the Ubuntu community for help.  Why, you could even write an updated tutorial yourself!

---

### Post by AB34125 on 2008-05-05
Thanks Sparkalo, 

After some more browsing I might go with something like IPCop or smoothwall.  Looks a lot easier.

---

### Post by MockY on 2008-06-01
I have been using SmoothWall for years and I highly recommend it. Especially now when 3.0 is out.

---

### Post by Dedoimedo on 2008-06-01
Hello,

That tutorial you posted goes way beyond the basic stuff.

1. You need a machine that will function as the firewall/gateway, with two network cards, one for external network and one for client machines on the local network.
2. On the gateway you need to setup ip forwarding.
3. On the gateway you need to enable firewall to forward and masquerade between internal network and external network.
4. On the gateway, you may consider setting up a dhcp server, but this is a bit advanced, so you can simply go for static ips for each client.
5. The gateway should have a static ip.
6. On each client, you should consider static ip address to make your setup easier and you need to specify the gateway as the gateway and the dns server.
7. Naturally, the gateway should have a working internet connection.

I know this is generic, but I hope it helps...

Cheers,
Dedoimedo

---

