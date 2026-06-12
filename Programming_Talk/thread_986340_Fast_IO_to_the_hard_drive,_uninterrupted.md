---
title: "Fast I/O to the hard drive, uninterrupted"
date: 2008-11-18
forum: Programming Talk
---

### Post by Xyro on 2008-11-18
I am writing some code to handle real time data, writing it to disk. I need to ensure that my process has complete (or near enough to complete) control over one of my CPUs. I have scheduled it as a SCHED_FIFO with a sched_param of 99 (using sched_setscheduler()), which has sped it up considerably. However, the write progression is still interrupted, causing single writes to take way to long, what seems to be every 5 seconds. Note: The individual line write speeds and total average line write speeds are fine, it is just the spikes that will cause problems.

A few questions:

When a process is set to SCHED_FIFO, does the 'nice value' set using setpriority() become irrelevant? In other words, will setting the nice value to -20 for my process have any effect if I have also scheduled it to be a SCHED_FIFO process? (I've done the FIFO part after the nice part)

I am running this on a WD Raptor (10K) with a 16MB buffer, could the buffer have anything to do with this issue?

Are there any other system calls for the CPU scheduling that supersede the ones mentioned?

Really, what I am wondering is why I am able to write ~4000 lines of data (each 8192 Bytes long) at about 0.1 - 0.2 microseconds per line, then have that jump to 80 milliseconds for a single line, followed by ~4000 writes again at 0.1 - 0.2 microseconds per line. The spikes seem to be exactly 5 seconds apart, if that helps any.

Any info would be greatly appreciated. Thanks in advance.

---

### Post by slavik on 2008-11-18
nice -20 :)

---

### Post by Cracauer on 2008-11-18
What you want isn't possible.

Even if you bind to a processor, just the fact that a kernel without hard real time support switches between kernel and userland mode ruins all guarantees. Furthermore, the delayed nature of writes to a Linux filesystem ruins it, because you write into memory and an asynchronous process later writes it to disk in bursts.

You can use O_SYNC but then base performance is horrible and your disk might not like it at all.

Just don't do anything else on the machine, that should do.

You might want to do things like using taskset to bind sshd and all children to one CPU, that way you can log in and check things without taking the same CPU.

But the core problem remains: the CPU is the least of your problems. The bigger problem is other I/O activity.

---

### Post by psusi on 2008-11-18
You want O_DIRECT and a file that is preallocated, or better yet, write directly to a disk/partition and not use a filesystem at all.  I wouldn't think the delay would be as large as 80 ms on a 10k rpm drive, but my guess is that every 5 seconds ext3 hits the journal causing the drive to seek to a different part of the disk,, then have to return.

Out of curiosity, why can't you tolerate any latency?  Can't you buffer more of the data and let it flush to disk lazily in the background?

---

### Post by tomchuk on 2008-11-18
It looks like you've got your CPU scheduling tweaked as far as it will go. I/O scheduling is the next step...

Have you tried changing the I/O scheduler for the device? Default in recent kernels is CFQ (Complete Fair Queueing) - it seems that what you're after is complete UNfair queueing. Try the noop, deadline or anticipatory scheduler and see if your results improve.

If you're on ext3 you can try setting the journaling to journal_data_writeback with tune2fs to overcome any overhead in writing to the journal. Or mount as ext2.

There is also the realtime switch to ionice which may help a bit at the expense of starving other processes.

---

### Post by Xyro on 2008-11-19
Hey! Thanks for the responses all. Looks like I have a few things to try out.

"Just don't do anything else on the machine, that should do."

The system is running a lean Ubuntu server, no GUI, just openSSH installed. That is it. Can't possibly run anything less (as far as I know).

"Out of curiosity, why can't you tolerate any latency? Can't you buffer more of the data and let it flush to disk lazily in the background?"

The system will be a data acquisition box and be pulling down data at a high rate for quite some time. I might be able to buffer it, but I'm not sure I will have the buffer space, due to the duration of the acquisition. Since I'd rather not rely on a buffer I'd prefer direct writing, but I will look into this. The reason for is that the data is not repeatable within a reasonable time or financial window. A botched run due to buffer overrun would not be acceptable.

"If you're on ext3 you can try setting the journaling to journal_data_writeback with tune2fs to overcome any overhead in writing to the journal. Or mount as ext2.

There is also the realtime switch to ionice which may help a bit at the expense of starving other processes."

I am running ext3, I will look at tune2fs or possibly the ext2 fs. I think you (and others above) are correct, it is quite possible an io scheduling problem. I hadn't thought of that.

Thanks again for all the feedback.

---

