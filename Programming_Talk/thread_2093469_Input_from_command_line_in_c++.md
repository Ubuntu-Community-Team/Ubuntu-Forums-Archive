---
title: "Input from command line in c++"
date: 2012-12-10
forum: Programming Talk
---

### Post by wardo1254 on 2012-12-10
I am new to programming and am trying to create a program that takes two numbers from the command line (wind speed and outside temperature), runs them through a few calculations and spits out a number (wind chill). I would like to take input in this sort of style:

```
 ./wind_chill -w 12 -t -7
```

I must be able to use negative numbers for the temperature variable.

So, how would one take the "-w 12 -t -7" part and define them as variables for further use?

---

### Post by Some Penguin on 2012-12-11
If your textbook says nothing about argument passing, look up the subject in K&R -- it's argc/argv.

---

### Post by dwhitney67 on 2012-12-11
> **Some Penguin said:**
> If your textbook says nothing about argument passing, look up the subject in K&R -- it's argc/argv.

Yes, and coupled with getopt() it should make it fairly trivial to parse the command line options.

---

