---
title: "Networking"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Celect on 2008-05-01
How do you let one Ubuntu computer see another Ubuntu Computer? (Ubuntu 8.04)(Hardy Heron)

---

### Post by Paqman on 2008-05-01
If you just want to do it once you can go just browse to the other machine through Nautilus. If you want to connect permanently you'll have to add an entry to /etc/fstab, and it will mount automatically at boot.

---

### Post by mlentink on 2008-05-01
In nautilus, in the address-bar type "smb://name-of-other-machine", obviously without the quotes.
Please note that you won't actually be able to access that machine unless it has any shares defined. This you can easily do in 8.04 by right-clicking on a folder, selecting "sharing options", and then ticking the appropriate box. If filesharing is not already installed, ubuntu will ask you if it should install it.

---

### Post by Paqman on 2008-05-01
> **mlentink said:**
> In nautilus, in the address-bar type "smb://name-of-other-machine"

They're both Ubuntu machines, so no need for smb. NFS would be a lot better.

Alternatively you could use this [SSH method for sharing](http://ubuntuforums.org/showthread.php?t=742276)

---

### Post by hyper_ch on 2008-05-01
[https://wiki.ubuntu.com](https://wiki.ubuntu.com)

Search for NFS and/or SSHFS

There you find plenty of help :)

---

### Post by jdn-za on 2008-07-04
> **Celect said:**
> How do you let one Ubuntu computer see another Ubuntu Computer? (Ubuntu 8.04)(Hardy Heron)

Ola!

I am staying at my girlfriends place in kilenmond this weekend and would be happy to show you some basics. am busy doing an install on my tc1100

---

