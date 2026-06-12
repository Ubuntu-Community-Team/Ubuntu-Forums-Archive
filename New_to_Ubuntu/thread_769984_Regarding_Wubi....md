---
title: "Regarding Wubi..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by lavadisco on 2008-04-27
I just installed Ubuntu using Wubi. So far, I am ecstatic at the prospect of ditching Windows entirely (eventually). But here are the first of many questions:

- Is Ubuntu actually running on top of Windows running in the background? Or is it just Ubuntu that's running?

- Drivers for all of my hardware, like my video card, bluetooth card, wireless card - they all seem to work in Wubi-installed Ubuntu. Is Ubuntu piggy-backing on the Windows drivers for these devices, or would I have the same pain-free experience if I wiped the hard drive and installed Ubuntu from scratch?

Thanks for all your help and newbie tolerance.

---

### Post by mevets on 2008-04-27
Its virtualized, so you could say its piggy-backing on windows. This is the reason all the drivers work. Best way to see if your drivers will work is to boot to the live cd

---

### Post by maniacmusician on 2008-04-27
[http://wubi-installer.org/faq.php#internals](http://wubi-installer.org/faq.php#internals)

According to the WUBI FAQ, it is not virtualized, and is just as native as a real installation. The only difference is that it runs in a fake filesystem created inside your Windows partition. 

So no, it shouldn't be relying on Windows for drivers at all.

---

### Post by grazed on 2008-04-27
> **mevets said:**
> Its virtualized, so you could say its piggy-backing on windows. This is the reason all the drivers work. Best way to see if your drivers will work is to boot to the live cd

yeah, totally disregard what was just said here. obviously misinformed.

to answer your question, yes. a clean install will yield the same exact results you have now. no need to worry about drivers if they are working properly now. 

the only difference being that your experience will be much faster due to it running on a true partition.

---

### Post by maniacmusician on 2008-04-27
> **grazed said:**
> yeah, totally disregard what was just said here. obviously misinformed.

to answer your question, yes. a clean install will yield the same exact results you have now. no need to worry about drivers if they are working properly now. 

the only difference being that your experience will be much faster due to it running on a true partition.
I wonder if this has to do simply with the fact that using ntfs-3g to access the fake partition file (which is how I'm assuming wubi does it) is slower than the open source, non-reverse-engineered ext3 drivers? I'm guessing that's it, so probably no need to post this, but I took the time to write it, so why not?

---

