---
title: "64 bit Ubuntu"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by pzs on 2008-06-30
This is a stupid question. Sorry.

I'm in the process of buying a new machine and was trying to work out whether I'd have any problems if I bought a 64 bit CPU. 

I checked the specs on my current machine, which has a Intel Core2 Duo and found that it already is 64 bit. 

Does this mean that when I put in the liveCD it just figured out it was 64 bit and installed itself appropriately, without me ever knowing? Where can I found out whether it's true 64 bit Ubuntu or some kind of emulated 32 bit mode?

---

### Post by overdrank on 2008-06-30
> **pzs said:**
> This is a stupid question. Sorry.

I'm in the process of buying a new machine and was trying to work out whether I'd have any problems if I bought a 64 bit CPU. 

I checked the specs on my current machine, which has a Intel Core2 Duo and found that it already is 64 bit. 

Does this mean that when I put in the liveCD it just figured out it was 64 bit and installed itself appropriately, without me ever knowing? Where can I found out whether it's true 64 bit Ubuntu or some kind of emulated 32 bit mode?

Hi and you can use the command in the terminal ```
uname -a
```
Example 
Linux overdrank-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x**_86_64_** GNU/Linux
If you would like to use 64bit you will need to download the 64bit cd and install.

---

### Post by WRDN on 2008-06-30
When you download Ubuntu, you are given the choice whether to download a 32bit or 64bit OS.
There isn't a disk with the choice to install one or the other.
Though you have a 64bit processor, it may still be worth installing a 32bit OS.

To decide which is best, you should ask yourself, what will you be using your PC for?

---

### Post by Vivaldi Gloria on 2008-06-30
> **pzs said:**
> 
Does this mean that when I put in the liveCD it just figured out it was 64 bit and installed itself appropriately, without me ever knowing? Where can I found out whether it's true 64 bit Ubuntu or some kind of emulated 32 bit mode?

There are two versions of ubuntu here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

One for 32bit computers and one for 64bit AMD and Intel computers. Both work fine with core2duo and other 64bit processors. 

You can learn which one you have by giving the command

```
uname -a
```

in a terminal. If it says

```
i686 GNU/Linux
```

at the end then it's 32bit, otherwise it's 64 bit.

See

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

for more on 32bit vs 64bit.

---

### Post by Canis familiaris on 2008-06-30
> **pzs said:**
> This is a stupid question. Sorry.

I'm in the process of buying a new machine and was trying to work out whether I'd have any problems if I bought a 64 bit CPU. 

I checked the specs on my current machine, which has a Intel Core2 Duo and found that it already is 64 bit. 

Does this mean that when I put in the liveCD it just figured out it was 64 bit and installed itself appropriately, without me ever knowing? Where can I found out whether it's true 64 bit Ubuntu or some kind of emulated 32 bit mode?

64bit cpu can run 32bit OSes as well, no probs in buying the CPU. The Intel Processors from Pentium 4(newer Prescotts, Cedar Mill, etc), Core 2 CPUs, most Xeons and AMD64 based CPUs are 64bit CPUs and will run Ubuntu very well whether you run Ubuntu(Intel x86) or Ubuntu(AMD 64).
But if you are buying the Intel Itanium which is also a 64bit CPU, then you will not be able to run Ubuntu. 
But you are surely not buying the Itanium?

---

### Post by pzs on 2008-06-30
```

[pzs@suemez /home/pzs]$ uname -m
i686

```

Thanks for your replies everybody. I probably won't get a machine with more than 4GB RAM and I'm not doing video or graphics work, so I'll probably go with 32 bit Ubuntu as my main install. I may install a 64 bit version alongside it to test it out.

---

### Post by Inxsible on 2008-06-30
Here's a great [link]("http://ubuntuforums.org/showthread.php?t=765428") to figure out yourself whether 64 bit will be useful to you or not.

NOTE : 64 bit support is not what it used to be. Most apps now come in 32 bit and 64 bit. So using 64 bit is NOT a problem at all. Eventually, everything will move towards 64 bit, just like it did from 16 to 32 :)

---

### Post by Vivaldi Gloria on 2008-06-30
```
I probably won't get a machine with more than 4GB RAM
```

FYI, you cannot use more than 3.5GB of ram with 32bit ubuntu. I have a 32bit machine with 4GB ram and this is what I get:

```
~$ cat /proc/meminfo | grep MemTotal
MemTotal:      3630976 kB
```

---

### Post by Canis familiaris on 2008-06-30
> **Inxsible said:**
> Here's a great [link]("http://ubuntuforums.org/showthread.php?t=765428") to figure out yourself whether 64 bit will be useful to you or not.

NOTE : 64 bit support is not what it used to be. Most apps now come in 32 bit and 64 bit. So using 64 bit is NOT a problem at all. Eventually, everything will move towards 64 bit, just like it did from 16 to 32 :)

At least in Linux.:popcorn:

---

### Post by hyper_ch on 2008-06-30
> **Vivaldi Gloria said:**
> FYI, you cannot use more than 3.5GB of ram with 32bit ubuntu.
You can, with PAE (which makes it actually 34bit)

---

### Post by Vivaldi Gloria on 2008-06-30
> **hyper_ch said:**
> You can, with PAE (which makes it actually 34bit)

Yeah, I forgot about that.

---

### Post by Canis familiaris on 2008-06-30
> **hyper_ch said:**
> You can, with PAE (which makes it actually 34bit)
But It will be easier to run the 64bit Ubuntu. Isn't it.

---

### Post by hyper_ch on 2008-06-30
well, if you use the server kernel then PAE is enabled by default... is you use the generic kernel you'll have to recompile it with PAE enabled...

So, on server editions it doesn't matter but on desktop editions it would be easier to use 64bit

---

### Post by Inxsible on 2008-06-30
A PAE enabled system would allow you access to 2^34 bytes = 64GB of address space.

A 64 bit system would allow you access to 2^64 bytes of address space.


Of course, unless you are building server farms and such, you probably will not have more than 4GB RAM. So the above becomes moot. But by using 64 bit - lets just say you are ready for the future ;-)

---

