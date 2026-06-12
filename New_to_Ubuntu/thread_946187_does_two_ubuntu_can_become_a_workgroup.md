---
title: "does two ubuntu can become a workgroup?"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by legolas_w on 2008-10-13
Hi
Thank you for reading my post.
In windows we could setup two computers to become workgroup member and then we could share files, printer, internet, etc.
is it possible for two ubuntu machine to share internet, files, printer,... ?
I mean how I can setup a network between two ubuntu system?

Thanks

---

### Post by Pro-reason on 2008-10-13
As far as I understand you, yes.

I have a router and multiple computers.  They all connect to the router and form a Local Area Network.  I can then use ssh to perform a variety of networking tasks.

---

### Post by legolas_w on 2008-10-13
So, Things like opening the other computer shared folders in the file explorer is not possible in linux networks?

Thanks

---

### Post by newlinux on 2008-10-13
yes, you can share files using the same protocols as windows if you like. I have a mixed network of windows, macs, and linux and can share files from any of them.

There are many ways to share folders, depending on your needs.I believe you can share folders using nautilus.

[http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/](http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/) is one way...

---

### Post by The Cog on 2008-10-13
Yes it is possible. But you need to install some file-sharing software such as sshd, samba (wndows file sharing protocol) or nfs (unix file sharing protocol). Ubuntu doesn't share files by default - too much of a security risk.

---

### Post by anewguy on 2008-10-13
The Cog - is that a Cray you have an Ubuntu logo on for your avatar?  I like it!

---

### Post by The Cog on 2008-10-14
Well spotted. Yes, I remember when a Cray 1 was **the** iconic supercomputer. Of course, no way did it have the memory needed to run Ubuntu. And I'm not even sure which model that is a picture of. There's no seat round it, so it may not be a cray-1.


Edit:
I think you probably thanked the wrong message there. Never mind.
I found that it's actually a picture of a Cray-2. I might have too correct that.

---

### Post by Kellemora on 2008-10-14
Hi Leg

If you only have TWO computers and NO Router, you WILL need to use a CROSSOVER type of LAN cable or a crossover connector to set up your system as Peer to Peer.  Not as robust as a normal LAN but works nearly the same.

I would suggest that you do pick up a Router as you ARE going to want to expand your system once you find out how easy using a LAN is over trying to make your computers do everything.

I have 8 computers here, 3 are in use, the others are for specific purposes, like print server, file storage, archives, etc.
Yeah I know an external Terrabyte Drive could replace 3 to 4 of our computers, hi hi.......  But they are also for redundant backups.

Even with 8 computers, we are still only using TWO of the Router Ports, one for the house system and one for the office systems.  Hubs handle all the workgroup computers and saves a LOT of Cat5 over long distances, hi hi.....

I'm trying to learn about Servers as I think it may make things even better than how we have it set up now!
And with computers at a dime a dozen these days, under my desks looks like a ladies shoe closet, hi hi.......

TTUL
Gary

---

