---
title: "Program not using processing power"
date: 2010-09-14
forum: Programming Talk
---

### Post by till_hm on 2010-09-14
Hey everyone,

I wrote a program to simulate stellar evolution. The code runs smoothly and quickly on Mac but as soon as I port it to Ubuntu (no changes in code required) the program only uses ~10% of the processing power and is hence about 10 times slower.

I did some simple profiling using the "clock()" function and supposedly the program takes 3 seconds to run according to the output. However, as expected, it takes about 30s in reality.

I am rather surprised by these results and was wondering whether anyone else had run into similar problems before.

Cheers,
Till

---

### Post by cholericfun on 2010-09-14
what language is the code written in?
what compiler did you use? what options?

can you optimize your code somewhat so the compiler youre using on ubuntu can do a better job?

whats the hardware difference?
how much memory do you have on each computer and how does the memory usage look when running?

---

### Post by till_hm on 2010-09-14
> **cholericfun said:**
> what language is the code written in?
what compiler did you use? what options?

can you optimize your code somewhat so the compiler youre using on ubuntu can do a better job?

whats the hardware difference?
how much memory do you have on each computer and how does the memory usage look when running?

Hey, I don't think the problem is that my code is inherently slow but the code is not using any computing time (while the program runs the processor is only used by the program such that the load rises to ~10%).

The code is a combination of c (compiled with gcc -std=c99 -g) and fortran (compiled with gfortran -m64 -cpp) and is linked with gfortran (same options). The same makefile is being used on the Mac.

Mac Snow Leopard x64: MacBook Pro 2.33GHz (Core 2 Duo), 3GB RAM
Ubuntu 10.4 x64: Dell Vostro 2.10GHz (Core 2 Duo), 4GB RAM

Neither the processor load nor the memory used show any appreciable difference if I run the simulation.

Here is some output from my program (Simulate: <seconds> gives the time measured by the program to do one simulation; Total: <seconds> gives the time measured by the program to do all simulations)

```

[...]
Simulate: 0.010000
Simulate: 0.020000
Simulate: 0.020000
Simulate: 0.020000
Simulate: 0.020000
Simulate: 0.030000
Simulate: 0.020000
Simulate: 0.020000
Simulate: 0.030000
Simulate: 0.010000
Simulate: 0.030000
Total: 1.380000

```

In particular, the total of 1.38 seconds does not agree with the total runtime of the program (approximately 15 seconds).

Thanks for looking into this. I really appreciate it!

Till

---

### Post by ssam on 2010-09-14
is the program spending time waiting for IO?

have you tried to profile with gprof?

---

### Post by till_hm on 2010-09-14
> **ssam said:**
> is the program spending time waiting for IO?

have you tried to profile with gprof?

Yes, the program does use IO (to a MySQL database) but this should not impact the total time measured by the program itself. Also, it would be surprising for MySQL to have a factor of 10 performance difference between Mac and Ubuntu.

I tried profiling with gprof, but given that the program seems to only be aware of running for 1.38 seconds gprof gives me what I would expect to see, but not what actually happens.

---

### Post by Zugzwang on 2010-09-14
> **till_hm said:**
> Yes, the program does use IO (to a MySQL database) but this should not impact the total time measured by the program itself. 

Wait wait wait. If I remember correctly, the time measured by the program itself "1.38 seconds" is the running time you would exprect. It's just the wall clock time that differs to the actual wall-clock overall computation time by a factor of 10. So the MySQL calls *do* not have an impact on the total time measured by the program itself (the clock() function measures the process time) but it is fair to assume that a significant fraction of remaining ~10-1.38 seconds is spent waiting for database replies.

Note that there are multiple ways to connect to a MySQL database. Problably you are using a faster one on the Mac but a slower one on the Linux computer?

---

### Post by ssam on 2010-09-14
then it sounds like its not counting the time is spends waiting.

---

