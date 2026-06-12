---
title: "Ubuntu 8.10 and 4GB"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by noorez on 2008-11-03
I've read some articles that 4GB of memory isn't supported by default in 32bit OS unless you recompile the kernel. How can I go about doing this? I am going to upgrade my RAM to 4GB soon.

---

### Post by Bölvaður on 2008-11-03
I am not sure if that is possible.

What I would suggest to you is go for the 64 bit version.

---

### Post by bwhite82 on 2008-11-03
See:

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

It should be easy if you use your current kernel's .config file (which is in /boot after installing the headers and source).

Then enable PAE in kernel configuration.

---

### Post by phr0ze on 2008-11-03
4GB is supported, but you'll only have access to 3.2~3.3GB of it because the system is reserving address space for other hardware. I would only make the changes if I was going to 6+GB of ram. Everything has a penalty and by turning that switch on you will loose some performance so make sure it's worth it and not just for 700MB of ram.

Also, this isn't an ubuntu limitation, all 32bit operating systems have the same limitation.

---

### Post by SunnyRabbiera on 2008-11-03
> **Bölvaður said:**
> I am not sure if that is possible.

What I would suggest to you is go for the 64 bit version.

that is no help if he uses a 32bit processor though.
And yes its possible to get the desktop kernel to use more then 4GB of memory... the 32bit server kernel can with some tweaking

---

### Post by bodhi.zazen on 2008-11-03
32 bit processors can access more then 4 Gb, have been able to do so for quite some time.

See : [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

