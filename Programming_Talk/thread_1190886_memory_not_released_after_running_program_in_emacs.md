---
title: "memory not released after running program in emacs"
date: 2009-06-18
forum: Programming Talk
---

### Post by flylehe on 2009-06-18
Hi,
I am programming in Emacs and Ubuntu8.10. I found that every time after I run a memory-consuming C++ program, the memory is not released, which can be shown in my system monitor's "Resources" tab. Also the system monitor does not show the process that takes that large amount of memory in its "Processes" tab. 
Can someone tell me how to release the memory properly? 
Thanks and regards!

---

### Post by dwhitney67 on 2009-06-18
What language are you programming in?  (nevermind... C++)

How are you allocating memory?

How are you attempting to deallocate it?

```

int* i = new int;
delete i;

int* array = new int[1000];
delete [] array;

```

---

### Post by flylehe on 2009-06-18
It seems that in my code I have deleted all the memory that is allocated before. But I will check it again.

Just a simple question, is there a bash command that can release memory? I have finished running my C++ program from Emacs, even exited Emacs, however the memory used by my program is still held by the system.  System monitor shows this in the memory and swap charts under "Resources" tab, but does not show the process that takes that large amount of memory in its "Processes" tab, so I have no clue how to release the memory. Also even if there is no deallocation of memory in the code, why after the program finishes its running it does not release the memory used?
Thanks!

---

### Post by fr4nko on 2009-06-18
It looks very strange to me...

I will try to type

> ps axf

to see all active processes and check if your C++ application is still hanging like a zombie process. If the application is really terminated (i.e. it does not appear in the ps list) the memory should has been released. If the memory isn't released I will say you have a problem with your OS.

You can use also 'ps aux' to have more informations about memory usage.

I hope that helps,
Francesco

---

### Post by flylehe on 2009-06-18
Thank you Francesco. I didn't find the process of my program by ps axf.  If my Ubuntu has some problem, I think by update in time it will be fixed?

---