### Post by till_hm on 2010-09-14
> **Zugzwang said:**
> Wait wait wait. If I remember correctly, the time measured by the program itself "1.38 seconds" is the running time you would exprect. It's just the wall clock time that differs to the actual wall-clock overall computation time by a factor of 10. So the MySQL calls *do* not have an impact on the total time measured by the program itself (the clock() function measures the process time) but it is fair to assume that a significant fraction of remaining ~10-1.38 seconds is spent waiting for database replies.

Note that there are multiple ways to connect to a MySQL database. Problably you are using a faster one on the Mac but a slower one on the Linux computer?

So if I understood correctly, "clock()" measures the processor time rather than the actual time such that idle/wait for MySQL calls cannot be measured using "clock()"? Which function would give me the real time rather than the processor time?

Edit: No, that cannot be it either because MySQL would be eating up some of my processing power if it was struggling to deliver the data to the client on time.

---

### Post by NovaAesa on 2010-09-14
> **till_hm said:**
> No, that cannot be it either because MySQL would be eating up some of my processing power if it was struggling to deliver the data to the client on time.
MySQL would not necessarily be eating up processing power trying to deliver the data, it could simply be because of IO waits.

---

### Post by ssam on 2010-09-14
if you run top, and look in the CPU line there is a figure labelled 'wa' for the percent of time spend waiting for disk IO. what does that say while the program is running?

could be a difference between buffering, flushing or barriers between linux and macosx.

---

### Post by till_hm on 2010-09-14
> **ssam said:**
> if you run top, and look in the CPU line there is a figure labelled 'wa' for the percent of time spend waiting for disk IO. what does that say while the program is running?

could be a difference between buffering, flushing or barriers between linux and macosx.

Hm, wa jumps up to about 40-50% while the program is running. But that would only imply a factor of ~1.5 rather than ~10. Certainly something I need to look into though...

Edit: It looks like my insert statement is eating up most of the time. I used Jet Profiler and 332 insert statements take up 21s - that does not seem right. The insert statement looks like

```

insert into Properties (BinaryId, `Index`, `Time`, Mass1, Mass2, Coremass1, Coremass2, Type1, Type2, Separation, Eccentricity, Stage) values (1411565, 3, 60.289505, 1.205791, 1.310726, 1.205791, 1.310726, 11, 13, 4.677209, 0.783441, 0)

```

Also, running the program with "time" gives the following
```

real    0m36.811s
user    0m2.780s
sys    0m0.030s

```
which certainly suggests that something is wrong with IO here.

---

### Post by ssam on 2010-09-14
which file system are you using? if it is ext4 you could have a look at the data mode section in [http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt)

[http://www.humboldt.co.uk/2009/03/fsync-across-platforms.html](http://www.humboldt.co.uk/2009/03/fsync-across-platforms.html) also has some useful info.

---

### Post by till_hm on 2010-09-14
> **ssam said:**
> which file system are you using? if it is ext4 you could have a look at the data mode section in [http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt](http://www.mjmwired.net/kernel/Documentation/filesystems/ext4.txt)

[http://www.humboldt.co.uk/2009/03/fsync-across-platforms.html](http://www.humboldt.co.uk/2009/03/fsync-across-platforms.html) also has some useful info.

Am already using ext4. Thank you for the hint though!

Edit: Looks like other people have similar problems: [http://ubuntuforums.org/showthread.php?t=1547883](http://ubuntuforums.org/showthread.php?t=1547883)
Edit: And it looks like ext4 is the problem: [http://ubuntuforums.org/showthread.php?t=1313834](http://ubuntuforums.org/showthread.php?t=1313834)

**For everyone else who might run into this problem: Add barrier=0 to your /etc/fstab file for the ext4 file system that you are using to store your MySql data. Solved the problem for me.**
```
UUID=f4025c41-6edc-4c85-87e1-d8e103801652 /               ext4    errors=remount-ro,barrier=0 0       1
```

Thank you for all the great help!

---

### Post by Some Penguin on 2010-09-14
[http://postgresql.1045698.n5.nabble.com/ext4-finally-doing-the-right-thing-td2076089.html](http://postgresql.1045698.n5.nabble.com/ext4-finally-doing-the-right-thing-td2076089.html)

Barriers were added for a reason.

---

