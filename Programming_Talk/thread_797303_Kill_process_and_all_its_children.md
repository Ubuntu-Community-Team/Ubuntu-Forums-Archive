---
title: "Kill process and all its children"
date: 2008-05-17
forum: Programming Talk
---

### Post by [h2o] on 2008-05-17
I use python to spawn a subprocess (using subprocess.Popen or os.popen, should not matter I think?).

I can get the PID of the spawned process, which is most often a shell.
If I use os.kill(PID, signal.SIGKILL) the shell process is killed as expected, but any subprocesses of the shell lives on (its parent is just set to init (1)).

I want to know how I can, given a PID, kill that process and **any other process it or any of its children might have spawned**.

I know I can parse output from "ps" and recursively find all other processes and kill them of one by one. But it just doesn't strike me as the best solution.

Any advice?

The solution must work on Linux with Python 2.5

---

### Post by fyplinux on 2008-05-18
Is it possible to get a process group including all the subprocesses, then kill the group?

---

### Post by slavik on 2008-05-18
when you send a signal to the parent, the children should also receive it. if the parent is killed, the children should die, too. unless the Python interpreter is doing something behind the scenes.

---

### Post by [h2o] on 2008-05-18
> **slavik said:**
> when you send a signal to the parent, the children should also receive it. if the parent is killed, the children should die, too. unless the Python interpreter is doing something behind the scenes.

That's what I thought but it is not always true.
Try with python:
```

import subprocess
p = subprocess.Popen('python',shell=True)

```
Then in terminal run 'ps -Af' and locate your two new processes (one "sh" and one "python").
Then kill off the parent ("sh") process using "kill" or "os.kill" and watch how the python process will have detached from the shell and now have "init" as its parent.

---

### Post by thebigkevdogg on 2009-01-29
Hey I'm having the same problem. Did anyone ever figure out the solution to this? Thanks!

---

### Post by thebigkevdogg on 2009-01-29
From what I understand, the only good way to do this is use shell=False. That worked for me at least. If you have to do things like piping and ridirecting though, it will be more complicated.

---

