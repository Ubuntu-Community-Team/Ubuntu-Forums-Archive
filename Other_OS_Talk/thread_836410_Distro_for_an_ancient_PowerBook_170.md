---
title: "Distro for an ancient PowerBook 170?"
date: 2008-06-21
forum: Other OS Talk
---

### Post by klange on 2008-06-21
So I have in my possession a PowerBook 170 (circa '91). It has a 25MHz Moto 68030 (yup, 68k), 2MB RAM and a 20MB HDD. The Mac OS 7 on it is somehow FUBARed, and I'm looking to get a distro on it. Don't particularly need X, though it would be nice.

Any ideas?

---

### Post by mips on 2008-06-21
[http://www.linux-m68k.org/](http://www.linux-m68k.org/)

Follow the links on the above page. NetBSD could also be an option.

The only issue I see is that you might not have enough ram but look that up.

---

### Post by zmjjmz on 2008-06-21
[http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook170.html](http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook170.html)

Says the standard RAM is 4MB.

---

### Post by mips on 2008-06-22
> **zmjjmz said:**
> [http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook170.html](http://www.everymac.com/systems/apple/powerbook/stats/mac_powerbook170.html)

Says the standard RAM is 4MB.


True and also not true. The very first models only came with 2MB. 

This was really not enough for System 7 and many people complained about this. Apple made the later models with 4MB.

---

### Post by klange on 2008-06-22
As it turns out, this particular PowerBook might be totally pimped out. Finder reports a 140MB disk size (wow!). Still unsure about the RAM and seriously have no clue how to check it.

Anyway, getting a distro on there sounds like a good project for next month.

---

### Post by mikjp on 2008-06-25
My vote goes for.... NetBSD! 

I've got Debian on my iBook, but it's got 600 Mhz + 384 MB... could not install Ubuntu on it.

---

### Post by starcannon on 2008-06-25
I have no advice to give, but I am going to subscribe to this thread. Please, oh please, let us know how you get on. I enjoy making jurrassic ware useful again, but have never ventured under the 133mhz line lol. I have read a few articles about 60-somthin mhz machines and damn small linux, but never heard of anyone trying to ressurect a 25mhz machine before.

Anyway, I think you have a really cool project on your hands. I wonder if it could handle the dillo web browser, thats super lite, theres liter ones out there, but dillo is really sweet for what it is.

P.S.

Oh, and there is a tiny x server, can't remember what its called off the top of my head, but they used to and still may use it in damn small linux, dig around in there for some tips on possible things that may go on your laptop.

---

### Post by zmjjmz on 2008-06-25
I highly doubt X will run on this.

---

### Post by Ptero-4 on 2008-06-25
Heck. I doubt that the normal linux kernel is gonna run on that (most 68k's lack the required "paged memory manager(PMMU)" hardware) although maybe ucLinux will run on it (quite slow, you can't use swap files/partitions, as they rely on the PMMU).

---

### Post by cardinals_fan on 2008-06-25
[SIZE="6"][COLOR="DarkOrange"]*Of course it runs NetBSD!*[/COLOR][/SIZE]

I'm thinking command-line only here... :)

---

### Post by zmjjmz on 2008-06-25
There are 68k distros, they're just _really old_

---

