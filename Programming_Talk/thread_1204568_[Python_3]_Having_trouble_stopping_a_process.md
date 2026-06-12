---
title: "[Python 3] Having trouble stopping a process"
date: 2009-07-04
forum: Programming Talk
---

### Post by DustyMP on 2009-07-04
I'm trying to write a script for some programs I run routinely. The problem is that one is run in the terminal and only exits with a ctrl+c. I just can't manage to figure out how to pass it along. Everything I've tried so far interrupts it for half a second or so and it just keeps trucking along. The latest evolution looking something like:

```

import subprocess as sub, time
test = sub.Popen(['sudo airodump-ng mon0'], shell=True)
time.sleep(120)
test.terminate()

```

I'm trying to learn this language so I can move away from VBScript so any nudges in the right direction would be greatly appreciated =)

---

### Post by sub2007 on 2009-07-05
Have you tried sending a SIGKILL, SIGTERM or SIGABRT using send_signal()?

Otherwise, use os.system to execute a process kill using any relevant command that works.

---

### Post by snova on 2009-07-05
If it exits on Ctrl-C, send SIGINT.

```

import signal, subprocess, time

test = subprocess.Popen(["sudo airodump-ng mon0"], shell=True)
time.sleep(120)
test.send_signal(signal.SIGINT)

```

---

### Post by p0cky84 on 2009-07-05
Kill it, kill it with fire! aka. killall python(3?)

---

### Post by Empire537 on 2009-07-06
Just use:
```

import os
os.system('kiill processID')

```or if you don't have your processID

```

import os
os.system('killall myprocessname')

```

---

### Post by sub2007 on 2009-07-07
^You'll be able to get the pid from "test.pid" :)

---

### Post by DustyMP on 2009-07-13
Thanks all of you, killing it with the PID worked =)

---

