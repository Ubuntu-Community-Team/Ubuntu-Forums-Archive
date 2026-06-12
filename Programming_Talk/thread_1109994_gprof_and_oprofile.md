---
title: "gprof and oprofile"
date: 2009-03-29
forum: Programming Talk
---

### Post by flylehe on 2009-03-29
Hi,
I have some questions regarding these profilers:

1. Is oprofile better than gprof in terms of helping optimizing code time performance? Like checking branch misprediction, etc;

2. Why does oprofile require root while gprof doesn't? 
I am trying to use oprofile on a server, however I don't have access to root, so here is what I get:
> 
bash-3.2$ opcontrol --vmlinux=/boot/vmlinux-`uname -r`
Normal users are limited to '--dump'.
bash-3.2$ opcontrol --start
Normal users are limited to '--dump'.
bash-3.2$ opcontrol --dump
Unable to complete dump of oprofile data: is the oprofile daemon running?
bash-3.2$ opreport
opreport error: No sample file found: try running opcontrol --dump
or specify a session containing sample files

It seems to tell me I can use dump only, but actually I cannot even start. Is it no way to use oprofile if I am not root?
Would it help if I am able to install my oprofile under my $HOME?

Thanks!

---

### Post by Portmanteaufu on 2009-12-16
I realize that this is an older post, but I figured I'd respond anyway since I found this through Google and figured others might do likewise. From what I understand, where gprof profiles a given program, OProfile profiles the **entire system.**

From the OProfile "About" page:

> OProfile is a system-wide profiler for Linux systems, capable of profiling all running code at low overhead. OProfile is released under the GNU GPL. It consists of a kernel driver and a daemon for collecting sample data, and several post-profiling tools for turning data into information. OProfile leverages the hardware performance counters of the CPU to enable profiling of a wide variety of interesting statistics, which can also be used for basic time-spent profiling. All code is profiled: hardware and software interrupt handlers, kernel modules, the kernel, shared libraries, and applications. 

So while gprof only needs access to a particular program for which you as a user might have permissions, OProfile monitors not only every user program running but the entirety of the kernel as well. That's why you'd need to be root to run it.

Hope that helps!

---

### Post by flylehe on 2009-12-26
Thank you!

---