### Post by Cracauer on 2008-11-19
So what happens if your machine crashes?

In general, if you have data comping in at a higher rate than your disk throughput you'll lose if it happens for longer than it takes to fill up RAM with buffered dirty pages. What is your expected average and max rate?

In general, you seem to misunderstand how disk writes work. And you familiar with the concepts of O_SYNC and O_DIRECT? Do you know whether you want to or have to use any of these?

On a clean Ubunutu there's still a megaton of useless demons. And did you remember to turn off the locatedb cron job?

---

### Post by Xyro on 2008-11-19
The file I am writing the data to:

```
ifd = open(fname,O_WRONLY|O_LARGEFILE|O_CREAT|O_DIRECT,S_IRWXU);
```

---

### Post by psusi on 2008-11-19
You seem to misunderstand buffering.  Either the disk can keep up with the load or it can't; buffering won't change that.  What it will do is smooth over any hickups like the one you are seeing, provided that the disk can catch back up.

Why don't you just write to the file normally, allowing the system to buffer as it chooses, and not worry about how long an individual write takes to hit the disk?  As long as it all gets there eventually, everything is good no?

---

### Post by Cracauer on 2008-11-19
> **Xyro said:**
> The file I am writing the data to:

```
ifd = open(fname,O_WRONLY|O_LARGEFILE|O_CREAT|O_DIRECT,S_IRWXU);
```

Woah. I don't think that O_DIRECT does what you want here.

So again, what happens if the box crashes?

---

### Post by Xyro on 2008-11-19
If the box crashes, that would be bad. Thus, I am simulating the data handling to ensure this does not happen. I've yet to crash it.

---

### Post by Cracauer on 2008-11-19
> **Xyro said:**
> If the box crashes, that would be bad. Thus, I am simulating the data handling to ensure this does not happen. I've yet to crash it.

What happens on a power fail? Disk death? Power supply death?

Anyway, do you understand what O_DIRECT does, exactly? That it cuts the maximum write throughput to about 1/10th of the normal rate? That it puts enormous load on the disk and might kill the disk?

---

### Post by psusi on 2008-11-19
> **Cracauer said:**
> 
Anyway, do you understand what O_DIRECT does, exactly? That it cuts the maximum write throughput to about 1/10th of the normal rate? That it puts enormous load on the disk and might kill the disk?

No, that is not what it does.  What it does is disable the kernel buffering and all IO goes directly to the disk.  This requires that the buffers and offsets all be page aligned.  Since the request is not completed until it actually hits the disk, you want to use aio or multiple threads to issue more than one request at a time to keep the drive busy.

---

### Post by Cracauer on 2008-11-19
> **psusi said:**
> No, that is not what it does.  What it does is disable the kernel buffering and all IO goes directly to the disk.  This requires that the buffers and offsets all be page aligned.  Since the request is not completed until it actually hits the disk, you want to use aio or multiple threads to issue more than one request at a time to keep the drive busy.

Exactly. But the throughput is 1/10th (roughly) compared to normal files. Since there doesn't seem to be any protection against dead computers I really don't think that the right tool has been chosen here. And the constant seeking will kill desktop harddrives.

I have the throughput numbers somewhere in case anyone cares.

---

### Post by psusi on 2008-11-19
> **Cracauer said:**
> Exactly. But the throughput is 1/10th (roughly) compared to normal files. Since there doesn't seem to be any protection against dead computers I really don't think that the right tool has been chosen here. And the constant seeking will kill desktop harddrives.

I have the throughput numbers somewhere in case anyone cares.

If you don't use aio or multiple threads to issue multiple requests at once, throughput will go down.  How much depends on a lot of things.  I don't see what it has to do with crashing at all, and it doesn't cause seeking for no reason either.  It just takes more control from the kernel and gives it to the application.

---

### Post by Cracauer on 2008-11-19
> **psusi said:**
> If you don't use aio or multiple threads to issue multiple requests at once, throughput will go down.  How much depends on a lot of things.  I don't see what it has to do with crashing at all, and it doesn't cause seeking for no reason either.  It just takes more control from the kernel and gives it to the application.

Right, no seeks. You wait for another resolution of the disk most of the time but the head doesn't move. Sorry.

My point was that O_SYNC is normally used for high safety applications. When you write it you want to know it's on your disk. For normal applications you might have computer downtime but then you don't lose any data because the application isn't running.

If there's a live data feed our in the world and your computer receives it downtime of your computer means you lose some of that feed. So I don't think using O_SYNC is the right thing to do here. What's the point of waiting 10 times longer for the disk to make sure every block arrives when you'll lose tons of data on downtime.

