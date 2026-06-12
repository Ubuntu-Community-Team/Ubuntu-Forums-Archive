---
title: "File Server?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by onlyproductions on 2008-11-06
I want to share some files that i have on a computer over the Internet.
I would like to be able to connect to server on my mac at school type in the ip of my linux comp and get the certain files that i want from my linux comp.

how would i go about doing this

---

### Post by DGortze380 on 2008-11-06
> **onlyproductions said:**
> I want to share some files that i have on a computer over the Internet.
I would like to be able to connect to server on my mac at school type in the ip of my linux comp and get the certain files that i want from my linux comp.

how would i go about doing this

Make some choices:

Static IP from ISP  or dyndns (or similar)
SFTP  or  Samba
SSH   or  VNC

That should get you started on some google searched.

---

### Post by onlyproductions on 2008-11-06
> **DGortze380 said:**
> Make some choices:

Static IP from ISP  or dyndns (or similar)
SFTP  or  Samba
SSH   or  VNC

That should get you started on some google searched.

what would you reccomend?
and doesnt vnc just allow another user to share or control the other users screen

---

### Post by kerpow on 2008-11-06
The first (and last) thing to consider here is security.  You need to make sure your computers are protected against anyone else connecting to them, and you need to concider that there may be firewalls etc between the two machines (like your schools one) that might get in the way.

I am assuming that both machines belong to you (or are under your control) and that the mac in question is a laptop that you sometimes have at home on the network (let me know if that is not the case).

Try this:

Install Hamachi on both the machines you want to connect.
[https://secure.logmein.com/products/hamachi/vpn.asp?lang=en](https://secure.logmein.com/products/hamachi/vpn.asp?lang=en)
(Its small, free, cross-platform and I trust it.)

Follow the instructions from Hamachi on setting up a private virtual network and get both machines to connect.

Once this is done both machines will be able to talk to each other from anywhere as long as you have the private network enabled.  Also it will punch a hole in many firewalls you may encounter.

As the machines are now connected, you can go ahead and share files etc as you would if the machines where both on the network at home.

---

### Post by DGortze380 on 2008-11-07
> **onlyproductions said:**
> what would you reccomend?
and doesnt vnc just allow another user to share or control the other users screen

You are right, I'm sorry, mistype. I meant VPN not VNC.

I run dyndns, and ssh. Too big of a topic to really suggest anything useful. Research those few things and post back with any specific questions you have.

---

### Post by mapes12 on 2008-11-07
This HowTo may help:

[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

---

### Post by cmittle on 2008-11-07
proftpd and fireftp

---

