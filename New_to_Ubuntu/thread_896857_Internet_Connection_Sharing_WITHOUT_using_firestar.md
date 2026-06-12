---
title: "Internet Connection Sharing WITHOUT using firestarter"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by neurostu on 2008-08-21
I've got a group of computers that are all plugged into a switch. I then have a Controller computer that has two NIC's one is plugged into the building network and another is plugged into the switch.

I'd like to get internet connection sharing working over the two NICs on the Controller computer.  I had it working with firestarter but I hate messing with the policies under firestarter.  I pretty much <b>need</b> all ports open on the NIC that is plugged into the switch (btw they are open by default in ubuntu).

What is the easiest way to setup internet connection sharing without using firestarter?

---

### Post by ProgenitorVirus on 2008-08-21
Does it NEED to be ICS, or can it be a Network Bridge?

---

### Post by neurostu on 2008-08-21
> **ProgenitorVirus said:**
> Does it NEED to be ICS, or can it be a Network Bridge?
I really don't care ... I just need all computers plugged into the switch to be able to connect to remote locations (outside the lan)

---

### Post by ProgenitorVirus on 2008-08-21
Install bridge-utils through Synaptic


Stop your network


sudo /etc/init.d/networking stop


Edit your interfaces file


gksu gedit /etc/network/interfaces


Edit your interfaces file to look like:


auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1


Then restart your network


sudo /etc/init.d/networking start


It will take longer to start up, because it has to make the bridge, but it works fine

---

### Post by neurostu on 2008-08-21
so what exactly is an internet connection bridge? and how does it differ from internet connection sharing?

---

### Post by ProgenitorVirus on 2008-08-21
Pretty much they both do the same thing, only with ICS, you're sharing the same connection, with a bridge, its almost acting as a software network switch.  Both have about the same effect.

ICS assigns the client a static IP, usually 192.168.0.1 is saved for ICS, but with a Network Bridge, its that is simply acts like a crossover, they both use the same connection.  I find its also easier to share files over a bridge than ICS.

A bridge though, is less secure, mainly in a Windows environment, but much easier to configure and manage than ICS, which I've always had an issue with one thing or another.  Just be sure to have some sort of firewall up.

---

### Post by majornoob on 2008-09-10
Can I somehow do this and still use Network Manager to control the wireless interface?

---

### Post by neurostu on 2008-09-12
Majornoob, I don't know, but please post your question in a new thread. Its generally considered bad etiquette to resurrect an old thread with a new question, and besides you'll get better visibility and responses if you post your exact question in a new thread, with a complete description of what you're trying to do.

---

