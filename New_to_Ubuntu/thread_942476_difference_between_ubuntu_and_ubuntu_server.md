---
title: "difference between ubuntu and ubuntu server"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-10-09
hi all,

what exactly is the difference between ubuntu desktop and ubuntu server edition. 

i know ubuntu desktop runs in desktops and ubuntu servers run in servers.
but ... i am truly confused by the term **"server"**. i guess server is **" a machine with high computing capacity and high storage capacity"**.some say server is a software(in case of apache) and in another context they same term as machines..can you explain
...
what is going to make the difference if you run ubuntu desktop edition in servers and ubuntu server edition in ubuntu desktops.....

---

### Post by aeiah on 2008-10-09
the difference between any desktop and any server is really about usage. in terms of ubuntu, the ubuntu desktop distro has all the things for desktop usage (that doesnt mean you cant configure and install things to use it as a server) and ubuntu server likewise it has all things pre-installed for server usage (apache for web, php, mysql, email server stuff etc). ubuntu server also doesnt come with a desktop environment like gnome or kde, just a command line interface. you can of course install a desktop environment afterwards.

i think the only reason that ubuntu splits this up is because it is focused on supplying a livecd and install package all on one 700mb cd, and if it did what say, fedora does, it would have to use a dvd, like fedora does.

fedora has all the server software and all the desktop environment and desktop software stuff all on one disk. you choose before installation what parts you want to install. ubuntu just chooses to split things up so it can all fit on 700mb cds

---

### Post by _sAm_ on 2008-10-09
They use the term «*server*» on different things. Your Ubuntu desktop can act as an server, just start VLC and stram a video on the LAN or www and it will be a «server». 

As I understand it the major different between Ubuntu Desktop And Ubuntu Server is the kernel they use, and of course Ubuntu Desktop comes with GUI. The server also has others packages then the desktop version, like ssh and so on. 

I installed Ubuntu Desktop on my pc, witch use a Intel Duo cpu. I have later changed the kernel to the one used in Ubuntu Server since I read it supports better new cpu with dualcore. I don't know if it is true, and cant say I have noticed any big different.

---

### Post by luckydeveloper on 2008-10-09
suppose i have a LAN with 10 desktop and one server machine(with lots of computing power and storage capacity) . then i would install ubuntu server edition in tat server and ubuntu desktop edition on all those clients.. 

(or)

suppose i want to self host my website, then i shud rent or buy a server and install ubuntu server edition .....

is this how i must ubuntu server edition,,, am i right?

---

### Post by jerome1232 on 2008-10-09
> **luckydeveloper said:**
> suppose i have a LAN with 10 desktop and one server machine(with lots of computing power and storage capacity) . then i would install ubuntu server edition in tat server and ubuntu desktop edition on all those clients.. 

(or)

suppose i want to self host my website, then i shud rent or buy a server and install ubuntu server edition .....

is this how i must ubuntu server edition,,, am i right?

I just wanted to point out that servers don't need to be powerful or have alot of storage capacity. I use an old box I have; Celeron mmx 400mhz, 112 MB SDRAM, 5 GB Pata disk as a teamspeak/dhcp/bind9/ssh server and it fills that role beautifully. Only uses 45% of it's ram to run it's apps.

Any computer that has programs designed to provide services to other computers is a 'server'.

---

### Post by _sAm_ on 2008-10-09
You define a "server" has "a machine with high computing capacity and high storage capacity". 

This is only partly true, a server could use great hardware but it don't need to. You can pick up an old pc with low spec and use it as an server. Just take a look on the system requirements here: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Witch hardware you need depends on what you gonna use the server for. If its only gonna share files for those 10clients you talked about then you don't need much.

---

### Post by luckydeveloper on 2008-10-09
ok.. what if i want to host my website or my cool web application in my own machine or any other machine(if i need to buy for the sake of it)....what should i do in that case

---

### Post by Ryadt on 2008-10-09
> **luckydeveloper said:**
> ok.. what if i want to host my website or my cool web application in my own machine or any other machine(if i need to buy for the sake of it)....what should i do in that case
Install LAMP server on the desktop edition.

---

### Post by H.Callahan on 2008-10-09
Ubuntu gurus, please correct me if I am wrong, but isn't there some difference in memory usage or something with like that between the two versions?

---

### Post by jerome1232 on 2008-10-09
> **H.Callahan said:**
> Ubuntu gurus, please correct me if I am wrong, but isn't there some difference in memory usage or something with like that between the two versions?

A little bit, the server kernel has PAE enabled meaning a 32 bit computer that has a motherboard that supports PAE can address 4GB's of ram.

It has some optimizations and such for a server, you can install the server kernel on a desktop edition.

---

### Post by amauk on 2008-10-09
> **H.Callahan said:**
> Ubuntu gurus, please correct me if I am wrong, but isn't there some difference in memory usage or something with like that between the two versions?
AFIAK
the desktop version uses the generic kernel, while the server version uses the server kernel

generic kernel is better suited for desktop use
while the server kernel prioritises things for background daemons (server apps)

---

### Post by Nxion on 2008-10-09
> **luckydeveloper said:**
> ok.. what if i want to host my website or my cool web application in my own machine or any other machine(if i need to buy for the sake of it)....what should i do in that case

I say start out with the desktop edition. I started that way and when I was more comfortable I moved to a GUI-less environment. With the desktop edition you can run pretty much anything you can run on the server edition. And if you were going run a simple website then I would say you wouldn't need the server edition. 

I would say that you should use the server edition if you are starting to host multiple websites, hosting files or databases. With the server edition you would have better optimization for the processor and add more then the 4GB of memory.

Hope that helps, :)

---

### Post by hyper_ch on 2008-10-09
[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/kernel)

---

