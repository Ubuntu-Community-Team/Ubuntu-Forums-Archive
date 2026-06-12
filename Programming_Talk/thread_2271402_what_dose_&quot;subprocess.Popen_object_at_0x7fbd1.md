---
title: "what dose &quot;subprocess.Popen object at 0x7fbd1a079d50&quot; mean"
date: 2015-03-29
forum: Programming Talk
---

### Post by lance bermudez on 2015-03-29
my code is 
```

#! /bin/python3.3
import subprocess

log_file = open ('command.log', 'a')

p = subprocess.Popen ('rsync -vaPhz --stats /home/lance/bin/ -e "ssh -p 22" 192.168.2.5:/home/lance/bin/python/bin',  stderr=subprocess.PIPE, stdout=subprocess.PIPE, shell=True)

print(p)

for line in iter (p.stderr.readline, ''):
    log_file.write ('>ERROR:' + line)

for line in iter (p.stdout.readline, ''):
    log_file.write (line)

log_file.close ()

```

error i get is
```

$ python test1.py
<subprocess.Popen object at 0x7fbd1a079d50>

```

What I'm trying to do is have the output print to screen and save to log file. I need some kind of output so that I know the script is working and not stuck.

---

### Post by Vaphell on 2015-03-30
p = subprocess.Popen (...) spawns an object

when you directly print an object that doesn't implement a __str__() method you get a run of the mill '<CLASS object at MEMORY_ADDRESS>' message. 

```
>>> class X:
...   pass
... 
>>> a = X()
>>> print(a)
<__main__.X object at 0x7fc819de3978>
>>> class X:
...   def __str__(self): return 'zomg'
... 
>>> a = X()
>>> print(a)
zomg
```

Apparently subprocess.Popen doesn't so the default is used and that's not how you are supposed to get to the relevant stuff.

And if you want to see output - you iterate over stdout/stderr already to write them line by line to files, why not also print these lines?

---

### Post by lance bermudez on 2015-03-31
I made some changes and still don't know what I'm doing but thanks for the help. I just hope I'm on the right track.
```

#! /bin/python3.3
import subprocess

log_file = open ('command.log', 'a')

p = subprocess.Popen(['rsync','-vaPhz','--stats','/home/lance/','-e','ssh -p 22','192.168.2.5:/home/acer/lance/'],  stderr=subprocess.PIPE, stdout=subprocess.PIPE, shell=True)

output = p.communicate()
print(output)

```

not sure what to do with this code. This is what I was told may be called a loop right. I did not know it was a loop or not.
```

for line in iter (p.stderr.readline, ''):
    log_file.write ('>ERROR:' + line)

for line in iter (p.stdout.readline, ''):
    log_file.write (line)

log_file.close ()

```

---

