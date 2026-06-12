---
title: "Scripting question"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by anewguy on 2011-09-22
I don't know if it's just too late right now or what, but I'm trying to help another user on the forum with their problem, and have run into a problem:

I can't seem to make a script to do this correctly:

need to know what arguement 1 on the calling line is (e.g. ./my.sh arg1 )

need to know how to put that in a blkid command and have the returned value stored in another variable:

xx=blkid $arg1

when I try this with just:

xx=blkid /dev/sdb1  (with sudo) the resulting xx doesn't contain the output string from the blkid command.  It should look something like:

/dev/sdb1: SEC_TYPE="msdos" UUID="2A29-EDE7" TYPE="vfat"

I then need to extract what is inside the quotes for UUID and store in another variable like my_uuid, and need this variable accessable in another command such as:

some_command param1 param2 $my_uuid

I've tried what extremely little I know at this time about the cut command but can't make any of this work.

The help would be greatly appreciated, and if you'd like to post the answer straight into the thread in question, please see:

[http://ubuntuforums.org/showthread.php?t=1847604]("http://ubuntuforums.org/showthread.php?t=1847604")

Thank you SO much for any help you can provide!

dave ;)

---

### Post by Lisiano on 2011-09-22
In both SH and Bash, to run a command and set a variable as the output of the command either backtick the command or put it in $( ... ) for example
```
#!/bin/sh
VAR=$(blkid)
VAR2=`date`
echo $VAR
echo $VAR2
```
All arguments on the script are interpretted as $1, $2 etc. All are $@

---

### Post by mutley89 on 2011-09-22
For the first argument use $1.
 To set a variable to the output of a command enclose it in backticks or use $(command): 
 ```
xx=$(blkid $1)
``` You can use the -s option to blkid to print only the UUID, then strip the UUID= and quotes:
 ```
my_uuid=$(blkid -s UUID $1 | cut -d \" -f 2 )
```

---

