---
title: "Problem understanding top"
date: 2018-02-09
forum: New to Ubuntu
---

### Post by brianww on 2018-02-09
So i'm playing around trying to learn the different commands when i came around to "top" i seem unable to find documentations about certains things like Tasks seems to have different states running, sleeping etc would love to read aobut these.
I've also seen PR and NI seems very confusing are there any good documentation about these? All i seem to find are forum posts and i don't know if that information is up to date.

---

### Post by vasa1 on 2018-02-09
Your installation should allow you to run *man top* or even *info top*.

---

### Post by sudodus on 2018-02-09
There is another program **htop**, that is showing the same or very similar information in a way that is easier to understand. Install it with

```
sudo apt install htop
```

---

### Post by brianww on 2018-02-09
> **vasa1 said:**
> Your installation should allow you to run *man top* or even *info top*.

it does but man does not contain alot of information about nice values or process states

  The status of the task which can be one of:
               D = uninterruptible sleep
               R = running
               S = sleeping
               T = stopped by job control signal
               t = stopped by debugger during trace
               Z = zombie


           Tasks shown as running should be more properly thought of as ready to run  --  their task_struct is simply represented on the Linux run-queue.  Even without a true  SMP
           machine, you may see numerous tasks in this state depending on top's delay interval and nice value.

This is what i found but it just gives me what the symbols mean not what a zombie process is for example

---

### Post by vasa1 on 2018-02-09
I suggest you search the internet for specific terms. For example, for "uninterruptible sleep", I found
[https://stackoverflow.com/questions/223644/what-is-an-uninterruptable-process](https://stackoverflow.com/questions/223644/what-is-an-uninterruptable-process)
[https://lwn.net/Articles/288056/](https://lwn.net/Articles/288056/) and
[https://eklitzke.org/uninterruptible-sleep](https://eklitzke.org/uninterruptible-sleep)

---

### Post by QIII on 2018-02-09
All child calls become zombies (generally very briefly) when they have completed via an exit call.  They stay in the process table until the parent reads their exit status via a wait call.  At that point they are reaped by the system.  

A long-lived zombie process can indicate a parent that is doing something else (or sleeping itself) or poorly written code.

---

