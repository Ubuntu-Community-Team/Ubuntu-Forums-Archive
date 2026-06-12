---
title: "How do you call a program from python"
date: 2012-03-06
forum: Programming Talk
---

### Post by brushman on 2012-03-06
Say I have a program that simply runs by just entering ./program. Except now I want to call it from a python script. What's the easiest way to do this? Is there some simple command I can use, like 'call program' or something?

Thanks.

---

### Post by r-senior on 2012-03-06
You can use os.system:

```
import os

os.system('./program')

```

---

### Post by ve4cib on 2012-03-06
> **brushman said:**
> Say I have a program that simply runs by just entering ./program. Except now I want to call it from a python script. What's the easiest way to do this? Is there some simple command I can use, like 'call program' or something?

Thanks.

You can also use:

```

import subprocess

client = subprocess.Popen("/command/to/execute")

```

The subprocess module lets you do all sorts of useful things with programs you want to execute.  For example, if your program asks the user for input you can easily communicate with the program:

**myProgram**
```

#!/usr/bin/python

val = raw_input("Enter a number")
val = int(val)
print 'You entered',val

print val,"squared is",val**2

```

**Program that calls "myProgram"**
```

#!/usr/bin/python

import subprocess

client = subprocess.Popen("./myProgram", stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE)

# write a number to myProgram to read in
client.stdin.write("10\n")
client.stdin.flush()          # flush stdin to ensure that the data is not buffered

# read the output from the program
client.stdout.flush()
result = client.stdout.readlines()[-1] # we only care about the last line
print 'Got result from myProgram:'
print result

```

---

