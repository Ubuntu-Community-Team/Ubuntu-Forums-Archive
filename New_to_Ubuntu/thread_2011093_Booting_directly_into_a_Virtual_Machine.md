---
title: "Booting directly into a Virtual Machine"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by yeehi on 2012-06-26
I think I heard this on IRC, but I didn't understand very well.

Somebody mentioned that they booted there system right into a virtual machine. I am sure that is what they meant. This sounded very interesting. Why would anybody do that? What are the advantages? Is it difficult to do? How do you set it up?

Shouldn't a Virtual Machine installation of Ubuntu be as fast as a rocket, since the whole thing runs in RAM?

---

### Post by mapes12 on 2012-06-26
> Virtual Machine installation of Ubuntu be as fast as a rocket, since the whole thing runs in RAMA VM usually shares RAM so you need lots of it. Some VM's are better than others by using dynamic RAM utilisation. Parallels for example.

If you need to boot right into an OS then why not go down the dual boot config option?

---

### Post by Paqman on 2012-06-26
> **yeehi said:**
> 
Shouldn't a Virtual Machine installation of Ubuntu be as fast as a rocket, since the whole thing runs in RAM?

Any VM is going to be slower than running the same system on bare metal, because you've got the overhead of running two systems.

Virtualised operating systems don't run in RAM any more than their host OS does. You could try and optimise it so that as much of it as possible ran in RAM, but you could do that to a system on bare metal too.

People generally virtualise OSes for convenience, not speed.

---

