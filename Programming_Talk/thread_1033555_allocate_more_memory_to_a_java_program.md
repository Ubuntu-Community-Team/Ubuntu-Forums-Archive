---
title: "allocate more memory to a java program"
date: 2009-01-07
forum: Programming Talk
---

### Post by nfyllas on 2009-01-07
Hi there
I am running an algorithm in Netbeans and I would like to know if I could speed it up
When running the system uses: 100 and (20--30) % of CPU1 and CPU2 respectively, plus 500 -- 600 MB (30%) of the ram.
Is there any way to allocate more memory to netbeans, something similar to change priority in Windowz?
Can I do than on run-time? 

Thanks

---

### Post by cszikszoy on 2009-01-07
Try to profile your algorithm, find out where the bottlenecks are, and optimize the actual algorithm.  Throwing hardware at a software problem is never the correct solution :D

---

### Post by Quikee on 2009-01-08
> **nfyllas said:**
> Is there any way to allocate more memory to netbeans, something similar to change priority in Windowz?

What has scheduler priority has to do with memory allocation ?

---

### Post by pp. on 2009-01-08
> **Quikee said:**
> What has scheduler priority has to do with memory allocation ?

Both control the assigment of ressources to tasks. Usage of different types of ressources is rarely orthogonal as more usage of one type of ressource often leads to more demand on another type.

---

### Post by myrtle1908 on 2009-01-08
You can set the min and max heap size allocated to the JVM with the -Xms and -Xmx options respectively.

---

