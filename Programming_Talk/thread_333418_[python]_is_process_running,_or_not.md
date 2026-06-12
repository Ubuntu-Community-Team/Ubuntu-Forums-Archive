---
title: "[python] is process running, or not?"
date: 2007-01-07
forum: Programming Talk
---

### Post by lazka on 2007-01-07
how do i get the information if e.g. apache is running?

atm i do this:

```
def check_apache( *args ):
	process = os.popen("ps x | grep apache").read().splitlines()
	if len(process) > 2:
		return 1
	else:
		return 0
```

2. question: how do I get the path of the python script itself?
i always have to start it in the folder to get pictures

---

### Post by gpolo on 2007-01-07
answer to question 2: what you want is the current working directory:

import os

print os.getcwd()

answer to question 1: there are lots of ways, do what works for you

---

### Post by lazka on 2007-01-07
sry but thats not what i wanted
it always returns my home-directory path

---

### Post by Tomosaur on 2007-01-07
current directory checking only works on where the user currently is, not the python script. You probably need to set an environmental variable to tell the script where it is.

---

### Post by gpolo on 2007-01-07
I'm sorry but I can't understand then, you arent asking a python question but a shell question ?

---

### Post by M7S on 2007-01-07
What about
```
os.path.abspath(os.path.dirname(sys.argv[0]))
```

---

### Post by ghostdog74 on 2007-01-07
> **lazka said:**
> how do i get the information if e.g. apache is running?

atm i do this:

```
def check_apache( *args ):
	process = os.popen("ps x | grep apache").read().splitlines()
	if len(process) > 2:
		return 1
	else:
		return 0
```

2. question: how do I get the path of the python script itself?
i always have to start it in the folder to get pictures


1.just one way :
```

process = os.popen("ps x -o pid,args | grep apache").read() #sometimes have to use grep -v grep
if process:
   print "apache running"

```

---

