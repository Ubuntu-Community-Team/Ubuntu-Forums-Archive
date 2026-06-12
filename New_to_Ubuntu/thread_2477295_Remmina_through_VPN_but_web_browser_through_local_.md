---
title: "Remmina through VPN but web browser through local connection."
date: 2022-07-20
forum: New to Ubuntu
---

### Post by rc-brooks on 2022-07-20
What is the best approach to route my Remote Desktop through my work VPN (Cisco Anyconnect), but route my local web browser through my local connection (skipping Cisco)?

---

### Post by TheFu on 2022-07-20
> **rc-brooks said:**
> What is the best approach to route my Remote Desktop through my work VPN (Cisco Anyconnect), but route my local web browser through my local connection (skipping Cisco)?

It may not be possible. Most places that use Anyconnect will prevent what is called "split tunnels" for security reasons. Basically, it extends the work VPN network to your computer.

If you don't like that, there are a few choices.
a) Use a different computer.
b) Put the work computer with the VPN inside a virtual machine and access the internet you don't want to go through the VPN from the host or a different VM.

To see if AnyConnect or any other VPN doesn't allow split tunnels, after connecting to the VPN, look at the routing table.  **ip route |column -t** will show it.

Why use Remmina?  Is the overhead of that bloated software worth eating an extra 500MB of RAM?

---

### Post by rc-brooks on 2022-07-20
Thank you. A virtual machine was my first thought to be honest. It wasn't a problem before, but after a ransom attack earlier this year, they've choked it down so much, I'd like to run my browser off my local connection. Regarding Remmina, it was the most recommended software. I'm not dedicated to it, what is your recommendation?

---

### Post by rc-brooks on 2022-07-20
This is what I'm looking at. I'm not familiar with the route tables, other than the IP addresses obviously.

```
default         dev  cscotun0     proto  unspec  scope   link
default         via  xxx.xxx.x.x  dev    enp8s0  proto   dhcp    metric  100
default         via  xxx.xxx.x.x  dev    wlp6s0  proto   dhcp    metric  600
xxx.xxx.x.x    via  xxx.xxx.x.x  dev    enp8s0  proto   unspec
xxx.xxx.x.x/16  dev  cscotun0     proto  unspec  scope   link
xxx.xxx.x.x/16  dev  enp8s0       scope  link    metric  1000
xxx.xxx.x.x/24  dev  cscotun0     proto  unspec  scope   link
xxx.xxx.x.x/24  dev  enp8s0       proto  kernel  scope   link    src     xxx.xxx.x.x  metric  100
xxx.xxx.x.x/24  dev  wlp6s0       proto  kernel  scope   link    src     xxx.xxx.x.x  metric  600
xxx.xxx.x.x     dev  enp8s0       proto  unspec  scope   link
```

---

### Post by TheFu on 2022-07-20
a) when posting terminal commands and output, use forum code tags. Otherwise is it unreadable.
b) routing tables without the actual information are useless.  The details matter.  That's sorta the entire point.

Good VPNs don't allow the client to set the routing table. It is all controlled on the server-side.

---

### Post by rc-brooks on 2022-07-20
That is the return for **ip route**, short of the static IP addresses, which I would not want to volunteer online. I wasn't paying attention and marked out the local ip, which wasn't necessary, but my work IP I did. You mentioned that ip route will show if the connection is capable of split tunneling. What am I looking for? 

What would you recommend for a Remote Desktop client?

---

### Post by TheFu on 2022-07-20
I use x2go about 0.001% of the time I need remote connections. The other 99.999%, I use ssh or setup an ssh-tunnel for the specific services desired.

As for recognizing when there is a split tunnel, that's something you can look up with that keyword. Or you can actually post the details.  IP addresses are never secrets.

---

