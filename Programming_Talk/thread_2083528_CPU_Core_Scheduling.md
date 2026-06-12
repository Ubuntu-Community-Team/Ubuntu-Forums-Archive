---
title: "CPU Core Scheduling"
date: 2012-11-12
forum: Programming Talk
---

### Post by drmrgd on 2012-11-12
I'm working on this project that processes very large chunks of data, and to that end, I've implemented it to utilize multiple processor cores.  So far the package seems to work well on my test server running on a VM with 4 cores (the most that I can allocate to the VM with VMware Player).  However, I'm ready to roll this out on our production server, which has 12 cores.  The question I have is, can I open this up to use all 12 cores, or is that a bad idea given that the server is likely to need to process other datasets with other processes at the same time?  The jobs will be scheduled using a SGE job scheduler.  Still, I don't quite understand the semantics of this, and want to overwhelm the system.  Would it be better to just schedule say 8 cores instead of the full 12?  The processing time should be around 15 minutes, so maybe it's OK to use all those resources for that short time period?  Any advice?

---

### Post by akvino on 2012-11-13
Are you planning to affinitize threads? Are you planning to change scheduling policy?

If the answer is no, then you can use all that you have, since other tasks will be allowed time on CPU.

If you are affinitizing, leave core 0 and core 1 available, most architectures schedule kernel processing and interrupts on cores 0 and 1. 

OS threads should always have higher scheduling priority than application threads 'in REALTIME scheduling'. I am assuming you are not writing nuclear reactor software or airplane/submarine routines.

---

### Post by MadCow108 on 2012-11-13
> **drmrgd said:**
> I'm working on this project that processes very large chunks of data, and to that end, I've implemented it to utilize multiple processor cores.  So far the package seems to work well on my test server running on a VM with 4 cores (the most that I can allocate to the VM with VMware Player).  However, I'm ready to roll this out on our production server, which has 12 cores.  The question I have is, can I open this up to use all 12 cores, or is that a bad idea given that the server is likely to need to process other datasets with other processes at the same time?  The jobs will be scheduled using a SGE job scheduler.  Still, I don't quite understand the semantics of this, and want to overwhelm the system.  Would it be better to just schedule say 8 cores instead of the full 12?  The processing time should be around 15 minutes, so maybe it's OK to use all those resources for that short time period?  Any advice?


the job scheduler (in this case SGE) should take care of not overwhelming the machine.
you can give it hints on what kind of resources the program needs to help it with its job (so don't lie), for details see the manual of your scheduling system.
depending on the settings of your scheduler, you might also want to lower the priority of your process directly with nice. It will then only run with 100% when nothing else with higher priority needs the resources.

I wouldn't mess with cpu affinity unless you really see issues traceable to bad scheduling and need to squeeze the absolute best performance out of the machine. On a shared machine (which SGE implies) it may also not be a good idea.
the linux kernel scheduler is quite decent for computation intensive workloads by default.

---

### Post by drmrgd on 2012-11-13
Thank you both for the insight!  I found in some testing today that no matter how many cores I scheduled, I was running out of memory.  So, I added a ulimit line in the launch script to cap it at 8GB and it seems to be running fine with 8 cores.  After reading your responses, I'm going to try it with 12 tomorrow to see how more time I can cut out of the processing.  

This whole thing is based around an R script, and so I'm not sure how much control I have (just using the parallels library).   But, I think that based on what you say I think this should work safely.  

> I am assuming you are not writing nuclear reactor software or airplane/submarine routines. 	

Ha!!  That is a very safe assumption.  :)

---

