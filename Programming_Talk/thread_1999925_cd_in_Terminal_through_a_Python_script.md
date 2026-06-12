---
title: "cd in Terminal through a Python script"
date: 2012-06-08
forum: Programming Talk
---

### Post by dominion_vortar on 2012-06-08
Hi,

I'm writing a Python script to automate a few things for me in Terminal, but whenever I use

```
os.system("cd ~/path")
```

nothing happens... Is it possible for a Python script to change directory in this way? Any other commands I use execute fine...

Thanks :)

---

### Post by MG&amp;TL on 2012-06-08
os.system() spawns a subprocess, if I recall. Therefore, that executes in the subprocess.

You want os.chdir.

```
michael@laptop:~$ python
Python 2.7.3 (default, Apr 20 2012, 22:39:59) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.getcwd()
'/home/michael'
>>> os.chdir("Documents")
>>> os.getcwd()
'/home/michael/Documents'
>>> 

```that help any?

---

### Post by dominion_vortar on 2012-06-08
Thanks for your quick response. Your solution half worked... if I do it in terminal manually it works a treat

```
nas45-114:~ John$ python
Python 2.7.1 (r271:86832, Jun 16 2011, 16:59:05) 
[GCC 4.2.1 (Based on Apple Inc. build 5658) (LLVM build 2335.15.00)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import os
>>> os.getcwd()
'/Users/John'
>>> exit()
```

However, if I try to run the script which contains the exact same commands

```
import os
os.getcwd()
```

then I just get the following, and it doesn't list the directory

```
nas45-114:~ John$ python /Users/John/Desktop/test.py
nas45-114:~ John$ 

```

It must be an issue with the script itself, as the Python commands clearly work on their own...

---

### Post by MG&amp;TL on 2012-06-08
> **dominion_vortar said:**
> 
It must be an issue with the script itself, as the Python commands clearly work on their own...

In the python interpreter, everything is printed by default.

If you want to do that in a script, use print.

```

import os
print os.getcwd()
os.chdir("/home/John/Documents")
print os.getcwd()
```

---

### Post by dominion_vortar on 2012-06-08
Ah, of course! 

Thanks very much, I appreciate your help. Not worked in Python before, still getting used to scripting!

Cheers :)

---

### Post by MG&amp;TL on 2012-06-08
> **dominion_vortar said:**
> Ah, of course! 

Thanks very much, I appreciate your help. Not worked in Python before, still getting used to scripting!

Cheers :)

Not a problem, keep reading on the os module, it's a very useful one. :)

---

