---
title: "Python vs. BASH/Perl/PHP -- backticks"
date: 2007-12-30
forum: Programming Talk
---

### Post by altonbr on 2007-12-30
In BASH/Perl/PHP I can run a command like so:
```
#BASH
USER=`whoami`
#Perl/PHP
$user = `whoami`; # or...
$user = shell_exec('whoami');
```

How do I load a variable in Python by running a shell command?

I read that this is the only way:
```
import os
user = os.popen('whoami').read()
```

Is that true?

I guess the whole purpose is that python is cross-platform and should try not to rely on shell commands, am I correct?

---

### Post by Majorix on 2007-12-30
Have you already read the library manual for the os module on Python's official docs? They are a good source when it comes to stuff like this.

---

### Post by ghostdog74 on 2007-12-30
> **altonbr said:**
> 
I read that this is the only way:
```
import os
user = os.popen('whoami').read()
```

Is that true?

of course not. Read the docs, esp the section called Process Management in the library reference.
> 
I guess the whole purpose is that python is cross-platform and should try not to rely on shell commands, am I correct?

yes, but Python is not everything. Sometimes, we really do need to call shell commands.

---

### Post by rolando2424 on 2007-12-31
There is the os.system() function, that allows you to run the commands in a subshell, but it only returns the exit code (0 if all went well, other numbers if there was an error).

What I usually do is a redirect the output of the command to a file and then open it in python.

Example:

[code=Python]
#!/usr/bin/env python
import os

os.system("cat file > output.txt")

content = file("output.txt", "r").readlines()
[/code]

---

### Post by ghostdog74 on 2007-12-31
> **rolando2424 said:**
> 
os.system("cat file > output.txt")
[/code]

I hope this is just an example, and not what you normally do every time.

---

### Post by Wybiral on 2007-12-31
> **rolando2424 said:**
> There is the os.system() function, that allows you to run the commands in a subshell, but it only returns the exit code (0 if all went well, other numbers if there was an error).

Do some research on pipes. The subprocess module offers some really easy routines for handling pipes and processes.

```

import subprocess as sp
proc = sp.Popen("bc", shell=True, stdout=sp.PIPE, stdin=sp.PIPE)
proc.stdin.write("10+2 \n 5*5 \n quit \n")
print proc.communicate()[0]

```

---

### Post by rolando2424 on 2008-01-02
> **ghostdog74 said:**
> I hope this is just an example, and not what you normally do every time.

Sometimes I think it's easier to just do os.system("cat onlineInvoice.aspx.html | grep KB | sed 's/internet.vodafone.pt//g' | sed 's/\t/ /g' > output.txt") (taken from a script I wrote a few days ago) and then process the output.txt file in python, instead of writing the code to cat, grep and sed.

Isn't it the Unix way (I think)? To write one program that does one thing well, and then mixing them with redirects, pipes, etc. to make your program.

---

### Post by ghostdog74 on 2008-01-02
> **rolando2424 said:**
> Sometimes I think it's easier to just do os.system("cat onlineInvoice.aspx.html | | sed 's/internet.vodafone.pt//g' | sed 's/\t/ /g' > output.txt") (taken from a script I wrote a few days ago) and then process the output.txt file in python, instead of writing the code to cat, grep and sed.

Noooooooo.... you can do that purely in Python.. who taught you that? If you want to do that , you might as well use shell programming. 
```
 cat onlineInvoice.aspx.html 
```
is equivalent to
```

for line in open("onlineInvoice.aspx.html"):
  ....

```
or 
```

data = open("onlineInvoice.aspx.html").read()

```
> 
```

 grep KB

```

This is the same as :
```

...
if "KB" in line :
...

```
> 
```

 sed 's/internet.vodafone.pt//g' | sed 's/\t/ /g' 

```

This practically says to substitute "internet.vodafone.pt" with a blank and then substitute tabs with space.  therefore the Python equivalent might be
```

...
line.replace("internet.vodafone.pt","").replace("\t","") #not tested 
...

```
And I am sure  for "> output.txt", you know what to do in Python.

> 
Isn't it the Unix way (I think)? To write one program that does one thing well, and then mixing them with redirects, pipes, etc. to make your program.
No..definitely not. Mixing too many redirects and pipes makes your code not easy to read and prone to errors. Just the right amount to do the job right will do. For the record, this
```

cat onlineInvoice.aspx.html | | sed 's/internet.vodafone.pt//g' | sed 's/\t/ /g' 

```
is useless use of cat and pipes. Here's one way it can be done more "nicely"
```

# tr -s ' ' < onlineInvoice.aspx.html | sed 's/internet.vodafone.pt//g' > output.txt
```

---

### Post by ozgurk on 2009-08-05
I am trying to learn Python and not sure  for the equivalent of "> output.txt" usage..
Is there a way in Python that bypasses the need for output.txt? Can the output be redirected to an array internally?

---

### Post by tom66 on 2009-08-05
This writes to a file called output.txt.

```

f = open("output.txt", "w")
f.write("text to write\n")
f.close()

```

---

### Post by slavik on 2009-08-05
here's a nice Perl example:
```

open CMD, "|somecommand|command2|" or die $!;
print CMD "here is data to compute"
while ($result = <CMD>) {
  print "Result is" . $result . "\n";
  print CMD "here is more data";
}

```

or you can split the above into two threads that truly run concurrently. :)

---

### Post by ozgurk on 2009-08-06
Thanks :)

---

