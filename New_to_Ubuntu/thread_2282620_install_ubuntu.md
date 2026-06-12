---
title: "install ubuntu"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by bananelkerdi on 2015-06-15
Good morning,


I am trying to install ubuntu on a server, but on this server, in the past from 10 years ago 
we have installed linux red hat, I want Unstall this linux redhat and replace it with ubuntu 14.04.

But I need to transfer the data present in the server under linux redhat .

Can you help me to find a way to transfer the data out the server?


Best regards

---

### Post by Bashing-om on 2015-06-15
bananelkerdi; Hello; Welcome to the forum.

If it were me, I would:
Burn a liveDVD of ubuntu
Boot up the liveDVD to "try ubuntu" mode
In the live mode mount the target partitions
copy off the desired files to an exterior medium.

Now install the ubuntu server edition.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by mastablasta on 2015-06-16
it all depends on server configuration (RAID?) and also how much data you have. for smaller amounts it makes sense to do what bashing-om said. but with more data you might want to just install Ubuntu on some system disk, and then move data to your new server/drives from the old drives..

---

