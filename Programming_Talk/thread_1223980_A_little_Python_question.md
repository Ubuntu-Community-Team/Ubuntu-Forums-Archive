---
title: "A little Python question"
date: 2009-07-26
forum: Programming Talk
---

### Post by C++buntu on 2009-07-26
Hi everyone,

I'm using IPython on Windows to learn a little Python.
I want to use the os module to be able to change the working directory...

```

import os
os.chdir(r'C:\Documents and Settings\My name\My Documents\Scientific Python\')
---------------------------------------------------
File "<ipython console>, line 1
  os.chdir(r'C:\Documents and Settings\My name\My Documents\Scientific Python\')
                             little cap here

```

What i'm doing wrong?

Thanks

---

### Post by shadylookin on 2009-07-26
not sure with python but some languages uses \ as an escape character so when you want to use \ you have to use \\

for instance 

C:\Stuff\more stuff\

needs to be written as 

C:\\Stuff\\more stuff\\

could be wrong about this haven't used python in a long time

---

### Post by slavik on 2009-07-26
use raw string?

---

### Post by lavinog on 2009-07-26
> **shadylookin said:**
> not sure with python but some languages uses \ as an escape character so when you want to use \ you have to use \\

for instance 

C:\Stuff\more stuff\

needs to be written as 

C:\\Stuff\\more stuff\\

could be wrong about this haven't used python in a long time

the r at the beginning of the string is for a raw string with no escaping.

@C++buntu: Windows will not let you cd to a directory with spaces without using quotes.
try
```

os.chdir(r'"c:\Documents and Settings\My name\My Documents\Scientific Python\"')

```

---

### Post by days_of_ruin on 2009-07-26
Some good info here: [http://bytes.com/topic/python/answers/722075-windows-xp-os-chdir-path-problem]("http://bytes.com/topic/python/answers/722075-windows-xp-os-chdir-path-problem")

---

### Post by Can+~ on 2009-07-26
I remember reading that Windows accepts forward slashes also. Long time without using windows though.

But yeah, "raw string" is the easiest way to go.

---

