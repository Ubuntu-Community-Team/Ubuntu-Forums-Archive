---
title: "Using the subprocess module in Python scripting: checking command exit status?"
date: 2015-11-11
forum: Programming Talk
---

### Post by neoh2 on 2015-11-11
hi all, 

So I'm trying to learn Python scripting on Ubuntu. I now know to call a command from the system I should use subprocess, but I'm not fully understanding it. I'm trying to work out how to call a function, have it run in the shell where I started my script as normal, but have my script check if the command exited correctly and store the error message from stderr if it does.

so far I've worked out:
```

#!/usr/bin/python
import subprocess as sub

try:
    sub.check_output(['*command*', '*arg*', '*target*'])
except sub.CalledProcessError as errData:
    errMsg = errData.output
    print(errMsg)

```

I think that the command runs, and the stderr from the command is being re-redirected back into my script; hence the need for the print function. However stdout goes missing, so if I were to call something like ```
ls -la ~/test
``` output will only be printed to the shell if there is an error. 

Reading the python docs, it sounds like subprocess.call() wouldn't intercept stdout, but also wouldn't catch stderr, and subprocess.check_call() wouldn't store the stderr message string. This leads me to guess that I need to use subprocess.Popen() but after reading back and forth I can't quite work out how I do it. 

Does anyone know how I can call a command from inside a Python script, have stdout and stderr print to the console as usual but also log stderr in the script? 

Thanks all!

---

### Post by Vaphell on 2015-11-11
if you don't care about realtime output you can do something like this

```
#!/usr/bin/env python3

import subprocess as sub

cmd = [ 'bash', '-c', '{ for i in {1..5}; do echo "$i"; echo "errrr #$i" >&2; sleep 1; done }' ]

print('cmd:  ', *("'{}'".format(a) for a in cmd))
proc = sub.Popen(cmd, stdout=sub.PIPE, stderr=sub.PIPE )   # intercepting both stdout and stderr
out, err = proc.communicate()
exit_code = proc.wait()
print('stdout:\n{}\nstderr:\n{}'.format(out.decode('utf-8'), err.decode('utf-8')))
print('exit code: {}'.format(exit_code))
```

that way you can put your hands on all output and do whatever you want with it.

if you are interested in reading in realtime it would be more like 

```
#!/usr/bin/env python3

import subprocess as sub

cmd = [ 'bash', '-c', '{ for i in {1..5}; do echo "$i"; echo "errrr #$i" >&2; sleep 1; done }' ]

print('cmd:  ', *("'{}'".format(a) for a in cmd))
proc = sub.Popen(cmd, stderr=sub.PIPE)   # stderr intercepted for processing purposes

for line in proc.stderr:                                # reading stderr on a per line basis
    print('[stderr] ', line.strip().decode('utf-8'))
exit_code = proc.wait()
print('exit code: {}'.format(exit_code))
```


reading both in a transparent manner is more of a pain and i haven't figured it out to a tee yet, some stackoverflow trawling is in order.

---

### Post by neoh2 on 2015-11-11
Thanks! 

I'm still very confused by the sheer complexity of Popen, but your examples helped give some context, (even if i don't understand it all lol!)

I made the following change to my first attempt, which works for my basic script. I think I understand a bit more what's going on now, but I'll have to experiment with your examples a bit, before making more complex scripts!

```

#!/usr/bin/python
import subprocess as sub

try:
    passData = sub.check_output(['*command*', '*arg*', '*target*'], stderr=sub.STDOUT)
    print(passData[:-2]
except sub.CalledProcessError as errData:
    errMsg = errData.output
    print(errMsg[:-1])

```

---

