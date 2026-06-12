---
title: "Can I use multiple alarms() in my Program ?"
date: 2006-04-11
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-04-11
HI,

I am new to linux just a few days back i ran my first c program in Linux. I need to use a timer kind of a thing in my program, i found the alarm() function with SIGALRM will serve the purpose. But what if i want to use more than one timer and if i use alarm() then the previous timer will be rescheduled I guess.. I am not sure about it Please help me on this.:confused: 

I just want to do certain things on each timer like reading from a file and writing on to a file but at a cetain different intervals, is there any other way round  for this ? , please help.

Thanks in Advance

---

### Post by LordHunter317 on 2006-04-11
What are you trying to time?  Reading/writing asynchronously is better accomplished using select()/poll() or a similiar method.  

You can have multiple alarms(), but you'll need to time them yourself and wrap the call to get the delivery semantics you want.

---

### Post by kolichina_s_s on 2006-04-11
HI,

Thanks for the reply,

[QUOTE=LordHunter317]What are you trying to time?  Reading/writing asynchronously is better accomplished using select()/poll() or a similiar method.  
[/QUOTE]

I need to read data from a serail port at a specified interval and put it on to a file. 

also i need to send a query to the serail port device at a specified interval.

[QUOTE=LordHunter317]You can have multiple alarms(), but you'll need to time them yourself and wrap the call to get the delivery semantics you want.[/QUOTE]

if you can give any links on this alarm() programming than it will be gr8 help. cause the only book i am using is the Advanced Unix programming of 1992 :-? edition where it says that there can only be one timer per process. I know there are many changes since 1992 but i have no other go.. 

Thanks again

---

### Post by LordHunter317 on 2006-04-11
[QUOTE=kolichina_s_s]I need to read data from a serail port at a specified interval and put it on to a file.

also i need to send a query to the serail port device at a specified interval.[/quote]My asynchronous I/O experience has shown me two things:[list][*]Even if you're polling at specified inteverals, the timing may not be perfect and you may need to read/write ahead of schedule[*]If you're doing both, the timing may not coincide[*]Other issues don't want you blocking in the middle of nowhere for this.[/list]You do not want to use alarm() for this, trust me.  Use select() or poll(), both of which can be handed a timeout, after placing the FDs in asynchronous mode.  That way, if the port gets data early, you can read it to prevent a buffer overflow.

> if you can give any links on this alarm() programming than it will be gr8 help. cause the only book i am using is the Advanced Unix programming of 1992 :-? edition where it says that there can only be one timer per process.Writing a wrapper around alarm() to figure out what the shortest alarm is, schedule it, and save the time of the next alarm(s) in a linked list; and writing a SIGALARM signal handler to schedule the next alarm (or force the main program to do it) is relatively straightforward.

---

