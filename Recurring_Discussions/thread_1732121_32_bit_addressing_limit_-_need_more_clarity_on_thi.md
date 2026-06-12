---
title: "32 bit addressing limit - need more clarity on this in the installation guide."
date: 2011-04-17
forum: Recurring Discussions
---

### Post by gemstonetiger on 2011-04-17
According to the current installation guide(s), the recommended install is still the 32 bit version. This is despite most low-end PCs that are purchasable today having 64 bit processors.

That isn't really the issue (although at some point I would expect the 64 bit version to be recommended to the average user). The problem is that the addressing limit of 32bit systems to 4Gb is now starting to affect many more machines (not just high end). I just bought a £350 laptop, with 4Gb and a 1Gb video card. I installed the 32 bit (erroneously, as I did it through the Xubuntu distro which still labels 64 bit as AMD64 which is quite misleading). That wasn't a problem until I realized later than my machine was only showing 3Gb, due to what I later found was the common addressing issue.

I like to think of myself as quite technically proficient, at least I was able to fix this within a few hours by a reinstall. However there are users out there who will be buying new relatively low-end PCs and won't even notice that they're getting short-changed on memory... Perhaps the installation should at least warn about the addressing issue? (Again I assume it doesn't - technically I went through the Xubuntu install, which doesn't). It would also be good if the installation guide advises people on this issue prior to them downloading the installation CD.

Anyway, that is all. I continue to love Ubuntu, just saying you might want to rethink the 32-bit recommendation policy now.

---

### Post by Dutch70 on 2011-04-17
Yeah, I think they should at least remove the word "recommended".

---

### Post by cometdog on 2011-04-17
Note that often the 32-bit installer will choose the PAE kernel for you (might not do this with the alternate install CD?) if you have a computer that is capable of more than 3GB memory.  In that case you'll get access to all of it, even though you retain the usual 32-bit limitations per process I think.  Clearly that's not exactly what you are asking for, but I suspect it is what was done to address the issue you bring up.

---

### Post by uRock on 2011-04-17
Moved to Recurring. This has been brought up before. There is even a bug report on it.

---

### Post by gemstonetiger on 2011-04-17
Ah, thanks. :)

---

### Post by NMFTM on 2011-04-18
> **cometdog said:**
> Note that often the 32-bit installer will choose the PAE kernel for you (might not do this with the alternate install CD?) if you have a computer that is capable of more than 3GB memory.  In that case you'll get access to all of it, even though you retain the usual 32-bit limitations per process...
Doesn't using the PAE kernal slow down the time it takes to retrieve things from RAM? Something about storing stuff as bigger values with filler information.

---

### Post by lemming465 on 2011-04-18
In my experience, a 64-bit kernel is about 15% faster than a 32-bit kernel on the same hardware.  Your mileage may vary.  There are a variety of arcane technical reasons for this, mostly related to reducing virtual memory overhead.

Regular users may not notice much difference for light office and web work, and as noted, while 32-bit systems will limit any individual process to 3GiB RAM, they will use all available physical RAM.  People who Really Need 64-bit are those running large media, scientific, or database workloads.  All of those will run *much* better in 64 bits, possibly by a lot more than 15%.

---

### Post by PhillyPhil on 2011-04-19
> **NMFTM said:**
> Doesn't using the PAE kernal slow down the time it takes to retrieve things from RAM? Something about storing stuff as bigger values with filler information.

Yes 32bit+PAE is slower than straight 32 bit, because you need an extra level of lookups before you actually access memory. 

The only reason to use PAE would be because you need more than 4GB total memory, and for some reason you don't have access to a 64 bit OS.

---

