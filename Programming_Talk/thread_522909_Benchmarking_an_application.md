---
title: "Benchmarking an application"
date: 2007-08-11
forum: Programming Talk
---

### Post by n.aggel on 2007-08-11
Hi, i 've recently done a university project requiring me to construct a data structure{ a heap}....

Now that i 've finished the programming task , i am thinking how can i measure the programm's performance.....

I will populate my data structure with 2 million random elements, and i will measure the time it takes to complete the varius operations on it....

The question is how can i do this...????

---

### Post by Mathiasdm on 2007-08-11
Something like this?

```
long largeNumber = 10000000;
time_t begin = time(NULL);
for(int i=0;i<largeNumber;i++) {
    doActionOnHeap();
}
time_t end = time(NULL);
difference = end - begin;

```

You can double/halve the 'largeNumber' to see if how your code scales.

---

### Post by n.aggel on 2007-08-11
i was thinking about calling a function of the  OS because i don't think it is reliable to test your program like this...

---

### Post by slavik on 2007-08-11
man time

also, you want to generate the random list before the program is run and use it as test data ...

---

### Post by n.aggel on 2007-08-11
> **slavik said:**
> man time

also, you want to generate the random list before the program is run and use it as test data ...
thank you!!....that is what i was looking for....

---

### Post by Mathiasdm on 2007-08-11
> **n.aggel said:**
> i was thinking about calling a function of the  OS because i don't think it is reliable to test your program like this...

Oh, sorry. I didn't know it had to be that precise ;)

---

