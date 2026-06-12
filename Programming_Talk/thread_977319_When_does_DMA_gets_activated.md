---
title: "When does DMA gets activated?"
date: 2008-11-10
forum: Programming Talk
---

### Post by kcode on 2008-11-10
When data transfer among peripheral devices is needed, either CPU does it || it is done by DMA. What i cant understand is that when does DMA gets activated? Does it gets activated by the CPU || it gets activated by requests from the peripheral devices it needs to act upon?

Another thing, where in the kernel code can i find such transfer of control?
And can i control the transfer dnyamically??

(I have extremely inefficient teachers in my college and i just hate them like hell, and this is the only place where i can find my answers!)

thanks

---

### Post by Ferrat on 2008-11-10
[http://en.wikipedia.org/wiki/Direct_memory_access](http://en.wikipedia.org/wiki/Direct_memory_access)

---

### Post by kcode on 2008-11-11
> **Ferrat said:**
> [http://en.wikipedia.org/wiki/Direct_memory_access](http://en.wikipedia.org/wiki/Direct_memory_access)

I got that!
But where in kernel the switch is implemented??

thanks

---

### Post by Zugzwang on 2008-11-11
> **kcode said:**
> I got that!
But where in kernel the switch is implemented??

thanks

Just out of curiosity: Why do you need that information? Does it have something to do with your question regarding the playing of sound? From a developer's point of view, you should *never* worry about those details *except* if you want to make your own drivers.

---

### Post by Desty on 2008-11-11
> **kcode said:**
> Another thing, where in the kernel code can i find such transfer of control?
And can i control the transfer dnyamically??

(I have extremely inefficient teachers in my college and i just hate them like hell, and this is the only place where i can find my answers!)
These are really specific questions; if you expect your lecturers to know answers to special mechanisms like this that are different in each operating system, then you're kidding yourself.

It's like expecting a geography teacher to know the population of every town in the world.

Have you checked the source code from some kernel drivers that deal with DMA? (e.g. disks, audio, video, network adapters)

---

### Post by kcode on 2008-11-12
> **Zugzwang said:**
> Just out of curiosity: Why do you need that information? Does it have something to do with your question regarding the playing of sound? From a developer's point of view, you should *never* worry about those details *except* if you want to make your own drivers.

I want to know only to play with my machine so that i can control it well, and then to break it and then build it, which goes on and on. I was just going through basic computer architecture (Morris Mano), during which i thought of how kernel implements this.

> **Zugzwang said:**
> Does it have something to do with your question regarding the playing of sound? 

No it has to nothing with that. Using Lenovo y-410, which has this problem.

---

### Post by kcode on 2008-11-12
> **Desty said:**
> These are really specific questions; if you expect your lecturers to know answers to special mechanisms like this that are different in each operating system, then you're kidding yourself.

It's like expecting a geography teacher to know the population of every town in the world.


Teacher couldnt even explain what DMA is. I dont expect anything from teachers. They are all s***! They care more how you sit in the   
lab than what you are doing in the lab. I just dont want to go to college...it is a daily torture for me.
I apologize for talking this s***, but sometimes i just feel to take it all out.

No i havent gone through those device drivers.

---

### Post by Npl on 2008-11-12
I think it should be abstracted in the PCI-interface, thats where DMA typically occurs in a regular PC.

On the lowest level a DMA-Transfer needs to be triggered by either the CPU or another device. For example by writing source and destination parameters to a specific area in memory and then writing to a special address to initiate transfer. Could be initiated with interrupts aswell, that depends on the specific Bus-System used.

---

