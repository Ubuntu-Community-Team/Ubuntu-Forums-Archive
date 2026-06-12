---
title: "Monitoring Memory Leak Question"
date: 2008-12-09
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-12-09
**This question is actually about Windows XP, but there might not be anything Windows-specific about it.  I am basically trying to figure out how to measure memory leakage (or allocation to see if a program continuously allocates memory) for a given process...

I have a program and its associated process and I want to monitor how much memory it is allocating (all memory dynamically allocated to it by the operating system which in this case is Windows XP). I know that I can monitor this through Performance Logging -> Processes, but I don't know which instrument I should look at. What parameter should I use to monitor memory consumed by the program?

I have been monitoring through task manager and also Start -> Control Panel -> Administrative Tools -> Performance -> Counter Logs -> Performance Object -> Process from there I can select:

Handle count
ID Process
IO Data Bytes / Sec
IO Data Operations / sec
Page Faults / Sec
Page File Bytes
Page File Bytes Peak
Pool Paged Bytes
Priority Base
Private Bytes
Thread Count
Virtual Bytes
Virtual Bytes Peak
Working Set
Working Set Peak

Would any of these tell me how much memory the program has dynamically allocated for itself on the heap?

---

