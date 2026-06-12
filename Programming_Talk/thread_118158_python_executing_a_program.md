---
title: "python executing a program"
date: 2006-01-16
forum: Programming Talk
---

### Post by Luggy on 2006-01-16
Heyhey,

I'm looking to make a python app that will execute another program (mencoder). Can anyone show me how to do this or point me at a tutorial that can?

Thanks a bunch!

---

### Post by gord on 2006-01-16
using 
subprocess.call([<executionable>, <arguments>]) works nicely for me

for example, this code would call a program called oggenc which converts audio files to .ogg, in the following manner "oggenc -o moo.ogg moo.wav"
```

import subprocess
subprocess.call( ["oggenc", "-o  moo.ogg", "moo.wav"])

```


more info on the [subprocess module](http://docs.python.org/lib/module-subprocess.html)

---

### Post by Luggy on 2006-01-16
Awesome!
It works like a charm.

Thanks for the help.

---

### Post by briancurtin on 2006-01-16
im sort of new to python, so my method might not be the best way to do it, but it could also be done like this

```
import os
os.system('mencoder -xyz')
```

whatever is in those single quotes, is what you would enter on the command line. you can also pass in variables from your code to set flags or parameters and such

---

### Post by ow50 on 2006-01-17
[QUOTE=briancurtin]im sort of new to python, so my method might not be the best way to do it, but it could also be done like this...[/QUOTE]
Yes, but...
[quote=Python Library Reference]New in version 2.4.

The subprocess module allows you to spawn new processes, connect to their input/output/error pipes, and obtain their return codes. This module intends to replace several other, older modules and functions, such as:

**os.system**
os.spawn*
os.popen*
popen2.*
commands.*
[/quote]
subprocess is newer and more powerful. For some simple purposes os.system might be enough. I  recently used subprocess to start MPlayer so that I can get all output (stderr and stdout) and get the return value on all platforms.
```
popen = subprocess.Popen(
    command,
    stdout=output_file_desc,
    stderr=subprocess.STDOUT,
    shell=True,
    universal_newlines=True,
)
return_value = popen.wait()
```

---

### Post by briancurtin on 2006-01-17
thank you very much for that. my oreilly python book is a bit out of date, so i wasnt aware of that change in 2.4. thanks for the heads up, i will be looking into it

---

