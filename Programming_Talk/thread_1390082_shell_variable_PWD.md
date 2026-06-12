---
title: "shell variable: PWD"
date: 2010-01-25
forum: Programming Talk
---

### Post by piyush.neo on 2010-01-25
changing the value of variable name PWD show the changed current directory but actully it is in the same directory..
```
piyush@piyush-machine:~$ cd try
piyush@piyush-machine:~/try$ ls
f  file  mkdir t  try
piyush@piyush-machine:~/try$ PWD="/donot/exist"
piyush@piyush-machine:/donot/exist$ ls
f  file  mkdir t  try
piyush@piyush-machine:/donot/exist$ 

```

**Can u explain its mechanism..??**:confused:

---

### Post by MadCow108 on 2010-01-25
PWD is a bash variable which you should usually not mess with.
It is set when you change working directory but not vice versa.

it is apparently also used to display the working directory so you get a wrong display when you change it.

use cd to change the working directory

---

### Post by piyush.neo on 2010-01-25
can you explain this too...just giving echo leaves 1 line..so the second command should leave two line but it is still leaving one..why???
(so much of doubts today....:(:()
```
piyush@piyush-machine:~$ echo 

piyush@piyush-machine:~$ echo `echo`

piyush@piyush-machine:~$ 

```

---

### Post by MadCow108 on 2010-01-25
backquotes seem to strip ending newlines of output:
var=`ls`
echo -n $var

this has no ending newline, although normal ls does
seems reasonable as backquotes are often used like that, and the ending might disturb further handling of the variable, and is just needed for more visually pleasing output

some other weird behavior I just found:
var=`ls -1`
echo -n $var #no newlines!
echo -n "$var" #newlines, but trailing newline stripped

---

### Post by piyush.neo on 2010-01-25
echo have new line problem from history...:wink:
May be someone else clarify it...

---

### Post by Garratt on 2010-01-25
edit: nevermind I mistyped.

---

### Post by piyush.neo on 2010-01-25
> **Garratt said:**
> edit: nevermind I mistyped.

A lot of people can't.....but none of u need to mention it here.
:lolflag:

---

### Post by piyush.neo on 2010-01-29
> **MadCow108 said:**
> backquotes seem to strip ending newlines of output:
var=`ls`
echo -n $var

this has no ending newline, although normal ls does
seems reasonable as backquotes are often used like that, and the ending might disturb further handling of the variable, and is just needed for more visually pleasing output

some other weird behavior I just found:
var=`ls -1`
echo -n $var #no newlines!
echo -n "$var" #newlines, but trailing newline stripped

well now i can put a bit more light over this..
echo is a command and every command accepts arguments.Shell removes extra spaces,tabs and new lines while accepting arguments. So in this case
echo -n $var #no newlines!
all new lines area removed..


But in second case
echo -n "$var" #newlines, but trailing newline stripped
due to quoting the value of $var will be treated as single argument and all its \n will be there in output....:D

---

