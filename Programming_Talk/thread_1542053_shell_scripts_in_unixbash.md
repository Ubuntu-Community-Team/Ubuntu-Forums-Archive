---
title: "shell scripts in unix/bash"
date: 2010-07-30
forum: Programming Talk
---

### Post by qedprigmosynois on 2010-07-30
I wanted to know what i'm doing wrong with my script here. 
It's a basic .sh file
i wrote with the following
directory=$(pwd)
echo the current directory is $directory
what i get is 
script1.sh: 1: directory not found
the current directory is

what can i do?
i want it to print
the current directory is (insert whatever)

---

### Post by Doobie9 on 2010-07-30
Maybe you could try:

>  DIRECTORY=`pwd` 

---

### Post by DaithiF on 2010-07-30
Hi,
have you got any spaces between directory and the $(pwd) command?  For variable assignments in bash you can't have any spaces:
```
directory = $(pwd)      # won't work
directory=$(pwd)        # works
```
if there is a space then the shell thinks you are trying to run a command called 'directory', and no command by that name exists.

---

### Post by geirha on 2010-08-01
In the subject, you stated bash, but you are missing the hash-bang, and you are running your script with sh (which is not the same as bash).
 
```

/tmp$ cat myscript
#!/bin/bash
echo "The current directory is: $PWD"
/tmp$ chmod +x myscript
/tmp$ ./myscript
The current directory is: /tmp

```

Read [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

