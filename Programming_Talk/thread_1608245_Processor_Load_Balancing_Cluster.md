---
title: "Processor Load Balancing Cluster"
date: 2010-10-28
forum: Programming Talk
---

### Post by clayfreeman on 2010-10-28
Yes, hello.  I am looking for a type of cluster that separates process workload across all connected slave nodes to do a certain portion of the task from the master node.  I don't want to send out a task delegated to one or more servers, but for them to all work on one process as equally as possible.  I also don't want to make the servers all work on the same task and take the one that gets done first.  Is there anything out there like this?  I'm basically wanting to make a supercomputing cluster for fast calculations.  Basically, if the main node alone uses 100% CPU, I want it and four other slave nodes to take 20% of the work.

---

### Post by NathanB on 2010-10-28
I think you mean a Beowulf cluster.

[http://en.wikipedia.org/wiki/Beowulf_%28computing%29](http://en.wikipedia.org/wiki/Beowulf_%28computing%29)

Please keep us informed as to how your project progresses.

---

### Post by clayfreeman on 2010-10-28
> **NathanB said:**
> I think you mean a Beowulf cluster.

[http://en.wikipedia.org/wiki/Beowulf_%28computing%29](http://en.wikipedia.org/wiki/Beowulf_%28computing%29)

Please keep us informed as to how your project progresses.

I seen that this page talked about parallel processing;  Does this mean that each node performs the task solitarily and reports back when done or does it mean that each node is given an equal amount of calculations to perform?  If it means the latter then this is exactly what I'm looking for.

---

### Post by NovaAesa on 2010-10-29
Each node will do an assigned task and report back when it's done. It just happens that this will be equivalent to having each node perform an equal amount of calculations, so in a way it's both.

---

### Post by clayfreeman on 2010-10-29
That's the thing, I don't want the redundancy in the tasks for each node.  Is there a way to disable this?

---

### Post by NovaAesa on 2010-10-30
I'm not sure what you mean by redundancy in the tasks done. It's up to which ever distributed algorithm you create to make sure there is no redundant work being done.

---

### Post by clayfreeman on 2010-11-10
> **NovaAesa said:**
> I'm not sure what you mean by redundancy in the tasks done. It's up to which ever distributed algorithm you create to make sure there is no redundant work being done.

I thought you meant that each machine would carry out the same task and report back when done.  The reason I need no redundancy in tasks or calculations is because I plan on running ongoing applications that need to be faster than the average Intel i7 processor.  I'm basically wanting to create a RAID 0 array of computers, but with processors, not hard drives.  I hope I'm making better sense.

---

### Post by DanielWaterworth on 2010-11-11
I haven't tried it, though I've been meaning to. Kerrighed looks pretty good. You can run any program designed for a SMP. [http://www.kerrighed.org/wiki/index.php/Main_Page](http://www.kerrighed.org/wiki/index.php/Main_Page)

---

