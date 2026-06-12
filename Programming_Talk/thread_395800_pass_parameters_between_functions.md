---
title: "pass parameters between functions"
date: 2007-03-28
forum: Programming Talk
---

### Post by bradleyd on 2007-03-28
Hello everyone,
I am having a problem trying to pass parameters in and out of functions in a wxpython app.
I can get the my functions to pass parameters outside of my wxpython app, but not in the wxpython 
I have bound a button to function GeditOpen.
```
def getPid(self,event):
	child1 = subprocess.Popen(["./gedit"], cwd="/usr/bin")
	bruce = child1.pid
	return bruce
```
I have another button bound to function OnClose:
```
def OnDisc(self,event):
        os.kill(getPid('pid'),15)
        self.Close()
        
```

I get "NameError: global name 'getPid' is not defined"
I do not want to use global variables,as this is bad practice.
any help would be appreciated.
thanks,
Brad

---

### Post by pmasiar on 2007-03-28
are these functions in same source file? In same package/class?

---

### Post by bradleyd on 2007-03-28
I created the app with wxglade, I think they are all under
class MyFrame(wx.Frame):

---

### Post by bradleyd on 2007-03-30
ok fixed call to other function, when it is in the same class you must use self before function. now I got one more problem. I am having trouble passing parameters to functions, for example.
```
#!/usr/bin/env python
import subprocess
import os
import time

def gedit():
	child1 = subprocess.Popen(["./gedit"], cwd="/usr/bin")
	bruce = hpid(child1.pid)
	return bruce
def term():
    child2 = subprocess.Popen(["./gnome-terminal"], cwd="/usr/bin")
    p = hpid(child2.pid)
    return p

def hpid(bruce,p):
	print bruce
	print p
	return bruce
        return p
       
gedit()
term()
time.sleep(3)
os.kill(hpid(''),15)
os.kill(hpid(''),15

```
I am trying to pass the pid to another function, and then when i want to kill those processess in main or another function, I hope that makes sense.

---

### Post by WW on 2007-03-30
The function hpid has two arguments, but in gedit and term, you call hpid with just one argument.

You have two return statements in hpid, one right after the other.  Since the first one will leave the function, the second will never be executed.

---

### Post by bradleyd on 2007-03-30
I put two arguments for hpid because I thought I had to put two to accept the pid's from gedit() and term()
bruce = hpid(child1.pid) does this pass the process id of gedit into function hpid(_**bruce**_,p)
and 
p = hpid(child2.pid) pass the process id of terminal to function hpid(bruce,_**p**_)

I am missing something here. thanks for the response.

---

### Post by WW on 2007-03-30
child1.pid is a single object.  To be clear (but redundant), you could do this:
```

    ....
    x = child1.pid   # x is the PID of child1
    b = hpid(x)     # Do whatever hpid is supposed to do, and save the return value in b
    ....

```
and define hpid as
```

def hpid(p):
    # Do whatever hpid is supposed to do...
    result = ... (whatever it is that hpid is supposed to return)...
    return result

```

---

### Post by bradleyd on 2007-03-30
ok this is what I got from your help:
```
#!/usr/bin/env python
import subprocess
import os
import time

def gedit():
    child1 = subprocess.Popen(["./gedit"], cwd="/usr/bin")
    b = child1.pid
    x = hpid2(b)
    return x

def term():
    child2 = subprocess.Popen(["./gnome-terminal"], cwd="/usr/bin")
    p = child2.pid
    s = hpid(p)    
    return s

def hpid(s):
	print s
	return s
def hpid2(x):
    print x
    return x

term()
gedit()

print hpid('')
print hpid2('')
```
I parsed out hpid to two functions to simplify things.
It know open gedit an terminal and prints the pid's. The trouble starts when I try to add a kill statement for one of the processes like so:
os.kill(hpid('x'),15)
it gives me  TypeError: an interger is required.

thanks again.

---

### Post by WW on 2007-03-30
Could you explain what it is that you think your function hpid is supposed to do?  Currently, all it does is print its argument, and then it returns the same value that it was given.  So this
```
os.kill(hpid('x'),15)
```
is effectively the same as this
```
os.kill('x',15)
```
which means you are passing the string 'x' as the first argument to os.kill().

Perhaps what you really want is simply
```
os.kill(child1.pid,15)
os.kill(child2.pid,15)
```
(I don't know if that will work--I am not familiar with these os functions.)

---

### Post by bradleyd on 2007-03-30
I can use os.kill(child1.pid,15)   if I declare child1 as global variable, but sinse child1 is local to function gedit() I was trying to pass the pid of spawned gedit to a holder function. Function hpid is just suppose to hold the pid's of gedit() and term()
for example let's say gedit() executes and spwans gedit and pass the pid(which is 32296) to function hpid. now hpid is holding 32296 and returns it to main or to another function. Then when ever the os.kill command is called I can pass the pid in hpid() to it, like so
os.kill(32296,15)<-----the 15 is the signal.
If I declared child1 global in function gedit(),like so:
```
global child1
child1 = subprocess.Popen(["./gedit"], cwd="/usr/bin")
child1.pid
```

 I can call os.kill(child1.pid,15) anywhere in the program, but this is what I am trying to avoid.

---

### Post by WW on 2007-03-30
Your hpid function doesn't store anything.  The argument s is also, in effect, a local variable, and once the function returns, s doesn't exist.

Would this outline work?
```

#!/usr/bin/env python
import subprocess
import os
import time

def gedit():
    child1 = subprocess.Popen(["./gedit"], cwd="/usr/bin")
    return child1.pid

def term():
    child2 = subprocess.Popen(["./gnome-terminal"], cwd="/usr/bin")
    return child2.pid

term_pid = term()
gedit_pid = gedit()

# ...do important stuff...

# Now kill gedit and term
os.kill(term_pid,15)
os.kill(gedit_pid,15)

```

---

