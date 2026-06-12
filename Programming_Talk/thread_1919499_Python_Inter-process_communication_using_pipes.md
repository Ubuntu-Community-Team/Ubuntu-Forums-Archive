---
title: "Python Inter-process communication using pipes"
date: 2012-02-03
forum: Programming Talk
---

### Post by ve4cib on 2012-02-03
I am trying to wrap my brain around using pipes to communicate between two processes with Python.  However, I am obviously doing something wrong, since I keep getting EOF errors.

To start with I am just trying to get two very, very simple scripts working:

**main.py**
```
#!/usr/bin/python
import subprocess

client = subprocess.Popen('./foo.py',stdin=subprocess.PIPE,stdout=subprocess.PIPE,shell=True,bufsize=256)
(stdout,stderr) = client.communicate('hello')
print stdout
(stdout,stderr) = client.communicate('world')
print stdout
(stdout,stderr) = client.communicate('exit')
```

**foo.py**
```
#!/usr/bin/python

s = raw_input()
while s != 'exit':
    print '#',s
    
    s = raw_input()

```

When I run main.py I get this as output:
```
$ ./main.py 
Traceback (most recent call last):
  File "./foo.py", line 7, in <module>
    s = raw_input()
EOFError: EOF when reading a line
# hello

Traceback (most recent call last):
  File "./main.py", line 7, in <module>
    (stdout,stderr) = client.communicate('world')
  File "/usr/lib/python2.7/subprocess.py", line 740, in communicate
    return self._communicate(input)
  File "/usr/lib/python2.7/subprocess.py", line 1271, in _communicate
    self.stdin.flush()
ValueError: I/O operation on closed file
```

What I was expecting to get is
```
$ ./main.py
# hello
# world
```

I think the problem is that the subprocess is simply dying too soon, and not staying open to accept input multiple times.  How do I get the child process to simply wait for input, instead of dying when it hits an EOF?  Do I just need to put a try/except block in the child process?  That seems kind of hacky though.  I'm hoping for a cleaner solution if one exists.

Any suggestions or links to documentation with example code would be greatly appreciated.  Thanks a lot!

---

### Post by StephenF on 2012-02-03
From the docs: 
> 
Interact with process: Send data to stdin. Read data from stdout and stderr, until end-of-file is reached. Wait for process to terminate. 

So you only get to use it once.

Instead you want something like:
```

client.stdin.write("command1\n")
print client.stdout.readline()
client.stdin.write("command2\n")
print client.stdout.readline()

```

---

