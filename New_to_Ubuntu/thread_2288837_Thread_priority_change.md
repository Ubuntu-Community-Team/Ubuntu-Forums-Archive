---
title: "Thread priority change"
date: 2015-07-30
forum: New to Ubuntu
---

### Post by Vinayaka_Negalur on 2015-07-30
Hello all,

Sorry if I am asking the same question again. But I did not find a suitable question to my problem in forum.

Background:
I have main function which is creating 2 threads. Thread1 is reading data from sensor1 @ 10ms and thread2 from some more sensor2 @100ms. Sensors are configured to send the data at the right rates. This is no doubt.

Coming to the problem now,
1. To read the data at 10ms, I am trying to increase the thread priority (to 60) of thread1 with FIFO policy. Yes, It gives me samples from sensor1 at a faster rate, but thread2 does not run at all.:confused:8-[ I did not increase priority of thread2.
I tried the same with RR policy also, but in vein.:mad:
2. When I use top/htop command, I do not see the thread name displayed. how can I have the thread name seen in the top command result?

Further observations:
When I do not set explicit priority to Thread1, I have both the threads running and values being read from both the sensors, but the rate is not fulfilled. Both the  sensor values are read one after the other

Any hints to achieve the higher rate for thread1!!:confused::confused:[-o

---

### Post by Vinayaka_Negalur on 2015-07-30
Please note, I have used below code to set the thread priority.
```

    struct sched_param param;
    param.sched_priority = 60;
    pthread_setschedparam(pthread_self(), SCHED_RR, &param);

```

---

### Post by dino99 on 2015-07-30
what return did you get from a terminal:
> nice thread2name 5 &

when your thread(s) are ran, how their data are hold ? then how they are read ? Do you have define some arrays ?

---

### Post by Vinayaka_Negalur on 2015-07-30
Hi Dino99,

I do not get any output for thread2name.
```

root@root:~# nice: thread2name: No such file or directory

[1]+  Exit 127                nice thread2name 5

```

The data from the threads are copied to the data structure whose type is defined by the sensors. And these data are further forwarded to applications via IPC. Currently to send the data to client we use message queue.

---

### Post by Vinayaka_Negalur on 2015-08-04
Hello all,

Can you please let me know if any of you have any thoughts. I am not able to make progress even after debugging for 2 days now.:(:confused::frown:

---

