---
title: "Using C++ to calculate uptime and busy time"
date: 2008-09-27
forum: Programming Talk
---

### Post by openium on 2008-09-27
I'm trying to write a program with the following specifications:

> In this section you will determine the system utilization during a short time interval when you are exercising the OS.  To do this, you will find (and print out).

   1. Duration of system uptime
   2. Duration of system idletime

Total running time (uptime) - time spent in  idle process (idletime) gives the system busy time. Busytime / uptime gives system utilization (what percentage of the time is the system doing work).  The initial numbers will give accumulated values since the system was last restarted.  To calculate the system utilization during a period when we have placed a load on the system, we need to record intitial values, put the system under load, and then take a second set of readings.  The difference in uptime and the difference in idletime can be used to calculate the system utilization during the test.

So the procedure will be to print out how long the system has been up and how busy it has been. Once you have some baseline numbers printed, you will run a short program that places a load on the system.  You will then take a second set of numbers and calculate the load that your program placed on the system.

I understand how to use the time and ctime functions to get the current time since the epoch or current calendar time.  But I don't understand how to get the "uptime" of the system.  I know you can execute the uptime command and see how long the system has been running, but I'm having trouble fitting it into c++.  
Does what my teacher want even make sense according to the program specified?  Do you think the total uptime is meant to be the uptime of the program itself running and not total system time?  It seems to me I should grab the time at the beginning of my program and right before I enter my function that puts a load on the system.  I should grab the time right after the function completes and calculate the differences needed to find what I want..I just don't understand how to define my idletime other than the time spent on the function execution.  Please help

---

### Post by Sockerdrickan on 2008-09-27
You need to get the time at boot in time() (google it) and time_now-boot_time

---

