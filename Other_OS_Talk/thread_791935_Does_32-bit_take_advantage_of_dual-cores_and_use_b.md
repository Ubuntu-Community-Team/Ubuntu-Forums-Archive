---
title: "Does 32-bit take advantage of dual-cores and use both?"
date: 2008-05-12
forum: Other OS Talk
---

### Post by Lord Xeb on 2008-05-12
My friend and I had an argument earlier in school about 64 and 32 bit systems. I know that if one where to install a 64-bit OS on a multi-core system, all  cores are used. In 32-bit systems (like Vista 32-bit and XP 32-bit) are all cores used? If so, way is there only one CPU graph in the system monitor? In Ubuntu, if there are multiple cores, and I use conky, it shows all the cores. Is it the same for windows?

---

### Post by LaRoza on 2008-05-12
> **Lord Xeb said:**
> My friend and I had an argument earlier in school about 64 and 32 bit systems. I know that if one where to install a 64-bit OS on a multi-core system, all  cores are used. In 32-bit systems (like Vista 32-bit and XP 32-bit) are all cores used? If so, way is there only one CPU graph in the system monitor? In Ubuntu, if there are multiple cores, and I use conky, it shows all the cores. Is it the same for windows?

Both cores will be used. In Vista, I have two graphs for the CPU activity.

---

### Post by seanc7 on 2008-05-12
Windows task manager should show all cores with their own graph. If it shows separate graphs for simple hyperthreaded CPUs then true multicore CPUs should show as well.

---

### Post by mips on 2008-05-13
All cores will be used. My friends quad core shows 4 cpu graphs in WinXP 32bit.

---

### Post by 3rdalbum on 2008-05-14
There's one graph, but there should be multiple lines on the graph.

Lots of people get confused about 32-bit and 64-bit; they confuse it with "cores". A 64-bit processor can access more memory and (some would say) can perform certain calculations quicker - it does not provide twice as many pipelines as a similar 32-bit processor.

Even Windows XP Home should support dual, triple and quad-core processors (actually, I'd be interested to see if it does support triple-core processors as these were never imagined back in 2001). There is one caveat: XP Home will not recognise more than one CPU socket, so if you want a dual-CPU system you will need XP Pro or better (including Linux).

---

### Post by r76 on 2008-05-14
Example:

---

### Post by maconga on 2008-05-14
Lord Xeb,

Yes Windows 32-bit will take advantage of it ..... 
Here is some more info. 
[http://en.wikipedia.org/wiki/Multi-core_(computing)#Advantages](http://en.wikipedia.org/wiki/Multi-core_(computing)#Advantages)

---

### Post by ankitR on 2008-07-03
thank you! that's great clarification for my googling question

---

### Post by MaxIBoy on 2008-07-04
> **3rdalbum said:**
> (actually, I'd be interested to see if it does support triple-core processors as these were never imagined back in 2001). There is one caveat: XP Home will not recognise more than one CPU socket, so if you want a dual-CPU system you will need XP Pro or better (including Linux).


Triple-core? Do those even exist? And I didn't know about the single socket limit, thanks.

Anyway, yes, all your cores will work.
[img]http://img368.imageshack.us/img368/2161/quadcoresps6.png[/img]

---

### Post by mips on 2008-07-04
> **MaxIBoy said:**
> Triple-core? Do those even exist?

AMD Phenom X3.

When they make processors they dont always have a 100% success rate. Something might be faulty or wrong on one core etc so instead of dumping the silicon they simply disable the faulty core and sell a quad core as a tripple core. Less wastage and loss of money.

Only problem is the X3 is not much cheaper than a X4 at this stage and I can't see the logix in buying a X3 in this case.

---

### Post by jnw222 on 2008-07-05
wow i have never seen a screenshot of a quadcore

and i heard from a friend that there are 5-core prosserss is that true

---

### Post by damis648 on 2008-07-05
Both or all cores are used in 32-bit systems. There are multiple lines on the system monitor graph. Is you use monitoring screenlets, you will find that there are one more core than you actually have. This is because ubuntu lists each core individually, and the average as "CPU0".

---

### Post by mips on 2008-07-05
> **jnw222 said:**
> wow i have never seen a screenshot of a quadcore

and i heard from a friend that there are 5-core prosserss is that true

Not from Intel or AMD at the moment that there are aware of. Some other architectures have more than 4, even up to 80 cores or more.

[http://en.wikipedia.org/wiki/Multi-core_(computing](http://en.wikipedia.org/wiki/Multi-core_(computing))

.

---

### Post by damis648 on 2008-07-05
The more recent Mac Pros achieve eight cores with I think two quads or four duos.

---

### Post by LaRoza on 2008-07-05
> **damis648 said:**
> The more recent Mac Pros achieve eight cores with I think two quads or four duos.

Those are Intel Xeon processors, and not specific to Macs.

---

### Post by damis648 on 2008-07-05
> **LaRoza said:**
> Those are Intel Xeon processors, and not specific to Macs.

Ah, OK.

---

