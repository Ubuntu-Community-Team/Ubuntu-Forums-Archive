---
title: "how to get $EDITOR variable in python"
date: 2009-03-26
forum: Programming Talk
---

### Post by benj1 on 2009-03-26
Hi
I'm writing a program in python and want to open the users default editor to edit text ie the $EDITOR variable.

the problem is, is that the $EDITOR variable is part of bash & every external command i run, runs in the sh shell, which doesn't have $EDITOR, and i can't work out how to run it in another shell (in my case bash), i've been using the subprocess module by the way.
I can get the $SHELL variable so thats not a problem, that works from sh.
anyone got any ideas?
thanks in advance.

---

### Post by ghostdog74 on 2009-03-26
you get them through os.environ()
Check the docs, always.

---

### Post by yeats on 2009-03-26
I don't know the answer to your specific question, but would it help to know that "sh" on Ubuntu is symbolically linked to bash anyway?:

```
ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2009-03-20 15:08 /bin/sh -> bash
```

---

### Post by benj1 on 2009-03-26
@chrissharp123
i thought so too but if you go in to sh & type 'echo $EDITOR' it doesn't work

@ghostdog74
just tried that
```
import os
editor = os.environ['EDITOR']
print editor
```
i assume the code is ok i tried it with SHELL and HOME and it worked

i also tried


```
pipe = Popen("echo $EDITOR", shell = True,  stdout= PIPE).stdout
shell = pipe.read()
print shell
```
which doesn't work either but again works with $HOME and $SHELL

---

### Post by ghostdog74 on 2009-03-26
what are you actually trying to do?

---

### Post by benj1 on 2009-03-26
my fault my apologies

in my .bashrc 
had editor line set to: 
EDITOR=

not:
export EDITOR=

nevermind, thanks everybody

---

