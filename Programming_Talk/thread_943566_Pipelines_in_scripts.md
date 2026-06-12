---
title: "Pipelines in scripts"
date: 2008-10-10
forum: Programming Talk
---

### Post by tmrlvi on 2008-10-10
I have this peculiar desire to write my own scripts using the shell programming language, python or c... I'm doing alright actually, except for one thing-
I can't seem to find a way to handle the information that is passed throught pipelines.
(ie: cat hello_world | capitalized.py)

Can you tell me how to do it in each language? (btw, I do work on ubuntu)

---

### Post by newbuntuxx on 2008-10-10
i believe that variables passed to a python script are stored as a list in: argv

so,

argv[1] = the first thing passed, in that case, Hello_World

---

### Post by kknd on 2008-10-10
> **newbuntuxx said:**
> i believe that variables passed to a python script are stored as a list in: argv

so,

argv[1] = the first thing passed, in that case, Hello_World

Arguments can be accessed this way, but by doing a cat arq | prog, you are redirecting the output of `cat arq` to the input of the script, thus you can access the content reading from the stdin.

---

### Post by iponeverything on 2008-10-10
```
echo hello |tr a-z A-Z

```

or

echo hello |upcase.pl

upcase.pl:
```

#!/usr/bin/perl
while(<>){
    tr/a-z/A-Z/;
    print;
}

```

---

### Post by geirha on 2008-10-10
When you pipe something to your program, you are replacing stdin of your program with stdout of the program at the left of the pipe. When you don't use a pipe, then stdin is read from the keyboard. Consider the following script sum.bash:
[php]#!/bin/bash

sum=0
while read line; do
  for number in $line; do
    (( sum += line ))
  done
done

echo "Sum is: $sum"[/php]

First run it by itself:
```
~$ chmod +x sum.bash
~$ ./sum.bash


```
At this point your looking at a blank line. The while loop is waiting to read some data, type in something:
```
~$ chmod +x sum.bash
~$ ./sum.bash
1 2 3 5
^D
Sum is: 11

```
The ^D means I hit Ctrl+d, which will tell the read command that this is the end of file (file being stdin in this case)

Now lets use echo to give the same data through a pipe. The script will return "instantly" with the sum.
```

~$ echo 1 2 3 5 | ./sum.bash
Sum is: 11

```

---

