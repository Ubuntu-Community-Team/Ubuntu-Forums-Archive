---
title: "Cant connect to internet"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by danielhemple on 2008-08-07
Hey everyone..I just installed Dapper Drake..and I am having a lot of trouble connecting to my wireless network. Can any one guide me through getting connected. 

This is what happens when I try to connect..It just takes forever..and then does not connect (i know my password is correct) and then when i click on the network connections tab an error message pops up. 
 " Please contact your system administrator to resolve the following problem: SIOCGIFFLAGS error: No Such Device."

Can someone guide me through the terminal to fix this. My network is fine..I can run windows on it fine..
Thanks in advance!

---

### Post by nothingspecial on 2008-08-07
> **danielhemple said:**
> Hey everyone..I just installed Dapper Drake..and I am having a lot of trouble connecting to my wireless network. Can any one guide me through getting connected. 

This is what happens when I try to connect..It just takes forever..and then does not connect (i know my password is correct) and then when i click on the network connections tab an error message pops up. 
 " Please contact your system administrator to resolve the following problem: SIOCGIFFLAGS error: No Such Device."

Can someone guide me through the terminal to fix this. My network is fine..I can run windows on it fine..
Thanks in advance!

Try installing something newer. :)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by Tatty on 2008-08-07
Dapper Drake is a very old distro now, i believe it is still supported, but its support cycle is nearing its end.

As nothingspecial said, it may be worth installing a newer version of ubuntu (the latest LTS edition is Hardy Heron).

If you want to use Dapper then im sure someone could assist you, but its been so long since i used it that I wouldnt know where to begin :)

---

### Post by Immolatus on 2008-08-07
What machine is it and what is the wireless card? I haven't seen a SIOCGIFFLAGS error since I was working in Fedora over a year ago. Ubuntu has had drivers for the Atheros and intel wifi cards out of the box since before dapper, I would presume that it had more to do with the card than the distro.
What it is telling you is that the kernel cannot access the hardware (wireless card). It needs the firmware to do so.

---

