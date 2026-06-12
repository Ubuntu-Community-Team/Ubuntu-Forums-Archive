---
title: "Timing in Linux"
date: 2007-08-07
forum: Programming Talk
---

### Post by DBQ on 2007-08-07
Hey Guys,
   I was wondering what is more accurate way of timing the program, using the times function in #include <sys/times.h> or to use the command line time utility.  I was advised before not to use the command line utility.  Any ideas would be good.

---

### Post by PandaGoat on 2007-08-07
You should use the system header.  Using the system() to call something on the command line is taking the long route to using the system header; the commands for the terminal just use the system header.

---

### Post by hod139 on 2007-08-07
Here is a good article about accurate timing of functions:
[http://www.cs.rpi.edu/~musser/gp/timing.html](http://www.cs.rpi.edu/~musser/gp/timing.html)

---

### Post by nitro_n2o on 2007-08-07
you can also the time utility for something quick 
```
time ./myprogram 
```
if the program output stuff on the screen, for debugging for example you can get rid of it to /dev/null 
```
time ./myporgram > /dev/null
```
I'm not sure how accurate is this... but it's great as a quick solution

---

### Post by fatsheep on 2007-08-07
> **nitro_n2o said:**
> you can also the time utility for something quick 
```
time ./myprogram 
```
if the program output stuff on the screen, for debugging for example you can get rid of it to /dev/null 
```
time ./myporgram > /dev/null
```
I'm sure how accurate is this... but it's great as a quick solution

> **DBQ said:**
> Hey Guys,
   I was wondering what is more accurate way of timing the program, using the times function in #include <sys/times.h> or to use the command line time utility.  **I was advised before not to use the command line utility**.  Any ideas would be good.

:KS

---

### Post by slavik on 2007-08-09
the thing with time is that it knows where your code takes time ... it reports 3 metrics, real, user, system.

real = total time to run the program
user = how much time the program is in userspace (not accessing system stuff)
system = how much time syste spends on giving services to the program (writing file, connecting to network, etc.)

this allows you to somewhat gauge your program's performance and allow you to optimise they way you do things. :) (valgrind is supposed to be able to tell you which function in your code takes time and such)

---

