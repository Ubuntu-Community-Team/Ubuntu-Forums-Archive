---
title: "And now this..."
date: 2005-12-18
forum: Programming Talk
---

### Post by kudu on 2005-12-18
...what's the deal ?


fenris 0.07-m (3244, 23496) - program execution path analysis tool
Brought to you by Michal Zalewski <lcamtuf@coredump.cx>
***********************************************************
* During installation, I have determined that libraries   *
* in your system are mapped at 0x40nnnnnnn. Now, I've just *
* performed simple test to discover this is no longer     *
* true: library function 'open' is mapped at 0xb7c1c860.  *
* It might be because you've upgraded your kernel or have *
* some security-enhancing random address mapping feature. *
* In first case, all you have to do is to recompile me.   *
* In second case, I'm affraid I can't work with dynamic   *
* applications. I'm terribly sorry.                       *
***********************************************************
>> Exit condition: libc mapping problems


Any pointers in solving this one ? Thanks!

---

