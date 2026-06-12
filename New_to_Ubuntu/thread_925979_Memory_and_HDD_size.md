---
title: "Memory and HDD size"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by FixFax on 2008-09-21
I have just installed Ubuntu 8.04 on my new laptop HP 8510p. 
Works fine, but why is system monitor reporting 3.0 GiB memory (I have 4.0 GiB) and HDD 142GiB (I have a 160GiB)??
One of the great things about Ubuntu in my case is that it uses all of my memory, not like XP, using only about 3GB of 4GB.
Any ideas?

---

### Post by bumanie on 2008-09-21
If you installed the 32bit version, I think, like windows, it doesn't recognize 4gb ram, whereas the 64bit does. As far as the hard dive goes, a 160gb drive is in fact not a full 160gb, due to the way the drive manufacturers do their mathematics. For example 1gb is in fact 1024 mb, but the drive manufactures round it down to 1000mb - that accounts for some of the 'lost' space. Also, once formatted 5%, of the drive is reserved for the addressing needs of the filesystem, that accounts for 'lost' space also.

---

### Post by FixFax on 2008-10-08
As you understand, I am not working often with this new case. But thanks a lot for quick answer, bumaine. 
As I have understood, it is several pros and cons about choosing either 32 or 64 bit. One of the good things about 64 bit version is that bigger amount of data are processed each time - good for heavy working with a lot of graphics and stuff. I had an idea of that a 32 bit version gave me the best performance all though I am going to use my computer mostly as an VMware host for different types of OS. My goal is to have as much as possible of my HW-RAM to share between VMware virtual machines.
If I am far out in my understanding and priority, I would gladly install the 64bit version.
What do you recommend?

---

