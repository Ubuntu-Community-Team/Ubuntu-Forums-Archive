---
title: "Python - Retrieving output from os.system()"
date: 2009-08-31
forum: Programming Talk
---

### Post by Bodsda on 2009-08-31
Hi guys,

I am having a bit of trouble retrieving information output from os.system() calls. To be specific, I am trying to do the following:
```
cwd = os.system("pwd")
```

I was hoping to get the current working directory string that the above command prints out, stored in cwd, instead I get the exit status from the 'pwd' command.

Is there any way to retrieve the data I need, through os.system() or any other type of system call.

Kind regards,
Bodsda

---

### Post by credobyte on 2009-08-31
I'm far away from "I know Python", but .. answer could be found @ [http://mail.python.org/pipermail/python-list/2005-October/343901.html](http://mail.python.org/pipermail/python-list/2005-October/343901.html) ;)

---

### Post by Bodsda on 2009-08-31
> **credobyte said:**
> I'm far away from "I know Python", but .. answer could be found @ [http://mail.python.org/pipermail/python-list/2005-October/343901.html](http://mail.python.org/pipermail/python-list/2005-October/343901.html) ;)

Yeah, I tried using the subprocess module, specifically:
```
cwd = subprocess.call(["pwd"])
```
But I just got the exit status again.

Thanks,
Kind regards,
Bodsda

---

### Post by unutbu on 2009-08-31
Hi Bodsda, how about this:
[PHP]
#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT,call

proc=Popen('pwd', shell=True, stdout=PIPE, )
output=proc.communicate()[0]
print output
[/PHP]

or, in this case,[PHP]

import os
print(os.getcwd())
[/PHP]

PS. The subprocess code I learned from Doug Hellmann's wonderful Python Module of the Week blog: [http://blog.doughellmann.com/2007/07/pymotw-subprocess.html](http://blog.doughellmann.com/2007/07/pymotw-subprocess.html)

---

### Post by Bodsda on 2009-08-31
Hmm, 
```
ouput = os.popen("pwd").readlines()
```
seems to get me a list of the output. Thanks for everyones help.

Kind regards,
Bodsda

---

### Post by Bodsda on 2009-08-31
> **unutbu said:**
> Hi Bodsda, how about this:
[PHP]
#!/usr/bin/env python
from subprocess import Popen,PIPE,STDOUT,call

proc=Popen('pwd', shell=True, stdout=PIPE, )
output=proc.communicate()[0]
print output
[/PHP]

or, in this case,[PHP]

import os
print(os.getcwd())
[/PHP]

PS. The subprocess code I learned from Doug Hellmann's wonderful Python Module of the Week blog: [http://blog.doughellmann.com/2007/07/pymotw-subprocess.html](http://blog.doughellmann.com/2007/07/pymotw-subprocess.html)

Hi unutbu,

Could you explain your first code block please. I'm new to the popen attribute

Thanks,
Kind regards,
Bodsda

---

### Post by unutbu on 2009-08-31
Explanation? Uh-oh...
Here is where I expose my lack of understanding: :)
```

proc=Popen('pwd', shell=True, stdout=PIPE)

```
This makes proc an instance of the Popen class. 
This line, as I understand it, sets up a subshell which runs the 'pwd' command. 
The stdout file handle is directed to PIPE. If you don't do this, then the subshell prints its output to the terminal. By directing it to the PIPE, you can then read what has been sent to the PIPE via the command
```

proc.communicate()
```

proc.communicate() returns a 2-tuple: (stdout, stderr)

So 
```

output=proc.communicate()[0]
```

picks of the stdout, and ignores stderr. 

Hope this helps. I'm sure Doug Hellmann explains it better.

PS. The official documentation on the subprocess module can be found here: [http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

---

### Post by Bodsda on 2009-08-31
> **unutbu said:**
> Explanation? Uh-oh...
Here is where I expose my lack of understanding: :)
```

proc=Popen('pwd', shell=True, stdout=PIPE)

```
This makes proc an instance of the Popen class. 
This line, as I understand it, sets up a subshell which runs the 'pwd' command. 
The stdout file handle is directed to PIPE. If you don't do this, then the subshell prints its output to the terminal. By directing it to the PIPE, you can then read what has been sent to the PIPE via the command
```

proc.communicate()
```

proc.communicate() returns a 2-tuple: (stdout, stderr)

So 
```

output=proc.communicate()[0]
```

picks of the stdout, and ignores stderr. 

Hope this helps. I'm sure Doug Hellmann explains it better.

PS. The official documentation on the subprocess module can be found here: [http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

Brilliant, thanks again unutbu,

Kind regards,
Bodsda

---

### Post by MadMan2k on 2009-08-31
[PHP]
import commands
print commands.getoutput("pwd")
[/PHP]

---

### Post by days_of_ruin on 2009-08-31
```
import os
print os.getcwd()
```

---

### Post by Bodsda on 2009-08-31
> **days_of_ruin said:**
> ```
import os
print os.getcwd()
```

Thanks, this also works

However I was also after a more generic way of doing it for any command.

Thanks for all your help guys

Kind regards,
Bodsda

---

### Post by pepperphd on 2009-08-31
I suppose this is a way to do it. Kind of cheap though.

```

os.system('ls -a &> _temp_')
out_file = open('_temp_', 'r')
out = out_file.read()
out_file.close()
os.remove('_temp_')

```For your specific need:
[FONT=monospace]
```

os.system('pwd &> _temp_')
out_file = open('_temp_' r')
out = out_file.read()
out_file.close()
os.remove('_temp_')
print out

```

You might have to put the full path to _temp_ in os.remove(). I didn't test this.
[/FONT]

---

### Post by spupy on 2009-08-31
> **MadMan2k said:**
> [PHP]
import commands
print commands.getoutput("pwd")
[/PHP]

I don't know what you guys are talking about. This here is the way. It can't be simpler.
You can also get the return status along with the output. Check the documentation of the commands module.

---

