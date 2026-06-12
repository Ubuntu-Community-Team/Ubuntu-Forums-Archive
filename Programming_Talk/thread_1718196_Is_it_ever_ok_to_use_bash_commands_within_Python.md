---
title: "Is it ever ok to use bash commands within Python?"
date: 2011-03-31
forum: Programming Talk
---

### Post by kevin11951 on 2011-03-31
I have been told by a lot of people that you should never use bash commands (ls/halt/etc...) from within Python, because it defeated the purpose.

The thing is that there are a lot of bash commands that will get the job done easier and quicker when used with Python's syntax.

For example:

[PHP]#!/usr/bin/env python

from sys import argv
from subprocess import Popen
from time import sleep

usage = 'Usage: watchfile [-h] file1 [file2] [...]'
args = argv

while True:
	if len(args[1:]) > 0:
		
		if args[1] == '-h':
			print usage
			break
		
		Popen(['clear'])
		
		for i in args[1:]:
			Popen(['du', '-h', str(i)])
	
	else:
		print usage
		exit(1)

	try:
		sleep(1)
	
	except:
		exit()
[/PHP]

This program will take any number of files as an input, and will watch them, printing their sizes to the screen once per second.  I wrote that for when I (often) make blank files using "dd" and what to know how far it has gotten.

---

### Post by DaithiF on 2011-03-31
absolute rules like 'never do x' are usually generalisations  ... really they're saying in the majority of cases doing x isn't a good idea and if you find yourself doing x then please think again for a better way.  There may be exceptions though ... and if in a specific situation doing x is the most efficient way to do something then ignoring the rule is just fine.

In your specific case i would actually question the need for the python script, rather than the need for bash in the python script :)

since you can do this just using bash like so:
```
watch -n 1 du -h file1 file2
```

---

### Post by kurum! on 2011-03-31
> **kevin11951 said:**
> 
The thing is that there are a lot of bash commands that will get the job done easier and quicker when used with Python's syntax.

then you should use Bash and not Python.

---

### Post by MadCow108 on 2011-03-31
there is nothing wrong with it when the solution is appropriate.
For simple scripts I mostly prefer to use python + subprocess nowadays.
some people even use python as a system shell (look at ipython)

the drawback of this approach is that it is dependent on the output of programs not under direct control, when they change your program needs adapting. But the same is often true for shell scripts.
And it can slightly slower due to the extra forking but also faster due to C implementation of the tools.

In your case a python only solution is just as simple, so it would be preferable.

---

### Post by nvteighen on 2011-03-31
The best is to understand what is said.

The biggest problem of the system() call is that it doesn't allow you to interact with what you're calling. It opens a new shell, it fires a process and meanwhile, your program can't do anything to communicate with that subprocess. So, e.g. if you wanted to modify the way a directories are sorted, in some way ls doesn't provide, you'll be lost. The only feedback you get from a system() call is the program's exit code.

That's why, the rule of thumb is to start looking for libraries that do the same work. Doing this makes the desired functionality be part of your program and, if the library is well-designed, it will give you much more control and it will also be more efficient (you won't be calling two programs via an intermediate shell, plus Python... just your program and Python). But it's not that much about efficiency: it's also about the possibilities of abstraction and much better interaction.

When a library doesn't exist, the second resort most people try is to connect to the program using a POSIX pipe (the popen function). It doesn't allow abstraction, but allows for I/O communication between the processes. Other programs use a server-client model (setting up a server in localhost) that has the same effect while allowing some more flexibility on the data type.

Then there are other issues to take in account and that make system() a quite ugly thing to use. A quite easy mistake to do is to call system() using a string that originates from user input... I hope you realize this can be a huge security vulnerability if you haven't provided means for input sanitization. Another issue is that using system() (or popen()) is very likely to break cross-portability, while the Python core libraries won't (or at least, shouldn't... and if you find that isn't portable despite the specs, file a bug against it immediately).

---

