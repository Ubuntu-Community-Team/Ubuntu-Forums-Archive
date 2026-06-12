---
title: "pthread_cond_wait() CPU usage"
date: 2013-01-11
forum: Programming Talk
---

### Post by bird1500 on 2013-01-11
It looks like each wait using this method consumes like 0.5-0.7% of CPU.
To me it's a lot of CPU, when waiting in like 8 threads (doing nothing) the app uses like 4-5% of CPU!
Can I do anything about it?

See [this youtube]("http://www.youtube.com/watch?v=H2O33p7wco8") video (at 1080p), process name "ufbio".

The relevant waiting code for each thread's cond_wait:
```

while(hints.bits & UFB_BIT_PAUSED) {
L;
    status = pthread_cond_wait(&hints.cond, &hints.mutex);//HERE each thread waits
L;
    if(status != 0) {
        ufbErr(status);
    }
    if(hints.bits & UFB_BIT_CANCELLED) {
        break;
    }
}

```"L;" prints "PING" plus the current line and function, like "PING {253}{ioCopy}", it shows up in the video in the terminal to prove the threads are doing nothing else.

---

### Post by bird1500 on 2013-01-12
The reason for high CPU usage was another thread copying stats from all (including paused) I/O threads to display the stats in the GUI. Now that it only copies stats from working threads the CPU usage is below 1% when all I/O threads are paused, that is, pthread_cond_wait()ing. Problem solved.

Now that it's fixed, here's [the new vid]("http://www.youtube.com/watch?v=2Nhu_s_Hyt8") with low CPU usage.

---

### Post by DaviesX on 2013-01-12
What project are you working on ? Just curious

---

### Post by bird1500 on 2013-01-12
A file browser for myself - ufb (ubuntu file browser), on the video is a complement of it, the I/O program that runs independently - ufbio - the best part of the latter is that you can pause/resume file I/O operations which is helpful since the desktop Linux typically stutters (sometimes a lot) more than Windows when doing I/O (people noticed it a long time ago, but no one really fixed it, and random people experience it, very weird, might be a collection of bugs).

Nautilus (the worst one), thunar, pcman aren't good enough for me.

---

### Post by DaviesX on 2013-01-12
Cool, hope it could be in the repository :) > since the desktop Linux typically stutters (sometimes a lot) more than Windows when doing I/O (people noticed it a long time ago, but no one really fixed it, and random people experience it, very weird, might be a collection of bugs).

I experience it too. That is because Linux's multi-task mechanism. Since linux is targeted on servers which is usually I/O intense and I/O typically wastes more time to finish a task than others, it gives I/O processes more time slices(by a static weight) than other processes. In addition, the maximum time slice in linux is 800ms in contrary to windows 95's 20ms (I don't know the current version's)

---

### Post by bird1500 on 2013-01-12
Glad it's not a bug, hopefully someone someday makes it a configurable option in some kernel config file so that I can change its value (closer to 20ms) while not having to recompile the kernel. I guess a lot of desktop Linux  users would like to buy him a beer.

---

