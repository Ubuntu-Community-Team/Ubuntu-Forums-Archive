---
title: "I got a laptop for my birthday and..."
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Audrizzle on 2008-05-18
It came with Windows Vista installed already. I have a live CD for 
Ubuntu 7.10. I would like to dual boot them and I'm still new at this. I need to know how large to make each partition. I have a 160GB hard drive and 1GB of RAM. I've read that Vista has a way to partition already installed. Is that the best way to go? If so, how do I use that? 

I really don't want to ruin my new laptop, so simple, clear, step-by-step instructions would be useful and most appreciated. 

Thanks.

---

### Post by Twitch6000 on 2008-05-18
> **Audrizzle said:**
> It came with Windows Vista installed already. I have a live CD for 
Ubuntu 7.10. I would like to dual boot them and I'm still new at this. I need to know how large to make each partition. I have a 160GB hard drive and 1GB of RAM. I've read that Vista has a way to partition already installed. Is that the best way to go? If so, how do I use that? 

I really don't want to ruin my new laptop, so simple, clear, step-by-step instructions would be useful and most appreciated. 

Thanks.

Well that vista partition tool I am not sure of.Altough this guide can help you out step by step very well.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
I would suggest downloading parted magic for partitioning though as it is better at doing that =].

---

### Post by Audrizzle on 2008-05-18
I see that the guide is written for 7.04. Does everything in it still work for 7.10?

---

### Post by Shazaam on 2008-05-18
Is the laptop still under warranty?
IMHO if it is I would recommend running Ubuntu as a virtual machine until you get used to it (Ubuntu). Use any virtualization program you want. That way if an install goes bad you don't have to worry about Vista getting trashed.

---

### Post by meierfra. on 2008-05-18
Don't use parted magic  or gparted for a Vista partition.  It can ruin it. Use  Vista build in partitioner instead.

> 
I see that the guide is written for 7.04. Does everything in it still work for 7.10?


Yes.

---

### Post by Audrizzle on 2008-05-18
In that guide it says nothing about creating a swap partition. Does it just do that automatically? Should I click manual and create it myself? And how large does it need to be?

---

### Post by teaker1s on 2008-05-18
firstly happy birthday.

 I would recommend trying the live cd, this will make no changes to your vista install and will allow you to see what works and what doesn't

in live ubuntu
applications>accessories>terminal


```

lspci -v
```

```

lsusb
```

copy output to a flash drive or if you can get on internet through live cd post directly into a reply.

As and when you feel happy to install ubuntu I would recommend
vista defrag and run
Code:

```
chdsk /f
```

then this guide

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by Audrizzle on 2008-05-18
Okay, so this is what I need to know:

How many partitions do I need?
How big does each one need to be?
What do I name them?

Exact, clear answers are, again, appreciated.

---

### Post by teaker1s on 2008-05-18
the guide I suggested will give clear guided partition help

---

### Post by akiratheoni on 2008-05-18
> **Audrizzle said:**
> Okay, so this is what I need to know:

How many partitions do I need?
How big does each one need to be?
What do I name them?

Exact, clear answers are, again, appreciated.

I advise you have:
1 Vista Partition
1 / partition
1 /home partition
1 swap partition.

Each partition can be as much as you want it to be although with 160GB, i would personally put:
Vista partition: 60GB
/ partition: 15GB
/home partition: 83GB or 84GB (depending on swap)
swap: 2GB or 1GB

Swap is generally 2x your RAM but I've always heard that 1GB is just about enough, although you can bump it to 2GB if you need to (I have mine at 4GB, don't ask me why, lol).

As for names, it doesn't exactly matter.

Hope this helps. If you have any other questions, feel free to ask more, I'm happy to help :)

---

### Post by Audrizzle on 2008-05-18
Thank you very much. But again, that guide says nothing about a swap partition. Do I even need one?

---

### Post by akiratheoni on 2008-05-18
> **Audrizzle said:**
> Thank you very much. But again, that guide says nothing about a swap partition. Do I even need one?

Yeah, I advise you do, even if the guide doesn't say it. Like I said it should be about 2x your RAM.

---

### Post by Audrizzle on 2008-05-18
I used the Vista partitioner to shrink the Vista partition and this is what I ended up with:

Vista: 88.77GB
Unallocated: 48.83GB
Presario RP ( D: ): 9.99GB
Unallocated: 1.47GB

Will this work if I install Ubuntu?

---

### Post by akiratheoni on 2008-05-18
> **Audrizzle said:**
> I used the Vista partitioner to shrink the Vista partition and this is what I ended up with:

Vista: 88.77GB
Unallocated: 48.83GB
Presario RP ( D: ): 9.99GB
Unallocated: 1.47GB

Will this work if I install Ubuntu?

As far as I know about partitions, that should work. Make sure you split up the unallocated partition for a / partition and a /home partition... the / partition can be less than 20GB... maybe even as little as 10GB. Trust me, it will make reinstalling Ubuntu cause less headaches :)

---

### Post by Audrizzle on 2008-05-18
Thanks for all your help. I'll probably be back in a couple days to let you know if it worked. Either that or I'll be asking for more help.

---

### Post by teaker1s on 2008-05-18
guided partitioning ubuntu will decide for you

---

### Post by axor1337 on 2008-05-18
for a first time dual boot i would leave out the home part

---

