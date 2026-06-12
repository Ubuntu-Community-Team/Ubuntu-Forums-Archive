---
title: "x86 or AMD64 for Intel Atom D525 (Jetway JNF99FL-525)"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by m-dw on 2014-04-04
OK, so I'm not a complete beginner, but I've been running Linux on an AMD64 3200+ since 2004ish and switched to Ubuntu desktop on it about 2 years ago.  I'm now embarking on a home-server project to replace a consumer NAS.

I've bought the above motherboard, it is 64bit CPU, and evidence suggests it works with Ubuntu server, but suddenly I realise there isn't anything explicit as to whether I need the 32bit x86 or the x86_64 (from the AMD64 installer image.

HELP! (please)

---

### Post by Double.J on 2014-04-04
Hi there!

Can't see any real advantage these days to not using 64 bit unless you're looking at pretty ld hardware or less than 2GB RAM? Back in the day 64 bit was notriously buggy, but I've not had any issue with the 64 bit versions since around lucid and it is now the recommened version.

What is interesting is that intel list the D525 as 4GB max RAM, however multiple users on newegg have listed that this board can support upto 2x4GB, so for that reason alone, I'd install the 64 bit version incase you have cause to up the RAM at a later date you can just pop it in and not have to reinstall.

---

### Post by m-dw on 2014-04-04
Thanks... and yes I saw the notes about support for 8GB (after I bought 2 x 2GB SODIMMS).  Actually it's an even more more basic question than that....

Do I need (explicitly) the 64-bit PC (AMD64) server install image blah-blah-amd64.iso?   I kinda assumed that it is, but then remembered what they say about assumption, and that an Intel Atom processor isn't listed as compatible.

---

### Post by Impavidus on 2014-04-04
It's called amd64 for historical reasons, as amd was the first to come with this 64 bit instruction set. However, amd and intel 64 bit processors are both capable of running the same 64 bit Ubuntu.

---

### Post by Double.J on 2014-04-04
I think op was asking if the board supports it.

with atom boards, even though all but the n2* and z5* chips are 64 bit, not all boards have 64 bit chipsets and firmware. This is mostly due to intensive price competition on low performance server boards.

However, having looked into it the chipset definitely supports 64 bit and numerous reports list the use of 8gb and 64bit OS, so there shouldn't be a firmware issue.

---

### Post by m-dw on 2014-04-04
Thanks both.  I was asking both questions....
 
The wording on the alternative downloads page implies that x86 is 32bit but doesn't explicitly state it, and the same page indicates that the AMD64 will work on a variety of processors but doesn't explicitly say Intel64,or Atom.  Last time I bought a CPU specifically to run Linux was 2004.  Still using it now and it is an AMD64 :)

And I had also read that some miniITX boards based on the Atom processors didn't support the Intel64 instruction set unless enabled" so wanted to know specifically if that board was going to support a 64bit server, rather than spend 3 days trying to find out why it didn't.

---

### Post by Yellow Pasque on 2014-04-05
You can run 32-bit/x86 on a 64-bit system, so it's always the safe bet.

For 64-bit support, the CPU and mobo need to support it. It's easy to verify the CPU: [http://ark.intel.com/products/49490/Intel-Atom-processor-D525-1M-Cache-1_80-GHz](http://ark.intel.com/products/49490/Intel-Atom-processor-D525-1M-Cache-1_80-GHz)
As for mobo, it's tougher, but the Jetway page offers 64-bit drivers and newegg reviewers state they're running Windows64
[http://www.jetwaycomputer.com/NF99.html](http://www.jetwaycomputer.com/NF99.html)

So yes, you should be able to use 64-bit if you want.

> rather than spend 3 days trying to find out why it didn't. 
The good news is that if you try 64-bit install on a machine that doesn't support it, you usually find out quickly (the install .iso doesn't boot).

---

