---
title: "[SOLVED] how to get linux command out outs in to a python script"
date: 2008-05-27
forum: Programming Talk
---

### Post by brijith on 2008-05-27
Hai,

           When I write scripts in python I use ***os.system()*** for executing linux commands . My doubt is, is there any method to get the output of the command in side the python script. What I usually do is redirect the out of the linux command in to a file and then read that file in side python script. Can any one suggest any other good method ?


***[COLOR="Red"]Thanks[/COLOR]***

---

### Post by ghostdog74 on 2008-05-27
> **brijith said:**
> Hai,

           When I write scripts in python I use ***os.system()*** for executing linux commands . My doubt is, is there any method to get the output of the command in side the python script. What I usually do is redirect the out of the linux command in to a file and then read that file in side python script. Can any one suggest any other good method ?


***[COLOR="Red"]Thanks[/COLOR]***

what linux commands are you executing?

---

### Post by brijith on 2008-05-27
> **ghostdog74 said:**
> what linux commands are you executing?

Let me explain my current requirement. I have to check super user privilege inside a python script. In the case of bash we can use ***id -ur*** or ***whoami*** to check the privilege. So if I am going to use any of these two in side a python script as ***os.system('id -ur')*** or ***os.system('whoami')*** I have to get the out put of these commands inside a python script. That is what I asked in the previous mail

***[COLOR="Red"]Thanks[/COLOR]***

---

### Post by Lau_of_DK on 2008-05-27
> **brijith said:**
> Let me explain my current requirement. I have to check super user privilege inside a python script. In the case of bash we can use ***id -ur*** or ***whoami*** to check the privilege. So if I am going to use any of these two in side a python script as ***os.system('id -ur')*** or ***os.system('whoami')*** I have to get the out put of these commands inside a python script. That is what I asked in the previous mail

***[COLOR="Red"]Thanks[/COLOR]***

Hey Brijith,

Like in C you can redirect the standard output io in Python. If I remember correctly its something like this

[php]
import sys, StringIO

mystdout = StringIO.StringIO()
sys.stdout = mystdout

os.system("ls")
stroutput = mystdout.getvalue()

sys.stdout = sys.__stdout__
print mystdout
[/php]

Hope it flies,
/Lau :)

---

### Post by brijith on 2008-05-27
> **Lau_of_DK said:**
> Hey Brijith,

Like in C you can redirect the standard output io in Python. If I remember correctly its something like this

[php]
import sys, StringIO

mystdout = StringIO.StringIO()
sys.stdout = mystdout

os.system("ls")
stroutput = mystdout.getvalue()

sys.stdout = sys.__stdout__
print mystdout
[/php]

Hope it flies,
/Lau :)


I tried the code :


```
#!/usr/bin/env python
import sys, StringIO
import os

mystdout = StringIO.StringIO()
sys.stdout = mystdout

os.system("ls")
stroutput = mystdout.getvalue()
sys.stdout = sys.__stdout__

print 'mystdout  :', mystdout  # this is an istance of StringIO.StringIO, right ?
print 'stroutput :', stroutput # I think this variable contains the value

```

but the result is as shown below:

```
~/Desktop? python strio.py
12.tar.gz  abc.txt  CBQ data  Deskop  HOWTO  new  new file~  qwe  smtptest.py  strio.py  tools
mystdout  : <StringIO.StringIO instance at 0xb7d9ed6c>
stroutput :
~/Desktop?

```

The variable ***stroutput*** is empty



***[COLOR="Red"]THANKS[/COLOR]***

---

### Post by dtmilano on 2008-05-27
However, os.getuid() maybe what you are looking for.

---

### Post by brijith on 2008-05-27
> **dtmilano said:**
> However, os.getuid() maybe what you are looking for.

Oky Thanks..


why the code didn't worked. if we could get the output of a bash in side a python it will be a great help.

Any why, thanks for ***os.getuid()*** 

:)

