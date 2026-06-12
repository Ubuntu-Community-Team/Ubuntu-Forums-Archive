---
title: "GCC clock"
date: 2012-01-06
forum: Programming Talk
---

### Post by sree88 on 2012-01-06
i have written a C code which has many function calls. my requirement is to get the time taken to execute a particular function in millisecs or microsecs i tried using the clock() function but the program doesnt complete execution.

---

### Post by lisati on 2012-01-06
*Thread moved to **Programming Talk**.*

Welcome to the forums.

If you comment out the calls to clock(), does the program work as expected?

---

### Post by Bachstelze on 2012-01-06
Post your code and describe the problem in more detail...

---

### Post by sree88 on 2012-01-06
i got the clock() function worked. there was some problem in the pgm. but canu explain how this code works

clock_t start,end;
double time;
start = clock();
//code to be executed
end = clock();
time= ((double) (end- start))/ CLOCK_PER_SEC;
printf("\n time:%f,(double)time);
}

i got this code from one of the ubuntu forums

---

### Post by Bachstelze on 2012-01-07
The clock() function returns (an approximation of) the amount of CPU time used by your program since it started. By substracting the two values, you get the amount of CPU time used by your program between the two calls to clock(), and dividing by CLOCKS_PER_SEC gives the time in seconds.

---

