---
title: "regarding sbrk()"
date: 2010-06-02
forum: Programming Talk
---

### Post by AdityaK on 2010-06-02
I'm working with a program on an AIX machine. Now I know that sbrk(0) returns the address of the end of the memory space allocated to the process. I want to know whether this allocated space also includes the heap kept aside for the process. I'm confused because my program uses sbrk(0) to locate the starting address of the heap allocated to it, while I feel the heap is already included in the allocated memory. How do I find out?

---

### Post by rnerwein on 2010-06-03
hi
have a look at: man edata --> etext, edata, end - end of program segments
think this will help you.
but if you are using brk/sbrk you really ! must know what you do !!!!
ciao

---

### Post by soltanis on 2010-06-03
```
       At  the start of program execution, the program break will be somewhere
       near &end (perhaps at the start of the following page).   However,  the
       break  will change as memory is allocated via brk(2) or malloc(3).  Use
       sbrk(2) with an argument of zero to find the current value of the  pro&#8208;
       gram break.

```

When the program is first initialized, there is little or no memory allocated to you beyond the amount which your program occupies in memory. You must allocate the heap yourself using sbrk, or more sanely, malloc. Why are you using sbrk, when most documentation advises strongly against it?

---

### Post by AdityaK on 2010-06-14
Right, I get it now. Thanx 
I'm working with someone else's code who had used sbrk(0) to locate the current start of the heap memory allocated to the program. That's where the doubt came from. 
Thanx again :)

---

### Post by rnerwein on 2010-06-14
> **soltanis said:**
> ```
       At  the start of program execution, the program break will be somewhere
       near &end (perhaps at the start of the following page).   However,  the
       break  will change as memory is allocated via brk(2) or malloc(3).  Use
       sbrk(2) with an argument of zero to find the current value of the  pro&#8208;
       gram break.

```When the program is first initialized, there is little or no memory allocated to you beyond the amount which your program occupies in memory. You must allocate the heap yourself using sbrk, or more sanely, malloc. Why are you using sbrk, when most documentation advises strongly against it?

hi
what soltanis tell you is very,very,very .... true.
if you are using any function call in that programm you are the loser - sure.
have a redesign because nobody can following what's going on. ( malloc, valloc etc. don't know that brk and sbrk is used !! - or is this kernel stuff you are talking about ? ). 
ciao   :-)

---

