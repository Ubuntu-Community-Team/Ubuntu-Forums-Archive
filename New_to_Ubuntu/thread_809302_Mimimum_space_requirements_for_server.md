---
title: "Mimimum space requirements for server?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Cadmus on 2008-05-27
Hopefully this should be a simple one, I've inherited an old server with
[LIST]
[*]Xeon 3 GHz processor
[*]2GB RAM
[*]2x 36GB HDs
[/LIST]

And I'm going to use it to do some experimenting. 

My real question is how much space should I use for the root installation? I'm probably going to use 4GB for swap (never know what I may use this for) but if (as looks likely) I'm going to use hardware RAID 1 space is going to be at a premium, so assuming I install at most Apache, MySQL, PHP, Samba, DHCP Server, and FTP Server what sort of space am I looking at?

Don't worry about data produced by these (such as websites or databases) as I'll be putting them in an lvm, possibly using iSCSI, so I'm just concerned about the space for the OS and applications.

---

### Post by billgoldberg on 2008-05-27
> **Cadmus said:**
> Hopefully this should be a simple one, I've inherited an old server with
[LIST]
[*]Xeon 3 GHz processor
[*]2GB RAM
[*]2x 36GB HDs
[/LIST]

And I'm going to use it to do some experimenting. 

My real question is how much space should I use for the root installation? I'm probably going to use 4GB for swap (never know what I may use this for) but if (as looks likely) I'm going to use hardware RAID 1 space is going to be at a premium, so assuming I install at most Apache, MySQL, PHP, Samba, DHCP Server, and FTP Server what sort of space am I looking at?

Don't worry about data produced by these (such as websites or databases) as I'll be putting them in an lvm, possibly using iSCSI, so I'm just concerned about the space for the OS and applications.

10gb (you should be good with 5gb or even less, but 10gb is safer)

---

### Post by Cadmus on 2008-05-27
10GB is more than I was expecting, but I suppose it still leaves me with 22GB for data after 4GB of swap. Pleanty for toy sites and DBs, maybe even enough to play with rtorrent for a few ISOs of Ubuntu.

Cheers :)

---

### Post by billgoldberg on 2008-05-27
> **Cadmus said:**
> 10GB is more than I was expecting, but I suppose it still leaves me with 22GB for data after 4GB of swap. Pleanty for toy sites and DBs, maybe even enough to play with rtorrent for a few ISOs of Ubuntu.

Cheers :)

Oh, if you have little harddrive space, than 3-5 gb should do fine.

With 10 gb you have some more breathing space, but you shouldn't need that much.

---

### Post by bodhi.zazen on 2008-05-27
The base for a server can be very small. I have run a server with LAMP in as little as 400 Mb. (Data is obviously larger).

The less you have installed, the less tools for crackers.

---

