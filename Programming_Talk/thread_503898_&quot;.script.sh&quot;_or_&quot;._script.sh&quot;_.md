---
title: "&quot;./script.sh&quot; or &quot;. script.sh&quot; ..whats the difference?"
date: 2007-07-18
forum: Programming Talk
---

### Post by r0ck80y on 2007-07-18
Hi,
Just made an observation regarding script execution that i cannot quite explain. Suppose i had a script like this, call it say script.sh:
```
#! /bin/sh
echo -e "Enter your name:\n"
read name
echo -e "Your name is $name"
```
If i run the script as```
 ./script.sh
``` from one terminal and instead of typing my name there, i open another terminal and run the command:```
 pstree -p
``` I get the following output:```

`-terminal(5652)-+-bash(5661)-+-less(10054)
                 |            `-pstree(10053)
                 `-bash(9980)---script.sh(10031)

```
But if i run this as ```
 . script.sh
``` and then do a pstree, it shows:```

`-terminal(5652)-+-bash(5661)-+-less(10056)
                 |            `-pstree(10055)
                 `-bash(9980)

```
You can see that the "script.sh" entry is missing after bash(9980)...
Any idea why is this??

---

### Post by McNils on 2007-07-18
. script.sh 
is the same as typing 
source script.sh

The commands in script.sh is executed in the current shell when sourcing a script and therefore is script.sh missing from the result from the second pstree command.

---

### Post by r0ck80y on 2007-07-18
How will i know if the script is running if i don't see it in ps? I didn't quite get the importance of source command :confused:

---

### Post by McNils on 2007-07-18
> **r0ck80y said:**
> How will i know if the script is running if i don't see it in ps? I didn't quite get the importance of source command :confused:
If you want to se that the script is running don't source it, start the script ./script.sh. Sourcing files is usefull when you want to setup the environment, because all commands are done in the current shell.  For example is ~/.bashrc sourced, if it exists, when you start a new shell to setup the environment.

---

