---
title: "Python as everyday command line shell?"
date: 2006-05-22
forum: Programming Talk
---

### Post by Kvark on 2006-05-22
Is it possible to replace or combine Bash with Python? How?

You may be wondering why. Well, becuase Python can do things like...
```
>>> 5**3 - 150 / 4
88
>>> from math import *
>>> sin(radians(270))
-1.0
```

But the problem is that typing the names of executables such as ls, cd, mv, sudo and apt-get doesn't work in Python...
```
>>> ls
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'ls' is not defined
>>> sudo apt-get update
  File "<stdin>", line 1
    sudo apt-get update
           ^
SyntaxError: invalid syntax
```

I know that the program "qalc" can be used to do math in bash and there are other more powerful shells besides Bash but there are many situations other then math where I'd want to type Python code in the command line.

I also know that after "from os import *" you can do "system('sudo apt-get update')" in Python and that is exactly what I want to do but wrapping every command in "system('command')" is too cumbersome.

---

### Post by glinsvad on 2006-05-22
In Python your options are:
```

>>> import os
>>> os.system('ls')
>>> os.spawnl(mode, file, *args) 

```

Otherwise turn to pexpect, which is a Python-module for bash-interaction

---

### Post by Kvark on 2006-05-22
[QUOTE=glinsvad]In Python type:
```

>>> import os
>>> os.system('ls')

```[/QUOTE]
Yes that is exactly what I want to do. But almost everything one types in a shell is names of and arguments to executables. So that solution would mean typing os.system('') on almost every single line which would be too triesome. Is there any way to type the name of executables directly like in Bash?

---

### Post by tigrux on 2006-05-22
Try ipython.

It is a more interactive shell for python, and with bash-like features.

---

### Post by Kvark on 2006-05-22
[QUOTE=tigrux]Try ipython.

It is a more interactive shell for python, and with bash-like features.[/QUOTE]
Yeah, ipython is nicer then python's own interactive shell. But even ipython doesn't seem to like being used as a command line...
```
In [1]: sudo apt-get update
------------------------------------------------------------
   File "<console>", line 1
     sudo apt-get update
            ^
SyntaxError: invalid syntax
```

---

### Post by glinsvad on 2006-05-22
Hmm, maybe piping stdout from Python into stdin for sh...

Only way to do this directly is by pexpect (as mentioned above)

Otherwise, redirect stdout from Python into a file and then execute it:
```

import sys
import os
# Store the old stdout
old_stdout = sys.stdout

# Set a new one
sys.stdout = file(filename,mode)

# Print commands to file
print '#!/usr/bin/env sh'
print '<your commands here>'

# Close the file
sys.stdout.close()

# Restore stdout
sys.stdout = old_stdout

# Now run the script
os.system("sh %s" % filename)

```

You still have to type "print" in front of every command though :/

---

### Post by glinsvad on 2006-05-22
Wait a second... I just had a thought (surprise!)

Create a bogus class with nothing but a __getattr__ that executes whatever key is passed to it:
```

>>> import os
>>> class T:
...     def __init__(self):
...             pass
...     def __getattr__(self,k):
...             os.system(k)
...
>>> t=T()
>>> t.ls

```

Tadaa!

---

### Post by Steveire on 2006-05-22
[QUOTE=glinsvad]Wait a second... I just had a thought (surprise!)

Create a bogus class with nothing but a __getattr__ that executes whatever key is passed to it:
```

>>> import os
>>> class T:
...     def __init__(self):
...             pass
...     def __getattr__(self,k):
...             os.system(k)
...
>>> t=T()
>>> t.ls

```

Tadaa![/QUOTE]
An hour ago I thought of that. But I had to go and watch Lost, so didn't get the chance for glory.

*shakey fist*

---

### Post by Kvark on 2006-05-22
[QUOTE=glinsvad]Wait a second... I just had a thought (surprise!)

Create a bogus class with nothing but a __getattr__ that executes whatever key is passed to it:
```

>>> import os
>>> class T:
...     def __init__(self):
...             pass
...     def __getattr__(self,k):
...             os.system(k)
...
>>> t=T()
>>> t.ls

```

Tadaa![/QUOTE]
Thats a pretty clever trick. But there seems to be a "but" with every idea here...
```
>>> t.ls -l
<a lot of files in normal format, not long as it should be>
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
NameError: name 'l' is not defined
```
...looks like it tried to calculate the result of t.ls minus l. "t.nano file.txt" and "t.sudo apt-get install some-package" doesn't work either.

---

