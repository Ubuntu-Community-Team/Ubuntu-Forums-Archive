---
title: "32 versus 64 bit Ubuntu"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by ian49 on 2014-06-26
I'm just about to invest in a new pc build and have decided to install Ubuntu 14.04 as my primary operating system. The new pc will have a 64-bit processor and 8 Gb of RAM so what I was wondering was whether I should install the 32 or 64bit version of Ubuntu. Apart from Ubuntu I'm going to be running Windows XP as a virtual machine on the pc from time to time. In terms of storage I'll have a 120Gb SSD as primary and a 2TB Samsung as secondary.  Not sure that it's relevant but I'll be using Gnome fallback rather than the ghastly Unity. I was simply going to go ahead with 64 bit Ubuntu but read in a couple of places that there may be valid reasons for sticking with 32 bit. As I've little experience with Ubuntu I thought I'd just seek the opinion of those more qualified than myself to make a judgement. Thanks in advance for any constructive advice.

---

### Post by uRock on 2014-06-26
64bit will be faster. Especially with running a VM.

---

### Post by LastDino on 2014-06-26
With that config, stick with x64.

---

### Post by kostkon on 2014-06-26
64bit.

---

### Post by coldcritter64 on 2014-06-26
+1 to the previous 3 posts. From my past use of XP in virtualbox on both 64 and 32 bit installs, the performance is better with the 64 bit.

---

### Post by collisionystm on 2014-06-26
You will need 64 bit to take advantage of multi-core cpu's and that much memory.

---

### Post by Richard_Romick on 2014-06-27
To add to what the others said, the maximum RAM a 32-bit OS can support is 4 GB.  Therefore, your specifications would require a 64-bit OS.

---

### Post by 3rdalbum on 2014-06-27
There are good reasons to use 32-bit if you have very limited RAM. No reasons if you have 8gb.

---

### Post by zemega on 2014-06-27
Again, to reinforce your confidence, go with 64 bit.

---

### Post by Impavidus on 2014-06-27
> **Richard_Romick said:**
> To add to what the others said, the maximum RAM a 32-bit OS can support is 4 GB.  Therefore, your specifications would require a 64-bit OS.

Not entirely true because of PAE, but there still is a limit of 4GiB/application on 32 bit. I found out that whenever I use more than 4GiB out of 8GiB installed in my laptop, it's because a single application is using a lot, making PAE quite useless. The only advantage of 32 bit OS on 64 bit CPU is that 32 bit OS uses the available memory more efficiently, which can be interesting if you only have 1GiB ram or so.

---