---

### Post by Lau_of_DK on 2008-05-27
> **brijith said:**
> Oky Thanks..


why the code didn't worked. if we could get the output of a bash in side a python it will be a great help.

Any why, thanks for ***os.getuid()*** 

:)

Hi again,

I'm sorry for posting code that flunked. I've tried on my own box and it gives the same result. The only explanation I can think of, is that os.system() does not print to sys.stdout. Maybe you can find a way to determine where it prints and the reroute it?

Another way to do it, which was posted on this forum earlier is:
```

>>> import os
>>> p = os.popen('ls')
>>> s = p.readline()
>>> p.close()
>>> print s
'direct rendering: Yes\n'
>>>

```


This should work? :)
Lau

[tested myself: it does work. Repeat readline until end of stream]

---

### Post by brijith on 2008-05-27
Thanks, this time it worked.

now I am getting the output in side python script. What about the error. if error occures it is coming in terminal but noting in ***p.readlines()***. can we get the error message in side python script

Many Thanks

---

### Post by Lau_of_DK on 2008-05-27
> **brijith said:**
> Thanks, this time it worked.

now I am getting the output in side python script. What about the error. if error occures it is coming in terminal but noting in ***p.readlines()***. can we get the error message in side python script

Many Thanks

I think if I were you, I'd look up the documentation on os. and sys. You might be able to solve this be redirecting sys.stderr like we tried with stdout, but its juts a guess :)

/Lau

---

### Post by brijith on 2008-05-27
> **Lau_of_DK said:**
> You might be able to solve this be redirecting sys.stderr like we tried with stdout, but its juts a guess :)
/Lau
Yes I am trying each of ***os.*** and ***sys.*** entries It is very interesting 

But when we tried sys.stdout it failed in what we needed. I think it will be the same for sys.stderr.

Oky Let me find out it.....   :)

**[COLOR="Red"]Thanks for clearing my doubts   [/COLOR]**

---

### Post by dtmilano on 2008-05-27
Use (not tested, sorry):
> 
p = subprocess.Popen("id -u", stdout=PIPE)
p.stdout.readline()


---

### Post by strider1551 on 2008-05-27
> Can any one suggest any other good method ?

I usually just use the commands module

```

import commands
output = commands.getoutput("ls")
print output

```

---

### Post by RainCT on 2008-05-27
I think subprocess.Popen is the best option (in terms of security). Below you have an example function which wrapps around it to make it more usable, so that you can look at it to see different ways of how you can use it (for example function allows stdout only, stderr only and both mixed together in order of appearance) or just feel free to use it directly.

[php]
    def _get_output(self, command, stdout = True, stderr = False):
        """
        Run the program specified in the first argument and return its output
        as a string.
        """
        if (stdout or stderr) and not (stdout and stderr):
            pipe = subprocess.Popen(command, shell=True, stdout=subprocess.PIPE,
                                    stderr=subprocess.PIPE)
            if stdout:
            	return pipe.stdout.read()
            else:
            	return pipe.stderr.read()
        elif stdout and stderr:
        	return subprocess.Popen(command, shell=True, stdout=subprocess.PIPE,
                                    stderr=subprocess.STDOUT).stdout().read()
        else:
            try:
                return bool(subprocess.Popen(command))
            except OSError:
                print 'Error, could not execute the process.'
                return None
[/php]

---

### Post by RainCT on 2008-05-27
[Oops. Double post]

---

### Post by pointone on 2008-05-27
No need to reinvent wheels here...

```
import os
cmd_stdin, cmd_stdout, cmd_stderr = os.popen3("ls")
cmd_stdout.read()
```

```
import os
cmd_stdin, cmd_stdout, cmd_stderr = os.popen3("ls /non-existant_directory")
cmd_stdout.read() #returns nothing
cmd_stderr.read() #oh... there was an error!
```

[More information...]("http://docs.python.org/lib/os-newstreams.html")

---

