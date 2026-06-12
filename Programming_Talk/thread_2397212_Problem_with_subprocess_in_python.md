---
title: "Problem with subprocess in python"
date: 2018-07-26
forum: Programming Talk
---

### Post by mfitzsimmons9 on 2018-07-26
Hi guys, having an issue running a subprocess in python.


```
if (__name__ == "__main__"):
    D = subprocess.Popen(args=sys.argv[1],
                              stdout=subprocess.PIPE,
                              stdin=subprocess.PIPE)
```

Whenever I try to execute the script involving this code I get the following error:

```
Traceback (most recent call last):
File "./attack.py", line 152, in <module>
stdin=subprocess.PIPE)
File "/usr/lib/python2.7/[/FONT][FONT=arial]subprocess.py", line 394, in __init__
 errread, errwrite)
File "/usr/lib/python2.7/[/FONT][FONT=arial]subprocess.py", line 1047, in _execute_child
raise child_exception
OSError: [Errno 2] No such file or directory
```

I then altered it to include shell = True, and then I get this issue:

```
/bin/sh: 1: 5.D: not found
```

where 5.D is argv[1].

I'm new to Ubuntu so any help would be appreciated

---

### Post by &amp;KyT$0P# on 2018-07-26
> **mfitzsimmons9 said:**
> Whenever I try to execute the script involving this code
How are you running the script?  Please post the full command line.

---

### Post by mfitzsimmons9 on 2018-07-27
python ./attack.py 5.D 5.conf

where 5.D and 5.conf are files which exist in the same directory as attack.py

---

### Post by deadflowr on 2018-07-27
*Thread moved to **Programming Talk***

---

### Post by spjackson on 2018-07-27
What happens when you do:
```

5.D 5.conf

```
Is 5.D executable? If not then
```

chmod +x 5.D

```
Is it on your PATH? If not, either change your PATH or specify the path e.g.
```

python ./attack.py ./5.D 5.conf

```

---

### Post by mfitzsimmons9 on 2018-07-27
Thanks for the help mate

python ./attack.py ./5.D 5.conf

Solved the problem. I didn't think about the .D file being an executable.

---

