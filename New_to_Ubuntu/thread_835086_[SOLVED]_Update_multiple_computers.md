---
title: "[SOLVED] Update multiple computers?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Crusty Juggler on 2008-06-20
I've got two laptops and a desktop running Ubuntu and I was wondering if there is anyway to not have to download updates individually on each computer.  There have been a number of particularly large updates lately and I tend to run a bit thin on download quota towards the end of the month.

---

### Post by dracayr on 2008-06-20
> To download is to receive data from a remote or central system

Of course your computers need the data to update, and the only way to get it is to download it. You could of course download it on one computer and then download it tho the others via a local area network (LAN)

dracayr

---

### Post by fatality_uk on 2008-06-20
Here'd a quick guide for you
[http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/](http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/)

Essentially, you want to create a network addressesable copy of your /var/cache/apt/archives directory.
If you follow this link it should give you what you want and then the other PC's on your network will draw their updates from that directory instead of the internet.

---

### Post by hyper_ch on 2008-06-20
over NSF you could mount the /var/cache/apt of one computer into all others... so you can update from any computer and it will always be downloaded to the one that is being mounted... so you only need to download the stuff once.

Or you could setup a whole ubuntu mirror and then use it as source.

---

