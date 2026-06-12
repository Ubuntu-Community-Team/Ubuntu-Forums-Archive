---
title: "gcc cannot find stdio.h library?"
date: 2006-02-08
forum: Programming Talk
---

### Post by snoman on 2006-02-08
I'm having a slight problem.  I recently installed Ubuntu on both my laptop and desktop.  Being a fairly proficient programmer in C/C++, I have been writing programs on my desktop and compiling with gcc with no problems.

My problem is, when I try to compile the same code on my laptop, or even just simple programs, gcc chokes and tells me that it cannot find stdio.h.  The precise error is  "error: stdio.h: No such file or directory".  I've tried updating gcc, hoping that that would fix the problem, but it has gotten me nowhere.  Anyone have any ideas on how to fix this?

---

### Post by toojays on 2006-02-08
Have you installed the build-essential package?

---

### Post by MartinG on 2006-02-08
[QUOTE=snoman]I'm having a slight problem.  I recently installed Ubuntu on both my laptop and desktop.  Being a fairly proficient programmer in C/C++, I have been writing programs on my desktop and compiling with gcc with no problems.

My problem is, when I try to compile the same code on my laptop, or even just simple programs, gcc chokes and tells me that it cannot find stdio.h.  The precise error is  "error: stdio.h: No such file or directory".  I've tried updating gcc, hoping that that would fix the problem, but it has gotten me nowhere.  Anyone have any ideas on how to fix this?[/QUOTE]You need to install the whole tools set, not just gcc. Try[INDENT]sudo apt-get install build-essential[/INDENT]

---

### Post by snoman on 2006-02-08
Thanks, that seems to have done the trick.

---

### Post by praveensinha on 2008-09-07
> **MartinG said:**
> You need to install the whole tools set, not just gcc. Try[INDENT]sudo apt-get install build-essential[/INDENT]

:guitar: ihave install ubuntu 8.04 ,iface problum with C & c++ when compile
iget message gcc cannot find stdio.h library:guitar:

---

### Post by mssever on 2008-09-07
> **praveensinha said:**
> :guitar: ihave install ubuntu 8.04 ,iface problum with C & c++ when compile
iget message gcc cannot find stdio.h library:guitar:
Do you still have problems after following the instructions above?

---

### Post by Socrates1013 on 2008-09-07
> **praveensinha said:**
> :guitar: sudo apt-get install build-essential 

I had to run 'sudo apt-get install update' before that so it would work, just an FYI

---

### Post by mssever on 2008-09-07
> **Socrates1013 said:**
> I had to run 'sudo apt-get install update' before that so it would work, just an FYI
You mean, "sudo apt-get update", don't you?

---

### Post by Socrates1013 on 2010-02-02
> **mssever said:**
> You mean, "sudo apt-get update", don't you?

:DYeah, that was it.:D

---