### Post by glinsvad on 2006-05-22
Eeeh, I guess this trick its really not so much a trick again. Problem is the __getattr__ takes the name of a variable, and the names of variables is limited to consisting of A-Z, a-z, 0-9 and _.

Well this is getting stupid, but I persist as usual. You'll have to reform all your commands into only using valid variables names. I do this using "_code" where code is the ASCII number (i think?) corresponding to that character...
```

import re
import os

replace = {'_40': ' ', '_41':'!', '_42':'"', '_43':'#', '_44':'$', '_45':'%', '_46':'&', '_50':'(', '_51':')', '_52':'*', '_53':'+', '_54':',', '_55':'-', '_56':'.', '_57':'/'}

class T:
   def __init__(self):
      pass
   def __getattr__(self,k):
      for (subs, repl) in replace.items():
         k = re.sub(subs, repl,k)
      os.system(k)

t=T()
t.ls_40_55l

```

Moral: Make it easy on yourself only if it is truly easier!

---

### Post by glinsvad on 2006-05-22
```

from os import system as s

s('ls -l')

```

Is this really that much of a bother?

---

### Post by Corvillus on 2006-05-23
Just use a multi-line string
```

import os
script = '''
ls -l
echo "hello, world!"
# whatever shell commands
'''
os.system(script)

```

---

### Post by Kvark on 2006-05-23
Thanks for all the ideas on easy ways to do it. I guess it can't get easier then s('...') or racking up a long row of commands with ''''...'''. When using it all the time instead of bash I think even s('') becomes too much of an addition to every command, specially since ( and ) both requires shift. Guess I'll write a script that checks if the first word in each line of input is the name of an executable and if so does "os.system(user_input)" else does "exec user_input".

---

### Post by glinsvad on 2006-05-24
Using an interpreter before passing script to Python is not a bad idea. Easies way is to prefix all bash-commands in your Python-script by something like ## (lets call this script file.py):
```

from os import system as s

print "About to run some command-line stuff..."
print "---------------------------------------"

##echo "Hello $USER, ready to install somethingfunny?"
##sudo apt-get install somethingfunny

print "---------------------------------------"
print "Done"

```

Now a simple sed-script will do the trick. Save this code as convert.sed and make it executable:
```

#!/bin/sed -rf
s%^[ \t]*##(.+)[ \t]*$%s('\1')%g

```

Now to execute your Python-script in terminal:
```

./convert.sed file.py | python

```

I dare anyone to make execution easier that this :D

EDIT: Don't worry, there's no such package as somethingfunny (sadly)

---

### Post by DirtDawg on 2006-05-24
If you felt like taking the time, you could write your own, simple shell with the Cmd module? 

```


## Not correct code, but I'm not next to documentation at the moment ##

import cmd
import os

class Shell(cmd.Cmd):
    def __init__(self):
        __init__(cmd.Cmd)
        self.prompt= "$: "

def do_ls (self):
    os.system('ls')

def do_echo(self, string):
    print string

## So on and so forth ##

if __name__ == '__main__':
    shell= cmd.Cmd()
    shell.start() ## Again, I cannot remember the correct code here ##


```

Actually, now that I look at it, using this method you may not be able to escape the loop to run regular mathmatics, etc. Hmm. Well, it's a thought anyways.

---

### Post by Van_Gogh on 2006-05-25
Noone suggested Pysh yet...:-|

---

### Post by Wolki on 2006-05-25
hm, have you considered just using python in your bash scripts or the bash instead of using shell commands in python? you can pipe code into python and it will evaluate it, like ```
echo -e "print 5**3 - 150 / 4\nfrom math import *\nprint sin(radians(270))" | python 
```. Of course, if you're doing heavy python, this will become messy very quickly, otoh I find managing pipes much less of a hassle in the bash.

---

### Post by DAFORZE on 2006-05-25
Ah so Van_Gogh has the right answer. ;)  
thx

---

### Post by dabear on 2006-05-25
I presume the pysh project is dead. Front page is last updated 4 years ago, no official downloads are available, and the project is still in the alpha stage!

---

### Post by Kvark on 2006-05-26
[QUOTE=Van_Gogh]Noone suggested Pysh yet...:-|[/QUOTE]
That looks exactly like what I want. Unfortunately it seems to have died long before becoming complete. It's site mentions another project called [Pyshell]("http://pyshell.sourceforge.net/") which seems much more complete, I'll have to try that.

---

### Post by Van_Gogh on 2006-05-26
Hmm, ok. I don't actually use pysh myself, it just gets bundled with the Windows version of ipython(THE interactive Python interpreter IMO). Pyshell does indeed look more mature.

---

