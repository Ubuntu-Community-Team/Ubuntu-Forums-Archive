---
title: "CPU Usage"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by MattGEri on 2008-05-19
Hey,

Just wondering about CPU usage in Ubuntu. I have a pretty decent system but it seems to be lagging a bit with Ubuntu. Every time I start up a piece of software such as firefox, terminal, a game etc etc my CPU usage jumps to 100%. I also feel the lag when I switch programs etc. I do have desktop effects enabled but even with them disabled I feel the lag.

Is this normal?

My system specs are:

2ghz Celeron 440
1.5gb DDR2 ram
512mb Nvidia GeForce 7100GS graphics
160gb SATA hard drive

Thanks

---

### Post by Monicker on 2008-05-19
Grrr. Reply went to wrong window.

Disregard.

---

### Post by MattGEri on 2008-05-19
No worries :) Anyone else?

---

### Post by timandjulz on 2008-05-19
I have had a similar problem where file I/O causes the system to be very unresponsive.  Where Windows was performing the background file copying without having significant impact on starting other apps, Ubuntu is slow.  Running 8.04 64bit, quadcore cpu, 8GB memory.

Did you tweak your install any?  For example, did you change any file system settings... use compression... etc.

---

### Post by MattGEri on 2008-05-20
Nope I didnt tweak anything :S Just created my own custom partitioning...

---

### Post by MattGEri on 2008-05-24
Anybody else?

This is getting really bad. I now cant do anything without my computer lagging. When I run firefox it takes forever to switch tabs.

I think I may switch to openSUSE which I have running on my 4 year old laptop without any speed problems...

I have attached a screenshot to this post which shows my CPU usage in the top corner at 100% when I am just using amarok and firefox...

Any ideas would be highly appreciated...

- Matt

---

### Post by philinux on 2008-05-24
Open terminal and use the command

top

To see whats eating your cpu. Then report back

---

### Post by Harpoon on 2008-05-24
Make sure FF us updated (assuming you are using Hardy with FF3).  Next, you can disable (file) indexing --
System > Preferences >Control Center  - - it is at the bottom under "Other."  That might help.

The CPU "jumping" to 100% is kind of normal, based on the algorithm used by the CPU speed governor. Not to worry, unless it gets stuck up there and causes overheating problems.

---

### Post by tramir on 2008-05-24
Or, if you use Ubuntu, System-Preferences-Search and Indexing. Uncheck "enable indexing" and "enable watching". This has been known to cause the system to be relatively slow (I have an older computer and disabled it, it was almost unusable because of it).

---

### Post by shae on 2008-05-24
The possible problems you could be experiencing may be a combination of your cpu being throttled down to save power and produce heat combined with indirect bindings in compiz forcing compositing off onto the cpu.  However, forcing the cpu to maximum is normal for some programs when they are launching, such as firefox, but this should not persist after they are launched.

---

