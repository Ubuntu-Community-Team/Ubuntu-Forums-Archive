---
title: "timeout &amp; memout"
date: 2009-05-15
forum: Programming Talk
---

### Post by Zugzwang on 2009-05-15
Hi all, does any one of you know some tool (like "timeout") such that a program can be run with limits on both its maximum running time (in this case, it doesn't really matter whether it's wall-clock time or process computation time) *and* a given memory limit. 

I've tried building a "memout" script myself and combining it with an external timeout script (in some benchmark execution program), but it has the problem that when it gets terminated (by some external timeout tool), sub-processes of the process to be ran are not also killed. Also, sending SIGTERM instead of SIGKILL seems to be having no effect (is it possibly caught by the shell?).

[PHP]
#!/usr/bin/python
import os
import sys
import resource
import subprocess
import signal

def handler(signum, frame):
    print "Terminated!"
    os.kill(p.pid,signal.SIGKILL)
    p.poll()
    print "Waited!"
    exit()

try:
    limit = int(sys.argv[1])*1024.0*1024.0
except:
    print "Usage: memout <LIMIT IN MB> <COMMAND>"

resource.setrlimit(resource.RLIMIT_AS,(limit,limit))
p = subprocess.Popen(" ".join(sys.argv[2:]), shell=True)
signal.signal(signal.SIGTERM, handler)
sts = os.waitpid(p.pid, 0)
[/PHP]

---

### Post by imdano on 2009-05-15
Try using the atexit module instead of catching SIGTERM and see if that makes a difference.  You can probably handle the timer stuff by using the sched module, threading.Timer, or hooking up to a gobject mainloop and using the gobject.timeout_add method.

---

