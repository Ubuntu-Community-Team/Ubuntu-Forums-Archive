---
title: "Optimum PC configuration to run intensive C code?"
date: 2006-03-03
forum: Programming Talk
---

### Post by jofre on 2006-03-03
Hi lads, 

I need to run intensive C code. For that I have a Pentium4, and a 1GB of Ram.

I am using this machine to write this lines, but eventually I would have to run C code that can take days (I am doing physics). I am relatively new in Linux, so I was wondering if any of you can advise me in what is the best configuration for the computer. I have installed the 686-smp kernel from apt-get. I imagine that booting the computer in rescue mode, could be an option, so no X system is running. Sorry for this baffle, more specific questions:

** Which processes can i shut down safely and how can i do it (I don't need to be connected to internet to run the code, ...).

** With the minimum staff that I need to be running, it is worthy to try to compile everything from source, or the gain in speed will be minimal.

** It is worthy recompiling the kernel?

** It is better just to make another partition and do a server installation, to save unnecessary headache?

** It is worthy to buy more RAM, it will decrease running time? (my intuation is that is just the CPU who is important here, but I thought it was worht asking, just in case)

Thanks a million, Jofre

---

### Post by rmjokers on 2006-03-03
My intuition is that you will gain much more by optimizing your own code as much as possible rather than trying to optimize other parts of the system that will be mostly idle while your code is running.  You dont need more RAM unless your code will be using a large portion of what you already have.  Let it run for a while and take a look at how much memory the process is using.  If it is less than half of the total RAM, I wouldnt worry about it.  Finally, it is possible to make an existing Ubuntu installation boot into text rather than graphical mode.  By default, Ubuntu boots into runlevel 2, which is unusual for a linux distribution.  In any case, you can see what is scheduled to run by default by looking at the links in /etc/rc2.d.  If you delete the entry for GDM, the graphical login screen will not start by default.  You can always create the link again later to restore it.

---

### Post by LordHunter317 on 2006-03-03
There's nothing you should do beyond turning off a screensaver if you have one, and possibly disabling scheduled tasks for the duration.  The eaisest way to do that is to shutdown cron:```
sudo /etc/init.d/cron stop
```Don't forget to start again when you're finished.

Anything else won't matter, likely, assuming a computation-heavy, CPU-bound workload.

---

