---
title: "Program running out of memory - increase memory size"
date: 2008-12-10
forum: Programming Talk
---

### Post by DBQ on 2008-12-10
Hi everybody. My console program runs out of memory.  Is there a way, before I run the program to increase the size of the memory the program is allowed to use?

Thank You.

---

### Post by psusi on 2008-12-10
It should be allowed to use as much as you have.  You probably have a memory leak so it is using all of it up.

---

### Post by mssever on 2008-12-10
The answer to this question depends on the language you're using. Some languages (PHP comes to mind, but surely there are others) impose a memory limit on processes under certain circumstances. Others don't, and if you run out of memory it's because your system has run out of memory.

So, your questions are:

[LIST=1]
[*]Why are you running out of memory?
[*]Is the amount of memory your program is trying to use reasonable?
[/LIST]

---

### Post by grepgav on 2008-12-10
Memory allocation is usually handled by the Operating System, unless like the other poster mentioned you are using something like PHP that sets a cap for user programs. If you are managing the memory (something like c) you should make sure you are freeing up memory.

---

### Post by crazyfuturamanoob on 2008-12-10
Perhaps you could show the code to let us see if the problem is with memory leaks, as mentioned before.

What error message you got?

---

### Post by Cracauer on 2008-12-10
> **DBQ said:**
> Hi everybody. My console program runs out of memory.  Is there a way, before I run the program to increase the size of the memory the program is allowed to use?


What happens, exactly?

What kind of program?

---

