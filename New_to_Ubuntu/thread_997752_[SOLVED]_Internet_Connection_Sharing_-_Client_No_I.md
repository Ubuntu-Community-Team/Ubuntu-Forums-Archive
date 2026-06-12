---
title: "[SOLVED] Internet Connection Sharing - Client No IP"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by spikoley on 2008-11-30
I have set up internet connection sharing, but the client cannot get an IP address.  The network manage shows it connected but there is no IP address.  I have tried manually setting it up and using dhcp.  Any ideas? I am running Ibex on both machines. Thanks.

---

### Post by drubin on 2008-11-30
> **spikoley said:**
> I have set up internet connection sharing, but the client cannot get an IP address.  The network manage shows it connected but there is no IP address.  I have tried manually setting it up and using dhcp.  Any ideas? I am running Ibex on both machines. Thanks.

Have you tried manually assigning the computers ip address. Click on networks, properties, from the drop down static ip. Make the the 2 ip addresses are unique.

---

### Post by spikoley on 2008-11-30
> **drubin said:**
> Have you tried manually assigning the computers ip address. Click on networks, properties, from the drop down static ip. Make the the 2 ip addresses are unique.

Yes I have.  Do I need a crossover cable if I am hooking up ethernet to ethernet?

---

### Post by drubin on 2008-11-30
> **spikoley said:**
> Yes I have.  Do I need a crossover cable if I am hooking up ethernet to ethernet?

Cross over is only from computer to computer or hub to hub, but now days the hubs are clever enough to switch them around so you only need normal cables.

---

### Post by razy60 on 2008-11-30
are you using a router or hub to connect the pc's,
When you click on: Places-network. What does it show?

---

### Post by drubin on 2008-11-30
Ok best idea I can think about is to do post the output of these commands

```
sudo ifconfig -a
```

```
sudo cat /etc/resolv.conf
```

---

### Post by spikoley on 2008-12-02
> **drubin said:**
> Cross over is only from computer to computer or hub to hub, but now days the hubs are clever enough to switch them around so you only need normal cables.

I am connecting two computers directly.  It sounds like this is the issue.  Hopefully tomorrow I will have the time to pick up a crossover cable.  Thanks for your help.

---

### Post by spikoley on 2009-01-03
It was the cable.  I got a cross over cable and now both machines can communicate with each other.  But, when they are connected neither of them can reach the internet.  When I unplug the connection, the computer connected to the internet can surf.  I connect the 2 computers together and both of them cannot reach the internet.  This sounds like a route issue.  Any ideas on how to solve it?  Thanks.

---

### Post by spikoley on 2009-01-03
Got it working.  I had to run these commands again.

```
iptables -t nat -F
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

BTW, eth0 = the interface connected to the internet.  This [post]("http://ubuntuforums.org/showpost.php?p=6408893&postcount=2") resolved it.

---