Anyway, I think the OP uses O_SYNC in an attempt to ensure that blocks are written in a timely manner, but this seems to be grounded in a misunderstanding about how the filesystem buffer cache works, and also about how slow O_SYNC is. Overall this seems to make the situation worse, not better.

---

### Post by psusi on 2008-11-19
> **Cracauer said:**
> Right, no seeks. You wait for another resolution of the disk most of the time but the head doesn't move. Sorry.

No, you don't because disks have read ahead caches on them so they keep right on reading data that passes under the head so it's ready when you get around to requesting the next block.

> **Cracauer said:**
> Anyway, I think the OP uses O_SYNC in an attempt to ensure that blocks are written in a timely manner, but this seems to be grounded in a misunderstanding about how the filesystem buffer cache works, and also about how slow O_SYNC is. Overall this seems to make the situation worse, not better.

Yes, it doesn't sound like he has any reason to use O_SYNC, but again, it only slows things down if used naively.  As long as you keep multiple requests in flight concurrently you don't loose performance.

---

### Post by Cracauer on 2008-11-20
> **psusi said:**
> No, you don't because disks have read ahead caches on them so they keep right on reading data that passes under the head so it's ready when you get around to requesting the next block.


But he's only writing to the disk, isn't he?

> **psusi said:**
> 

Yes, it doesn't sound like he has any reason to use O_SYNC, but again, it only slows things down if used naively.  As long as you keep multiple requests in flight concurrently you don't loose performance.

Well, he's got a single stream coming in, that's my understanding.

So there's no parallelism there and the only way to get it would be for the application to buffer.

That would be just a poor man's filesystem buffer cache. Unless the sender of the data has a mechanism that you can tell it what you received and what you didn't and you build a kind of tagged queue scheme.

Unfortunately it seems we won't hear much of the OP anymore :(

---

### Post by Xyro on 2008-11-20
> **Cracauer said:**
> 
Unfortunately it seems we won't hear much of the OP anymore :(


Sorry, I've been trying out tweaking the IO priorities. I ran into some troubles with the ioprio header, updated the rt kernel, only to discover that my program would not run properly any longer. So a reinstall and set up later, here I am :P.

Adjusting the IO priorities, I have managed to make some significant improvements when running short simulations of 200,000 lines (~20 seconds of constant 8192 byte size writes to the disk). However, when I increase the number of writes to 1,000,000, I start seeing ~1.0 second hangs at about write #500,000. This is using the O_DIRECT modifier in open(). If I use O_SYNC, I lose the great performance from write #1 - 500,000, but I don't get any huge hangs. Using O_SYNC I am seeing very small (but still too large, ~25ms) periodic hang (almost exactly every 5 seconds) throughout the entire process.

I am having troubles using ioprio.h, which is supposed to enable the use of ioprio_set. It isn't working as the header isn't located in the 'include/linux' folder, it is in a header package folder buried in /src/. When I call it from here I receive a host of new errors as it is unable to recognise the functions etc. within ioprio.h. This may just be my own ignorance of how these things work, as I am fairly new to the programming/linux world. I have, however, been able to set the io priorities with ionice in a second terminal while the primary process waits for input before I've had it modify any CPU priorities. This works, but its not so elegant.

I am currently running  some tests with ext2, I will update when I have that info.

---

### Post by Cracauer on 2008-11-20
I think that using neither O_DIRECT nor O_SYNC will do what you want. Just plain writes is what you need.

And I don't think you need to set any kind of priority mission clearance for these things as long as there is no other process doing anything with the same disk. In any case, ioprio is something you use from the commandline utility `ionice`. But it only affects reads these days so the effect is NIL here.

Overall I see no reason to do anything special here except that you might want to increase the frequency of fsync calls over the standard in Linux.

---

### Post by Xyro on 2008-11-20
Ah, sorry. Should have posted that too. Using neither produces terrible results, with many many hang ups of larger hang times.

---

### Post by psusi on 2008-11-20
Where are you getting this real time data from, and why can't the source tolerate you not reading it for 25 ms?  If you can't fix the source to relax those requirements you will need to use one process to do nothing but read from it to a buffer in ram, and use another process to handle writing the buffer to disk more lazily.

---

### Post by slavik on 2008-11-20
I have to ask. The thing that outputs this realtime data ... how much data does it produce in one second? (give us the absolute maximum it can spit out in one second).

---

### Post by bsmith1051 on 2008-12-18
Have you considering leaving the standard I/O routines and instead overbuild the drives, i.e., a multi-disk array?  That way even if there are periodic interruptions the array can easily catch-up.

---

