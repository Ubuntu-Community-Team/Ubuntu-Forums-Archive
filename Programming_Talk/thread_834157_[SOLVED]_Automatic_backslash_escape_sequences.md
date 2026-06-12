---
title: "[SOLVED] Automatic backslash escape sequences?"
date: 2008-06-19
forum: Programming Talk
---

### Post by Jadd on 2008-06-19
When coding in python, I frequently write lines similar to these:
[php]import subprocess
# filename is a previously assigned string variable
subprocess.call("mkdir -p %s" % filename, shell=True)
[/php]
This works great, until the filename contains special characters, such as a space. A solution would be:
[php]subprocess.call("mkdir -p %s" % filename.replace(" ", "\\ "), shell=True)[/php]
However, I'm sure that the space character is not the only one that needs to be replaced with a escape sequence. What other the other ones? Is there a function that automatically replaces the special character with their escape sequences?

---

### Post by dtmilano on 2008-06-19
Use, for example
> os.makedirs('this/is the path/to /my dir')

---

### Post by Jadd on 2008-06-19
Thanks, but I was hoping for something that I could use in general, not just for mkdir. I'd like to do
[php]subprocess.call("randomcommand %s" % transform(filename), shell=True)[/php]
where transform is the function I'm looking for.

---

### Post by Martin Witte on 2008-06-19
A filename with a space is not invalid, you can create it by putting it in single quotes:
```
>>> import subprocess
>>> subprocess.call("mkdir -p '%s'" % 'Directory name with spaces', shell=True)
0

```

---

### Post by geirha on 2008-06-19
[php]
import os,subprocess
subprocess.call(['mkdir', '-p', '/tmp/directory with sp/aces and\n stuff'])
os.spawnvp(os.P_WAIT, 'mkdir', ['mkdir', '-p', '/tmp/directory with sp/aces and\n stuff'])
[/php]

---

### Post by ghostdog74 on 2008-06-19
for less worry about which way the slashes go, you can try to use os.path.join().

---

### Post by Can+~ on 2008-06-19
Use raw strings, not that it will solve your problem, but it usually helps with escape characters.
[PHP]normal_string = "this is some string\nasddsadsds."
a_raw_string = r"this is some string\nasddsadsds."[/PHP]

---

### Post by Jadd on 2008-06-21
> **geirha said:**
> [php]
import os,subprocess
subprocess.call(['mkdir', '-p', '/tmp/directory with sp/aces and\n stuff'])
os.spawnvp(os.P_WAIT, 'mkdir', ['mkdir', '-p', '/tmp/directory with sp/aces and\n stuff'])
[/php]
Thanks, that's exactly what I need.

---

### Post by Jadd on 2008-06-21
I just came accross an issue with this solution.
Running this command in a terminal will give an error:
```
gksu gedit --new-window new\ file.txt
```
The solution of course is:
```
gksu "gedit --new-window new\ file.txt"
```
So in python, I now have a problem:
[php]import subprocess
filename = "new file.txt"
# this prints an error
subprocess.call(["gksu", "gedit", "--new-window", filename])
# this opens two files in gedit: new and file.txt
subprocess.call(["gksu", "gedit --new-window %s" % filename])[/php]
How do I deal with this?

---

### Post by geirha on 2008-06-21
If you use gksudo instead of gksu, the first one of your subprocess.calls above should work.

EDIT:
Actually both (gksu and gksudo) should work, I just tested myself, and the problem is that gksu/gksudo is "taking" the options that should be passed to gedit. use -- to tell gksu to stop parsing options.
[php]
subprocess.call(["gksu", "--", "gedit", "--new-window", filename])
[/php]

---

### Post by Jadd on 2008-06-21
Brilliant! That -- trick is just what I need.

---

### Post by Jadd on 2008-07-02
I just discovered that bash uses single quotes to preserve the literal value of a string (including spaces and stuff). The only problem with that is when your filename includes single quotes, but I found [the workaround](http://muffinresearch.co.uk/archives/2007/01/30/bash-single-quotes-inside-of-single-quoted-strings/).

So here's some code with their results:
[php]
import subprocess
# we need to pass shell as True to let bash interpret the single quotes as it normally would
subprocess.call("touch 'a new day.txt'", shell=True) # creates: a new day.txt
subprocess.call(r"touch 'a'\''new'\''day.txt'", shell=True) # creates: a'new'day.txt
[/php]

Here's a function I wrote to automatically surrond with single quotes, replacing any single quotes with the appropriate string:
[php]#!/usr/bin/env python
import subprocess

def surround_with_single_quotes(string):
    """Surrounds the passed string with single quotes and replaces any
    quotes with '\'' required by bash
    >>> surround_with_single_quotes("a'new'day.txt")
    "'a'\\\\''new'\\\\''day.txt'"
    
    The previous example returns (without python's quotes and escape sequences):
    'a'\''new'\''day.txt'
    """
    str = string.replace("'", r"'\''")
    str = "'" + str + "'"
    return str

if __name__ == "__main__":
    import doctest
    doctest.testmod()
    subprocess.call("touch " + surround_with_single_quotes("a'new'day.txt"), shell=True)[/php]

---

