---
title: "[CUDA] 2 GPUS, one process"
date: 2009-03-16
forum: Programming Talk
---

### Post by kjohansen on 2009-03-16
Is it possible to start in parallel two CUDA kernels.  I have a machine with two CUDA enabled GPUS and would like to run them in parallel. 

I could start two processes on the host and have each one call a different device and then have the host processes communicate with openmp and MPI, but I want to avoid the communication if possible.s 


EDIT: I think the below is wrong upon more reading, calls are asynchronous?
I am thinking this is not possible since the CUDA calls are blocking, correct? So if I had:

```

Kernel Call 1

get some results

Kernel Call 2

get some results

```

Kernel 1 would execute then block and then Kernel 2 would have to wait until call 1 was done, so there would be no real advantage to using them as two since they necessarily have to be sequentially executed if my logic is correct...

---

### Post by Ferrat on 2009-03-17
been looking at it a bit, threading might work

---

### Post by bfhicks on 2009-03-17
You could possibly do threading. However, using SLI with CUDA I believe it treats both devices as ONE device. So, you would have 2x streaming processors depending on your device.

If you don't have them SLI'd, then I think it is possible to treat them both separately, but you'd have to provide a multi-threaded manager above to make sure both cards get the appropriate data with the corresponding kernel. Also, I'm not sure how fast the bus is and what negative side effects you'd have with trying to push data from one CPU -> 2GPUs.

---

