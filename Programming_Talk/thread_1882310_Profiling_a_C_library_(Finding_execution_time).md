---
title: "Profiling a C library (Finding execution time)"
date: 2011-11-17
forum: Programming Talk
---

### Post by khurshid_coms on 2011-11-17
[SIZE=3]Hi,
I am a new user of Ubunto. I have used a C library for compressing documents from [http://www.gzip.org/](http://www.gzip.org/).
Now I want to determine the execution time of compressing one document. I am using gprof with -pg option for this purpose. I am getting very low value (in micro seconds) which is not true. I think there is some problem in profiling the whole library. I think the execution time I am getting is the one for that specific function and not the library function which are called by this function during execution.
Please inform me if someone knows the solution. 
So the problem is how to find execution time of compressing a single document using gzip.[/SIZE]

---

### Post by Blackbug on 2011-11-17
I am not sure about suggesting any specific thing as an answer to your problem, but normally i use TIME command to check how much time was spent in the execution of my binary..

---

### Post by surfer on 2011-11-17
i don't have a direct answer to your question either, sorry.

i usually use valgrind to do my profiling. that way i see on which routines my programs spend most of the execution time.

```
$ sudo apt-get install valgrind  kcachegrind
```

then, assuming your executable is called a.out:
```
$ valgrind --tool=callgrind ./a.out
```
which generates a file called callgrind.out.PID (PID was the process number of you program) which you can then inspect with
```
$ kcachegrind callgrind.out.PID
```
(remember to change the PID).

hope that helps.

---

### Post by ofnuts on 2011-11-17
> **khurshid_coms said:**
> [SIZE=3]Hi,
I am a new user of Ubunto. I have used a C library for compressing documents from [http://www.gzip.org/](http://www.gzip.org/).
Now I want to determine the execution time of compressing one document. I am using gprof with -pg option for this purpose. I am getting very low value (in micro seconds) which is not true. I think there is some problem in profiling the whole library. I think the execution time I am getting is the one for that specific function and not the library function which are called by this function during execution.
Please inform me if someone knows the solution. 
So the problem is how to find execution time of compressing a single document using gzip.[/SIZE]Gprof may be looking only at CPU time, while "elapsed" time will take in account the tie spent I/O. AS other say, "time"  may give you more information. Btw, I wouldn't be surprised to find that some types of docs compress a lot faster than others.

---

### Post by khurshid_coms on 2011-11-17
> **Blackbug said:**
> I am not sure about suggesting any specific thing as an answer to your problem, but normally i use TIME command to check how much time was spent in the execution of my binary..

I had already tried time command. The problems is it shows two different execution time if I compress the same document twice, So maybe its not that much reliable. Another problem is that for one of my compression programs the execution time is very low (less than 1 ms) and hence it is not shown by time command.

---

### Post by MG&amp;TL on 2011-11-17
As a test, compile your compressing function separately as main() {} rather than compress() {} or whatever.

Then use time to measure the time used.

---

### Post by 11jmb on 2011-11-17
If you think that one or two functions are causing you problems, you will want to use gprof or the valgrind tool callgrind.

This may be a dumb question, but just in case, did you compile all of your libraries with -pg flags?

Post the outputs of time and gprof.


EDIT: by "all of your libraries" I mean only libraries that you are linking against

---

### Post by khurshid_coms on 2011-11-17
> **surfer said:**
> i don't have a direct answer to your question either, sorry.

i usually use valgrind to do my profiling. that way i see on which routines my programs spend most of the execution time.

```
$ sudo apt-get install valgrind  kcachegrind
```then, assuming your executable is called a.out:
```
$ valgrind --tool=callgrind ./a.out
```which generates a file called callgrind.out.PID (PID was the process number of you program) which you can then inspect with
```
$ kcachegrind callgrind.out.PID
```(remember to change the PID).

hope that helps.

Hi,
Thank you. I have installed it and executed it. Now I have the data, but I am unable to understand it. Please refer me some tutorial. Or Tell me how can reed the graph for the total executoin time of my compression. There are two things Incl and self. What does they mean. I am interested in total execution time of my compression.

---

### Post by khurshid_coms on 2011-11-17
> **11jmb said:**
> If you think that one or two functions are causing you problems, you will want to use gprof or the valgrind tool callgrind.

This may be a dumb question, but just in case, did you compile all of your libraries with -pg flags?

Post the outputs of time and gprof.


EDIT: by "all of your libraries" I mean only libraries that you are linking against

I have downloaded gzip library. Then I run ./configure. After that I  added -pg to the CFLAGS option in the makefile. Then I run make. I do not know if the whole library is complied with -pg option. I think this is the problem with me. How can I compile the whole library for profiling?

---

### Post by 11jmb on 2011-11-17
That should do it. in the future, a better way is to add the flags when you configure

```

CC="gcc -pg" CXX="g++ -pg" ./configure
```

possibly dumb question number 2: which gzip executable are you calling? There should be a gzip executable that is in /bin that came with your operating system, and the gzip executable that you installed from source is probably in /usr/bin

For your question about valgrind, were you unable to use Kcachegrind?

---

### Post by ofnuts on 2011-11-17
> **khurshid_coms said:**
> I had already tried time command. The problems is it shows two different execution time if I compress the same document twice, So maybe its not that much reliable. Another problem is that for one of my compression programs the execution time is very low (less than 1 ms) and hence it is not shown by time command.The second time around, your executable and your document file are in the disk cache, so are accessed faster. A third try would show  times similar to the second one.

---

