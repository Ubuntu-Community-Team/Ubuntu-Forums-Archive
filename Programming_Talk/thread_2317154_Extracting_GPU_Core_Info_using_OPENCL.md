---
title: "Extracting GPU Core Info using OPENCL"
date: 2016-03-14
forum: Programming Talk
---

### Post by pradyot on 2016-03-14
Hi,
   I am using OPENCL for last two months and pretty much understood the  basics of it. I am working on NVIDIA QUADRO 410 card. At this point I  can write simple kernels and good host programs. 
Now I wanted to know if it is possible to fetch the core details of my  card when i am executing my kernel. I want to map a particular thread to  that core where it has performed the operation. The card I am using 
has 192 CUDA core (cuda core coz its NVIDIA) when I define the total  number of thread and the number of threads in the group , and when these  threads perform any operation say matrix multiplication , is it  possible to 
to see which thread gets executed in which cuda core. If yes how? 
     It would be very helpful if u can come up wih this answer as i have searched in internet and came up with nothing.
regards
Pradyot

---

### Post by pradyot on 2016-03-16
Hi,

Here's something I managed to figure out. I used a feature called inline  PTX to return the particular details of the thread . In this case i  used it to get the warp ID, warp lane ID and the streaming  multiprocessor ID. However the warp id and warp lane id is coming out as  expected(ie warp lane from 0-31 and each warp getting executing) the SM  ID is 0 (zero) for all the threads. When i checked the clinfo , the Max  compute units: 1. So does this mean that the SM ID is zero for all the  threads is zero because of that?

    Also how can my nvidia quadro 410 have Max compute units as 1 when there are 192 cuda cores?

---

