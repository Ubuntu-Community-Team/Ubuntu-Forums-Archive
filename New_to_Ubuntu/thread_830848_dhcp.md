---
title: "dhcp"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by fnkhan on 2008-06-16
i want to configure dhcp in 2 networks pools but the main problem is group A user connect to 192.168.1.XX and group B user connect to 192.168.2.XX how i will do this with using mac of every pc.

---

### Post by Dedoimedo on 2008-06-16
Hello,

If you run the server and have access to it:

In this file /etc/dhcpd.conf

You need to add host directive for each relevant host:

host "hostname" {
   hardware ethernet ff:ff:ff:ff:ff:ff;
   fixed-address 192.168.x.x;
}

Example:

host "machine1" {
   hardware ethernet 0c:03:bb:1a:93:22;
   fixed-address 192.168.1.11;
}

This way, they'll lease the IPs from the server, based on their MACs.

Of course, you should be familiar with dhcp and how to run it, before you make any major changes. But if you need more help, do ask. Furthermore, always backup before making any change.

Cheers,
Dedoimedo

---

### Post by fnkhan on 2008-06-16
the problem is that i have more then 500 pcs in both network I want to enter automatically not enter the mac manually of these pcs.

If i'll enter the there's too much mac address.
do you have any other solution

---

### Post by Dedoimedo on 2008-06-17
Hi,

You might want to consider an enterprise level solution, like a CISCO router with all sorts of thingiemaggie.

Now, do you need per-host configuration as a security measure or simply to separate the two pools of hosts?

Maybe this could work:

Two network cards, with different IPs, each serving a different subnet. Then a firewall rule to allow only particular subnet on specific network card.

Then, you can use the pool statement to lease different IPs to each group.

But this means you have two physical connection grids. If they sit on the same net, this becomes more complicated. I can't think of anything smart now to make the DHCP server recognize certain hosts as X and others as Y, if they are on the same physical network, without the host declaration.

Dedoimedo

---

