---
title: "Python not working like it should"
date: 2006-01-23
forum: Programming Talk
---

### Post by chimera on 2006-01-23
OK a rather weird and disturbing experience:
I open up the interactive python shell (open terminal and type python)
I enter:
```
print "trk"
```
and I get a normal output.

Now, if make a trk.py file with the same line of code in it, set the perimissions to execute, and try to execute it(by double clickingit, and clicking "run in terminal",a terminal window just opens and closes in a moment, and if I click "run", nothing happens. What am I doing wrong?

---

### Post by thumper on 2006-01-23
Your program prints then exits.

Run it in a terminal with ./trk.py (assuming it is in the current directory) and you'll see it print and go back to the prompt.

---

### Post by chimera on 2006-01-23
[QUOTE=thumper]Your program prints then exits.

Run it in a terminal with ./trk.py (assuming it is in the current directory) and you'll see it print and go back to the prompt.[/QUOTE]

```

chimera@HOMEPC:~$ ./trk.py
Warning: unknown mime-type for "trk" -- using "application/*"
Error: no such file "trk"
chimera@HOMEPC:~$

```

---

### Post by Wallakoala on 2006-01-23
you can also add the line:
```
raw_input()
```
at the botton to make it so that it waits for any form of input before exiting

---

### Post by toojays on 2006-01-23
Does the first line of your file say "#!/usr/bin/python"?

The shell needs this line to know which interpreter to pass your script to.

---

### Post by chimera on 2006-01-23
toojays, yes, that's what was missing apparently. thanks for the help, it works now.

---

### Post by doas777 on 2007-12-28
I'm having a similar issue, but I'm afraid the bangline didn't do it for me. 

does anyone see anything wrong here?
```

#!/usr/bin/python
print "Hello, World!"

```

the file is executable:
```

# ls -l
total 4
-rwxr-xr-x 1 <user> <user> 42 2007-12-28 17:01 hello.py

```

and python exists at /usr/bin/python:
```

# ls -l /usr/bin | grep python
lrwxrwxrwx  1 root   root         23 2007-12-23 15:50 pdb2.5 -> ../lib/python2.5/pdb.py
lrwxrwxrwx  1 root   root          9 2007-12-23 15:49 python -> python2.5
-rwxr-xr-x  1 root   root    1158452 2007-10-05 10:17 python2.5
lrwxrwxrwx  1 root   root         29 2007-12-23 15:49 pyversions -> ../share/python/pyversions.py
-rwxr-xr-x  1 root   root       3179 2007-10-05 10:01 xmlproc_parse.python-xml
-rwxr-xr-x  1 root   root       4211 2007-10-05 10:01 xmlproc_val.python-xml

```

but when I execute it with:
```

# hello.py
bash: hello.py: command not found

```

or
```

# . hello1.py
Warning: unknown mime-type for "Hello, World!" -- using "application/*"
Error: no such file "Hello, World!"

```

but
```

# python hello.py
Hello, World!

```


some times I've noticed that banglines mysteriously work if you put a space between the #! and the first /, but that results in this:
```

# hello.py
bash: hello.py: command not found
# . hello.py
" -- using "application/*" for "Hello, World!
"rror: no such file "Hello, World!

```

any ideas?

---

### Post by RafG on 2007-12-28
> **doas777 said:**
> but when I execute it with:
```

# hello.py
bash: hello.py: command not found

```


This will not work, unless "." (the current directory) is in your $PATH (don't be tempted to add it there, though, because that's a security risk!!).

Execute like this:

```
$ ./hello.py
```

---

### Post by ghostdog74 on 2007-12-28
> **doas777 said:**
> 
any ideas?
yes , learn how to use the shell.

---

### Post by pmasiar on 2007-12-28
> **doas777 said:**
> 
any ideas?

Use IDLE - simple Python IDE. You can edit code in it, then run it.

---

### Post by Majorix on 2007-12-29
> **ghostdog74 said:**
> yes , learn how to use the shell.

Don't be so rude, we all had our times.

Use the way RafG defined and you should be fine.

---

### Post by ghostdog74 on 2007-12-29
> **Majorix said:**
> Don't be so rude, we all had our times.
that guy asked for ideas, i gave him the best one. Now why is that rude?  OS knowledge is closely intertwined with how you work with programming languages as well.

---

### Post by doas777 on 2007-12-30
Thanks folks, 
for now I'm just calling python implicitly (since I want to hook scripts to nautilus-actions) so I'll keep that in mind in future. I had been thinking that since my pwd was the dir the script was in, that I could neglect pathing, but that does not appear to be the case.

one of the things I like about linux, is that it forces me to learn a little almost everytime I login. in that vein, GD74, do you have any "required reading" on BASH?
 
Happy new year

---

### Post by ghostdog74 on 2007-12-30
> **doas777 said:**
> in that vein, GD74, do you have any "required reading" on BASH?
 

1) [Advanced Bash guide]("http://tldp.org/LDP/abs/html/")
2) [Unix CD bookshelf]("http://www.unix.org.ua/orelly/")
3) [Learning the bash shell]("http://211.99.128.10/Tech/OReilly.Learning.the.bash.Shell.2nd.Edition.chm")

---

