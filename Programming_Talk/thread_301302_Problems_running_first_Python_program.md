---
title: "Problems running first Python program"
date: 2006-11-16
forum: Programming Talk
---

### Post by FleetAdmiral74 on 2006-11-16
I did not think it was possible to mess up the first program following instructions, but I managed to.

Here are instructions I followed:
Start your editor, type the following program and save it as helloworld.py.

print 'Hello World'

Run this program by opening a shell prompt and run the command python helloworld.py. If you are using PythonWin, use the menu File &#8594; Run.

The output is as shown below:

$ python helloworld.py
Hello World

I get an error when I run the command in terminal...

NOTE- Edited error message, pasted wrong

>>> python helloworld.py
  File "<stdin>", line 1
    python helloworld.py
                    ^
SyntaxError: invalid syntax

EDIT- The carrot appears in terminal pointing to the d, but in the thread it does not seem to get spacing right

I have the file saved as helloworld.py on the desktop, and have no idea why this will not work....

Just entering "print 'hello world'" works fine in terminal

---

### Post by Joe_CoT on 2006-11-16
```

joe@necromancer:~$ cat helloworld.py
print 'Hello World'
joe@necromancer:~$ python helloworld.py 
Hello World
```

No such issue here....

---

### Post by FleetAdmiral74 on 2006-11-16
I get 

fleetadmiral@Central-Plexus:~$ python helloworld.py
python: can't open file 'helloworld.py': [Errno 2] No such file or directory
fleetadmiral@Central-Plexus:~$ 


Thats when I did not already type in python ( the stuff you pasted shows you did not). Am I supposed to save the files to some default dir its not telling me about?

---

### Post by user1397 on 2006-11-16
cause you typed "python helloworld.py" while already **in** python.  you were already running python inside a terminal, as denoted by the >>>

so make sure it looks like **$** python helloworld.py and not >>> python helloworld.py

where did you save your .py file?  if it is not in your home folder, you have to cd to the correct folder.

---

### Post by FleetAdmiral74 on 2006-11-16
I saved it to me desktop :)

Trying home folder now...

It worked. Thank you for your time.

---

### Post by user1397 on 2006-11-17
> **FleetAdmiral74 said:**
> I saved it to me desktop :)

Trying home folder now...

It worked. Thank you for your time.no prob.

---

