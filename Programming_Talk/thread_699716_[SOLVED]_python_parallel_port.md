---
title: "[SOLVED] python parallel port"
date: 2008-02-17
forum: Programming Talk
---

### Post by bschleusner on 2008-02-17
has ANYONE been able to get python to access the parallel port? :confused:

I have been trying for days and have got know where except very frustrated. Whenever I try to do anything it just gives me a bunch of bull about how the device does not exist!?!?!

Anyone?:evil:

---

### Post by ghostdog74 on 2008-02-17
how are you trying to access it?

---

### Post by bschleusner on 2008-02-17
I am using the pyParallel module.

import parallel
p = parallel.Parallel()

---

### Post by ghostdog74 on 2008-02-17
and ?? what else??

---

### Post by bschleusner on 2008-02-17
I don't know, it always errors out after that. I get:

```
>>> import parallel
>>> p = parallel.Parallel()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/parallel/parallelppdev.py", line 189, in __init__
    self.setDataDir(1)
  File "/usr/lib/python2.5/site-packages/parallel/parallelppdev.py", line 509, in setDataDir
    self.PPDATADIR(out)
  File "/usr/lib/python2.5/site-packages/parallel/parallelppdev.py", line 458, in PPDATADIR
    fcntl.ioctl(self._fd, PPDATADIR, msg)
IOError: [Errno 22] Invalid argument
```

do you know of a different way to send data out of the parallel port in python? What am I doing wrong with pyParallel?

---

### Post by zero-9376 on 2008-02-17
i ran into this same issue during my thesis, in order to use pyparallel you will need to unload the lp driver and load the ppdev driver

sudo rmmod lp
sudo modprobe ppdev

if you are going to be using the port all the time consider blacklisting the lp module.

---

### Post by ghostdog74 on 2008-02-17
make sure you get all installation requirement correct. Have you installed Javacomm?

---

### Post by bschleusner on 2008-02-17
> **ghostdog74 said:**
> make sure you get all installation requirement correct. Have you installed Javacomm?
yeah, it's there.

> 
sudo rmmod lp
sudo modprobe ppdev
It didn't seem to do anything, I keep getting the same error... What can I do to pinpoint the cause?

---

### Post by ghostdog74 on 2008-02-17
other areas to check maybe your BIOS, make sure if there are options to turn on/off parrallel port. Or at the Operating System, see if there are any settings about parallel ports. Also you may need to add ppdev to /etc/modules.

---

### Post by bschleusner on 2008-02-17
could it be that the new kernel version has an incompatible version of fcntl, and that's why it is not working? It seems to be the end-of-the-line for the debug output....

---

### Post by bschleusner on 2008-02-18
ok, I gave up on the pyParallel module, portio is working perfect. :popcorn:

thanks for all who helped!!!!

---

### Post by dwblas on 2008-02-19
Please add "Solved" to the title.  People periodically ask about parallel port access so adding "Solved" will point them here in the beginning.  It would be good to know to try portio if pyparallel does not work.

---

### Post by anonymousnobody on 2008-07-21
Did you check the permission on the actual device? I was doing stuff on the serial port and it was giving me errors. So I went into /dev/ttyS0 and changed the permissions so that I could read and write to it as "other."

---

