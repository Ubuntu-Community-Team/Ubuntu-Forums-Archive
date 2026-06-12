---
title: "How do I measure disk I/O ?"
date: 2005-07-11
forum: Programming Talk
---

### Post by negatory on 2005-07-11
I want to know how can I measure disk I/O much like the gnome system monitor applet.I want to measure the disk I/O in real time (so I can know the read/writes at any given moment).
I'm planning to log the information and see the effect it has on temperatures in my system along the day.
Thanks
Pedro Carrico

---

### Post by sksbir on 2005-07-11
[QUOTE=negatory]I want to know how can I measure disk I/O much like the gnome system monitor applet.I want to measure the disk I/O in real time (so I can know the read/writes at any given moment).
I'm planning to log the information and see the effect it has on temperatures in my system along the day.
Thanks
Pedro Carrico[/QUOTE]

try **netstat 5 **, and **vmstat 5**
you have to write a script file if you want to collect datas...

---

### Post by wmealing on 2005-07-15
I think "iostat" is the binary you are looking for.  

vmstat is good for the virtual memory manager.  Be warned that iostat shows the IO statistics on the per-disk level not the per-process level.

---

### Post by Denwerko on 2009-04-28
maybe "iotop" is what you're looking for

---

