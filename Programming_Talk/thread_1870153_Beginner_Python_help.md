---
title: "Beginner Python help"
date: 2011-10-26
forum: Programming Talk
---

### Post by Diametric on 2011-10-26
Hello,

I just picked up a beginners Python book (the one by Michael Dawson).  I didn't know it at the time, but the book is geared towards MS installs.  I imagine for the most part, I'll be fine, but are there any gotchas I need to look out for when running python code on Linux?

For example - I was following along in a lesson teaching escaping characters:

```
print("\t\t\tFancy Credits")

print("\t\t\t \\ \\ \\ \\ \\ \\ \\")
print("\t\t\t\tby")
print("\t\t\tDylan")
print("\t\t\t \\ \\ \\ \\ \\ \\ \\")

print("nSpecial thanks go to:")
print("My homeboy, Henry \'The Great,\' who never says \"can\'t.\"")

#sound the system bell
print("\a")

input("\n\nPress the Enter key to exit.")
```

When I tried to source the file, it didn't run.  After searching online I fond that it I type:

```
python mypythonscript.py
```

from bash, it runs as expected.  So, are there any others I should be aware of/

Thank you so much!

---

### Post by cgroza on 2011-10-26
What do you mean by "source the file" ?

---

### Post by Diametric on 2011-10-26
from my python directory, I attempted to "source" the file like a .sh file:

```
source myfile.py
```

That gave me an error.  I then found out, I need to execute a .py file as:

```
python myfile.py
```

The book is a MS book on Python, so all a MS user has to do is double click on the file and it runs...leaving me to figure out how to do it on Linux.  Thus my question - what else should I look out for (if anything)?

---

### Post by oldfred on 2011-10-27
Windows works of extensions and does not have permissions or ownership.

Linux knows file type by data in file usually.

So in python you want to add this as the first one or two lines. If you use python is runs the default 2.6 or 2.7 if you use python3 it will run the default version of 3 your have installed. I find most of the few simple programs I am running work the same under python or python3 with the main exception of print statements. Of course more advanced commands may run into the other differences.

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# [queryTest.py]

or:
#!/usr/bin/python3

I always include the coding line & a file name line as I has a crash and had to use photorec to recover files. Without a filename it was a mess to tell what was what.

You also can make the file executeable and then you can just run it.

---

### Post by Diametric on 2011-10-27
Ah - that makes some sense.  Is there a site that elaborates on that any, that I could review?

Specifically, I went back to a few of the practice scripts and added the "#!/bin/python3" as the first line (i am running python 3.1 - the one from our repos) and it didn't seem to change the behavior.  For example:

```
#!/usr/bin/python3

name = "Dylan"

print(name)

print("Hi,", name)

input("\n\nPunch \"Enter\" please.")
```

Still throws the following error when attempting to run from bash after adding the line you suggest *and* chmoding the file:

```
Traceback (most recent call last):
  File "variable1.py", line 12, in <module>
    input("\n\nPunch \"Enter\" bitch...please.")
  File "<string>", line 0
    
    ^
SyntaxError: unexpected EOF while parsing
```

---

### Post by Smart Viking on 2011-10-27
> **Diametric said:**
> Ah - that makes some sense.  Is there a site that elaborates on that any, that I could review?

Specifically, I went back to a few of the practice scripts and added the "#!/bin/python3" as the first line (i am running python 3.1 - the one from our repos) and it didn't seem to change the behavior.  For example:

```
#!/usr/bin/python3

name = "Dylan"

print(name)

print("Hi,", name)

input("\n\nPunch \"Enter\" please.")
```Still throws the following error when attempting to run from bash after adding the line you suggest *and* chmoding the file:

```
Traceback (most recent call last):
  File "variable1.py", line 12, in <module>
    input("\n\nPunch \"Enter\" bitch...please.")
  File "<string>", line 0
    
    ^
SyntaxError: unexpected EOF while parsing
```
That's because you're still running it with python 2.x.

When you have put in the shebang ("#!/usr/bin/python3") and made the file executable ("chmod +x file.py"), you run it like this: 
```
./file.py
```
Or simply type out the full path of the file, does the same thing.

When you run it with "python file.py", it will ignore the first line and think that it's a comment, because you're telling python to run this script. But if you run it like a program, then the system will look at the file, trying to understand how to run it, and the system does understand the shebang.

---

