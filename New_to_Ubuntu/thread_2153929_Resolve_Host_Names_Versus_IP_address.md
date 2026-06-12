---
title: "Resolve Host Names Versus IP address"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by bjackfly on 2013-06-12
Hi, I recently setup ubuntu 13.04 on my hp laptop, I have a windows xp machine and a linksys router with some switches connected in between.  Can someone tell me how I can have each computer resolve the other's hostname without having to make a manual entry in the hosts file on each computer?  I am using putty to connect to the laptop but I need to use the ip address for everything which is setup using dhcp so this can change even though I can set the router to hold (reserve) the ip address for that machine.  Any help is most appreciated.  I ideally I would be able to just type in the hostname in the putty session or type ping <xphost name> from the linux laptop and have that work.  Everything is working I just need to type ips addresses. I saw somewhere about setting up a local dns but I wasn't sure if I needed to actually do this and they showed something called bind9 but this looked like a lot of overhead so I thought I would ask first.  Thanks so much for your help, I appreciate it.

---

### Post by Cheesehead on 2013-06-12
Yes, bind9 will do what you describe. [https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto) can help you.

There is indeed some setup work for bind9, but there will be for *any* solution. It's a complex problem that you say you want to solve in one specific (complex) way. Your problem description seems to value a single central solution more than install convenience.

---

### Post by Iowan on 2013-06-12
I have a server on my network running **dnsmasq** as a DHCP server. It also keeps track of machine names, so I can use machine names even with DHCP leases. This machine is rather old - I haven't tried to set up anything similar on a current machine.

---

### Post by bjackfly on 2013-06-12
I don't mind installing I just wanted to make sure I was going down the right path such that all systems would get to use name versus ip resolution.  Is there anything specific I would have to do to configure each computer to use this dns? I guess I can venture into that once I go through the install.

---

### Post by bjackfly on 2013-06-12
Does dnsmasq work for all of your machines even when you add new ones to the network?  Is there a way to see the machines in MyNetwork and or similar Ubuntu tool or is that a different problem / configuration.

---

### Post by Iowan on 2013-06-12
Well, I **thought** */etc/dhcp/dhclient.conf* needed to be modified to send the appropriate hostname, but I just fired up my laptop, and could ping it by name with the default */etc/dhcp/dhclient.conf*.

Although one probably exists, I'm not sure what tool lists network occupants.

---

