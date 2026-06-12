---
title: "Segmentation faults and UnpicklingErrors with Python on 12.04"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by kramer65 on 2012-05-01
Hello,

I've been running Ubuntu 12.04 since the second alpha and I've been really happy with it. Strangely enough though, since 12.04 was released on April 26th (and me updating to it) I suddenly had a lot of trouble with it.

Sometimes I can't close applications by clicking the red X-button on the left top and I need to close it through a right click in the Unity Dock, Apport crashes when trying to report problems, and one time Firefox totally refused to start and kept on crashing on me. The biggest problems I now run into however, are with Python.

I am currently writing some simple Python programs to analyse some data. I do this using [Spyder]("https://code.google.com/p/spyderlib/") as IDE and test it on the command line. A script using Pythons multiprocessing module used to run perfectly well (using all my four cores). Since this past weekend however, this script suddenly ends in errors. The errors are not constantly the same and they appear after various times and at various points in the script. The errors that appear are either Segmentation Faults (which I had never heard of before), or UnpicklingErrors (indicating an "*invalid load key, 'W'*", where W is sometimes also '8' or '['). I will post the total UnpicklingError below this message.

This weekend I did install some new things:[Antlr]("http://www.antlr2.org/") through synaptic, which I removed again, and I [tried to install]("http://ubuntuforums.org/showthread.php?t=1968889") java2python from source. I don't know if either of these have anything to do with it.

Does anybody know how I can solve this issue? Can I for example reinstall Python somehow? All tips are welcome!



UnpicklingError:
```
Process PoolWorker-4:
Traceback (most recent call last):
  File "/usr/lib/python2.7/multiprocessing/process.py", line 258, in _bootstrap
    self.run()
  File "/usr/lib/python2.7/multiprocessing/process.py", line 114, in run
    self._target(*self._args, **self._kwargs)
  File "/usr/lib/python2.7/multiprocessing/pool.py", line 85, in worker
    task = get()
  File "/usr/lib/python2.7/multiprocessing/queues.py", line 376, in get
    return recv()
UnpicklingError: invalid load key, 'W'.
Process PoolWorker-5:
Traceback (most recent call last):
  File "/usr/lib/python2.7/multiprocessing/process.py", line 258, in _bootstrap
    self.run()
  File "/usr/lib/python2.7/multiprocessing/process.py", line 114, in run
    self._target(*self._args, **self._kwargs)
  File "/usr/lib/python2.7/multiprocessing/pool.py", line 85, in worker
    task = get()
  File "/usr/lib/python2.7/multiprocessing/queues.py", line 376, in get
    return recv()
UnpicklingError: invalid load key, '8'.
Process PoolWorker-6:
Traceback (most recent call last):
  File "/usr/lib/python2.7/multiprocessing/process.py", line 258, in _bootstrap
    self.run()
  File "/usr/lib/python2.7/multiprocessing/process.py", line 114, in run
    self._target(*self._args, **self._kwargs)
  File "/usr/lib/python2.7/multiprocessing/pool.py", line 85, in worker
    task = get()
  File "/usr/lib/python2.7/multiprocessing/queues.py", line 376, in get
    return recv()
UnpicklingError: invalid load key, 'W'.
Process PoolWorker-7:
Traceback (most recent call last):
  File "/usr/lib/python2.7/multiprocessing/process.py", line 258, in _bootstrap
    self.run()
  File "/usr/lib/python2.7/multiprocessing/process.py", line 114, in run
    self._target(*self._args, **self._kwargs)
  File "/usr/lib/python2.7/multiprocessing/pool.py", line 85, in worker
    task = get()
  File "/usr/lib/python2.7/multiprocessing/queues.py", line 376, in get
    return recv()
UnpicklingError: invalid load key, 'W'.
```

---

