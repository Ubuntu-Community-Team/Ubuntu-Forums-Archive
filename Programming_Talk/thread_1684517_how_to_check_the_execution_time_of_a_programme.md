---
title: "how to check the execution time of a programme"
date: 2011-02-09
forum: Programming Talk
---

### Post by Praveen30 on 2011-02-09
Is there any method so that i can determine the execution time of my c programmes???

---

### Post by cipherboy_loc on 2011-02-09
To time it:

```

time [program name]

```


Cipherboy

---

### Post by Praveen30 on 2011-02-09
> **cipherboy_loc said:**
> To time it:

```

time [program name]

```
Cipherboy


like if my programme name is reverse.c, then on the terminal i have to write it like this--

time [reverse.c]??:confused:

---

### Post by fct on 2011-02-09
No. Once compiled as "reverse":

$ time ./reverse

Just like a normal execution, but with "time" before.

---

### Post by Praveen30 on 2011-02-09
> **fct said:**
> No. Once compiled as "reverse":

$ time ./reverse

Just like a normal execution, but with "time" before.
 
ok i have found this..

```

praveen@ubuntu:~/Desktop$ gcc pid.c
praveen@ubuntu:~/Desktop$ time ./a.out
process id=4625
real    0m0.002s
user    0m0.000s
sys    0m0.000s

```

can you explain this real, user,sys??

---

### Post by Arndt on 2011-02-09
> **Praveen30 said:**
> ok i have found this..

```

praveen@ubuntu:~/Desktop$ gcc pid.c
praveen@ubuntu:~/Desktop$ time ./a.out
process id=4625
real    0m0.002s
user    0m0.000s
sys    0m0.000s

```

can you explain this real, user,sys??

I tried to find a good place to point to among the manual pages, but couldn't.

"real time" is the actual time that has elapsed. It's also often called wall clock time. The two others are parts of the time the computer did actual work for you: "sys" is when the operating system did something on your behalf, and "user" is the time your program itself took.

For example:

```
$ time sleep 5

real	0m5.003s
user	0m0.010s
sys	0m0.000s
```

Here, five seconds elapsed, but almost no code was run for you.

```
$ time du ~ >/dev/null
real	0m2.450s
user	0m0.430s
sys	0m1.780s

```

Here, I asked for a summary of disk usage, where most of the time was spent by the operating system doing things on the disk.

```
$ time ssh-keygen -b 4000 -f /tmp/kk -N '' -q

real	0m4.642s
user	0m4.420s
sys	0m0.020s
```

This command (never mind the details) generated a 4000-bit key, which is very CPU intensive, so most of the time will be found in the "user" category.

---

### Post by Rany Albeg on 2011-02-09
**_Real_** is wall clock time - time from start to finish of the call. This is all elapsed time including time slices used by other processes and time the process spends blocked (for example if it is waiting for I/O to complete).


**_User_** is the amount of CPU time spent in user-mode code (outside the kernel) within the process. This is only actual CPU time used in executing the process. Other processes and time the process spends blocked do not count towards this figure.


**_Sys_** is the amount of CPU time spent in the kernel within the process. This means executing CPU time spent in system calls within the kernel, as opposed to library code, which is still running in user-space. Like 'user', this is only CPU time used by the process.

---

