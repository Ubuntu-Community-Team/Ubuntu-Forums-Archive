---
title: "Home server connectivity"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by pirsmark on 2013-07-08
Hello


I would kindly ask you for some help.


Problem:
I live in a house with 2 floors. My wish is to make home server to store data, make backups, streaming media…
In first floor I have two TVs in two rooms and also the same in second floor. I have one desktop computer in each floor and 3 laptops.
My wishes are:
1.	to be able to watch HD movies from server computer to all TVs (have one disc in server with multimedia that everybody have access to it)
2.	have 4 more discs to make backup data from desktop and laptop (one disc access only me, one my wife and one my son – just private or job data)


So is this possible to do wireless without cables? 
If it is not can you tell me how to do it as I am not really expert (hardware, software...)?


Thanks a lot!
Mark

---

### Post by papibe on 2013-07-08
Hi pirsmark. Welcome to the forum ):P

> **pirsmark said:**
> So is this possible to do wireless without cables?
Very possible, however you would need modern and fast wireless hardware.

For a truly full HD (1080p) stream/share you would need a 'N' wireless router with a very good range. The clients (the machines that plays the media) would also need a 'N' wireless card.

The server does not need to be wireless, and you would have better speed transfers if it is wired to the router (ethernet cable).

Another thought: it is not that expensive nor difficult to wire the minimum connections for a house.

> **pirsmark said:**
> If it is not can you tell me how to do it as I am not really expert (hardware, software...)?
A few tips:
[LIST]
[*]For the server you can install either Ubuntu Server or the Desktop edition. All services can be set up on any version. It is a matter of preferences (experience with the command line), or resources (Desktop need more RAM).
[*]If the clients are computers, use shares instead of streaming. Both samba (Windows protocol), or NFS (Linux/Mac/Windows Ultimate) will work for that.
[*]In case you have game consoles that can play a stream, take a look at mediatomb.
[*]For the client side I recommend XBMC, as will play almost any format, and the interface is very easy to use (Alternative: plex).
[*]Clients must be relative modern computers in order to reproduce smoothly full HD.
[/LIST]
I hope that helps. Let us know if you need more help with that.
Regards.

---

### Post by pirsmark on 2013-07-08
Papibe thanks a lot for your quick reply and welcome wishes!

I am glad to hear that this is posible to do :)
So i am really begginer in all of this things but i would like to learn. 

Maybe can you suggest what kind of server to build to be able to process this things (which processor, disks,....)
Which router do you sugest?

I will check your tips...

p.s sorry but my english is not perfect

---

### Post by papibe on 2013-07-09
You don't need much processor power to serve files, even if they are big files (HD movies).

I have a setup similar to the one you want. My server is a refurbished P4, and my XBMC clients are a Raspberri PI running Raspbmc, and an Ubuntu Desktop machine on a Pentium D (Dual Core). All wired though.

Mostly any computer will do the job. If you want to save power you can get an Atom processor for instance.

If I had to build a server, I would go for something like:
[LIST]
[*]Intel i3.
[*]1Gb RAM.
[*]A motherboard that allows 4 to 6 Sata disks (or the ones you need).
[/LIST]
Does that help?

Regards.

---

### Post by pirsmark on 2013-07-09
ok thanks for all information.

---

