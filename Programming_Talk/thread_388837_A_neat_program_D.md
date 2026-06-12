---
title: "A neat program :D"
date: 2007-03-20
forum: Programming Talk
---

### Post by slavik on 2007-03-20
This is my next assignment for class ... a multithreaded matrix multiplier

takes 2 matrices (each of max size 200 by 200) and multiplies them :D

all the stuff attached ...

JOBS controls the number of threads to use
MSIZE controls the size of the matrices (if MSIZE is 10, each matrix is 10 by 10).

place all files in a single directory.

the program creates 2 files, matrix_result (with the result) and matrix_log which tells how many cells each thread computed ...

extract into a dir and simply run the perl script, which will compile, run and analyze the results.

please post the output and what kind of system you have (CPU type, number of CPUs, and the clock rate for the CPU).

---

### Post by dport113 on 2007-03-20
0.58user 0.03system 0:00.45elapsed 135%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+602minor)pagefaults 0swaps
thread 0 = 10066
thread 1 = 9335
thread 2 = 6103
thread 3 = 11201
thread 4 = 3295
total = 4000

4-  Intel Xeon 5300 (quad core) 16 cores, wooo.

---

### Post by slavik on 2007-03-20
change the number of jobs to 17, I wonder what will happen. :)

oh yeah, and I will generate 1000 by 1000 matrices later ^^

interestingly ... this is mine on a single 32bit CPU (with 5 JOBS)

0.25user 0.02system 0:00.27elapsed 99%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+522minor)pagefaults 0swaps
thread 0 = 13932
thread 1 = 22114
thread 2 = 2274
thread 3 = 951
thread 4 = 729
total = 40000

---

### Post by dport113 on 2007-03-20
17 jobs.

0.58user 0.01system 0:00.37elapsed 160%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+654minor)pagefaults 0swaps
thread 0 = 7085
thread 1 = 6791
thread 2 = 11696
thread 3 = 8245
thread 4 = 1084
thread 5 = 1393
thread 6 = 620
thread 7 = 1528
thread 8 = 1213
thread 9 = 345
total = 40000

---

### Post by dport113 on 2007-03-20
17 workers 1000x1000 matrices

85.76user 0.44system 0:47.79elapsed 180%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+8905minor)pagefaults 0swaps
thread 0 = 120503
thread 1 = 107078
thread 2 = 114239
thread 3 = 117348
thread 4 = 129364
thread 5 = 118305
thread 6 = 116123
thread 7 = 58985
thread 8 = 55405
thread 9 = 62650
total = 1000000

---

### Post by slavik on 2007-03-20
JOBS = 5
32bit 2.4GHz AthlonXP 2500M

50.73user 0.33system 1:01.50elapsed 83%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+8022minor)pagefaults 0swaps
thread 0 = 201309
thread 1 = 200883
thread 2 = 203227
thread 3 = 197345
thread 4 = 197236
total = 1000000

JOBS = 10
32bit 2.4GHz AthlonXP 2500M
52.00user 0.35system 1:02.70elapsed 83%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+8032minor)pagefaults 0swaps
thread 0 = 136819
thread 1 = 33276
thread 2 = 109990
thread 3 = 224833
thread 4 = 32390
thread 5 = 188472
thread 6 = 165403
thread 7 = 39418
thread 8 = 35452
thread 9 = 33947
total = 1000000

---

### Post by dport113 on 2007-03-20
806.22user 0.50system 0:50.63elapsed 912%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+8888minor)pagefaults 0swaps
thread 0 = 110259
thread 1 = 96303
thread 2 = 140429
thread 3 = 111488
thread 4 = 130329
thread 5 = 135246
thread 6 = 125376
thread 7 = 61578
thread 8 = 35144
thread 9 = 53848
total = 1000000

---

### Post by russell.h on 2007-03-20
Athlon 64 3800+ x2 (thats dual core)

0.33user 0.02system 0:00.20elapsed 174%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+616minor)pagefaults 0swaps
thread 0 = 11793
thread 1 = 9179
thread 2 = 9697
thread 3 = 8616
thread 4 = 715
total = 40000

---

### Post by maxamillion on 2007-03-20
I am curious (but too lazy to look at your source code) but when you say "multiply" do you mean algebraic or boolean?

---

### Post by slavik on 2007-03-20
I mean matrix multiplication from math ...

---

### Post by hod139 on 2007-03-20
My understanding of boolean matrix math is when the matrices consist soley of zeros and ones.  However, I'm not sure if this is what maxamillion meant, only he/she can clarify.

---

### Post by t4thfavor on 2007-03-20
Pentuim M 1.6 1.5Gig Ram
thread 0 = 9438
thread 1 = 5010
thread 2 = 2482
thread 3 = 1670
thread 4 = 21400
total = 40000

Im sad cause I have to use my fast PC for work, which means no Ubuntu :(

---

