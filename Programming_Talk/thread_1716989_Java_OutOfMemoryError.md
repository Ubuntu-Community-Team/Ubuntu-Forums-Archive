---
title: "Java OutOfMemoryError"
date: 2011-03-29
forum: Programming Talk
---

### Post by Ibrahim mufeed on 2011-03-29
Hi All,

I have been developing a Java program that's need to make a big matrix like this:

```
subCellController = new int [(int) Math.pow(dimSize, 2)][dimSize];
```

Where the dimSize = 960. I am not sure about the size required :( . Am I calculating it correctly this way:
(((((960^2 * 960) * 4 Byte) / 1024 Kilobyte)/1024 Megabyte)/1024 Gigabyte) = 3.2 G. ??

If this number is correct, then I knew what is the problem [my machine is 2G Ram only] and I can switch to another machine with 8G Ram in this case.

I have searched the net, and found solutions to set the initial heap size & maximum heap size. I did this in the netbeans.conf file and tried to add it in the project properties. But I still get the same error.

I followed the instructions here step by step:
 1- [http://p0l0.binware.org/index.php/2010/04/17/netbeans-performance-switches/](http://p0l0.binware.org/index.php/2010/04/17/netbeans-performance-switches/)
2- [http://ubuntuforums.org/showthread.php?t=1199861&highlight=OutOfMemoryError](http://ubuntuforums.org/showthread.php?t=1199861&highlight=OutOfMemoryError)
3- [http://www.codemiles.com/java/here-how-to-increase-java-heap-size-t663.html](http://www.codemiles.com/java/here-how-to-increase-java-heap-size-t663.html)

I do need help please, I do not know what to do to make my program run.

Thank you,
Ibrahim

---

### Post by PaulM1985 on 2011-03-29
In Netbeans I have done something similar in the past where I added:

```

-Xmx***m

```

to the command line arguments that need to used at runtime.  This is in the properties of your project under "run".  There should be a text box called arguments.  Set *** to be the size you require.

Your calculation looks ok, so maybe that much is what you need.

Out of interest what is your actual problem?  Do you really need an array of that size?

Paul

---

### Post by PaulM1985 on 2011-03-29
Another thing to remember is that amount is just the space you require for that one variable.  Don't forget about the other variables.

Paul

---

### Post by Ibrahim mufeed on 2011-03-29
Yes Paul, I have already did this [many times], however I still get the same error. Since you see my calculations look good, then I guess the problem is that I do need more Ram to work on. I will try to test on the other machine, and it works fine as expected.

Regarding the problem type; this is an engine for an evolutionary algorithm just like the Genetic Algorithm, and here [before] building the populations I need to set the search space [map] that will be used.

Thank you,
Ibrahim

---

### Post by lsl on 2011-03-29
Some JVMs (all?) apparently have a 2 GiB heap space limitation, at least in 32-bit mode. 

I don't know if this problem exists with 64-bit JVMs. There is a switch "-d64" in Oracle's java which enables 64-bit mode on 64-bit systems.

---

### Post by Ibrahim mufeed on 2011-03-29
My guess was correct. First I made my machine have it's full memory power [4 GB], and then assigned "-Xmx3500m" for the program and the error did not appear this time and the machine started the processising. However, I could not even move the mose smoothly. But at least I figured out [finally] the problem I was facing all the time.

@lsl: I found no limitations though on the memory size. My machine is 46bit.

Thanks all,
Ibrahim

---

### Post by coweatyou on 2011-03-29
> **Ibrahim mufeed said:**
> My guess was correct. First I made my machine have it's full memory power [4 GB], and then assigned "-Xmx3500m" for the program and the error did not appear this time and the machine started the processising. However, I could not even move the mose smoothly. But at least I figured out [finally] the problem I was facing all the time.

@lsl: I found no limitations though on the memory size. My machine is 46bit.

Thanks all,
Ibrahim

Allocating that much memory will take forever.  I would recommend either processing using smaller chunks of data or using soft and weak references to save memory.

---

### Post by Some Penguin on 2011-03-29
Are you using the entire allocated space, or would you be better off with a sparse structure?

---

### Post by Ibrahim mufeed on 2011-03-29
I believe that this is a new problem I have to solve. I did not think about a solution yet. Soon I will. But the problem that it's all algorithm dependent and I am not sure if I will be able to use chunks of data, or references.

Once I need help, you will find me here again.

Thank you all,
Ibrahim

---

