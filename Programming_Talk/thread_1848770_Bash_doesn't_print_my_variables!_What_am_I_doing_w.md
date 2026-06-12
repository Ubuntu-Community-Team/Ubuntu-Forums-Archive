---
title: "Bash doesn't print my variables! What am I doing wrong?"
date: 2011-09-23
forum: Programming Talk
---

### Post by Sprak on 2011-09-23
Hi!

I've run into a strange problem regarding a small shell script:

```

#! /bin/sh
FIRSTPATH=/first/path/
SECONDPATH=/second/path/

echo Line 1: Only first: "$FIRSTPATH"
echo Line 2: First: "$FIRSTPATH" Second: "$SECONDPATH"
echo Line 3: Second: "$SECONDPATH" First: "$FIRSTPATH"  

```

And the output I get when running the file is:
```

me@sprak:~$ ./bug_in_bash.sh 
Line 1: Only first: /first/path/
 Second: /second/path/path/
Line 3: Second: /second/path/ First: /first/path/

```

I have a standard 32-bits Natty installation:

```

me@sprak:~$ uname -a
Linux sprak 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux
me@sprak:~$ cat /etc/issue
Ubuntu 11.04 \n \l

me@sprak:~$ bash -version
GNU bash, version 4.2.8(1)-release (i686-pc-linux-gnu)
Copyright (C) 2011 Free Software Foundation, Inc.
Licens GPLv3+: GNU GPL version 3 eller senare <http://gnu.org/licenses/gpl.html>

```


Why doesn't the 6th line in the script (```
echo Line 2: First: "$FIRSTPATH" Second: "$SECONDPATH"

```) yield the result ```
Line 2: First: /first/path/ Second: /second/path/
```?

Please, is there anyone who know what might be wrong or has encountered something similar before? 

PS.
Perhaps it can help with some mor information:
If i run the script with "#! /bin/sh -x" instead then I get the following output:

```

+ FIRSTPATH=/first/path/
+ SECONDPATH=/second/path/
+ echo Line 1: Only first: /first/path/
Line 1: Only first: /first/path/
+ echo Line 2: First: /first/path/ Second: /second/path/
Line 2: First: /first/path/ Second: /second/path/
+ echo Line 3: Second: /second/path/ First: /first/path/
Line 3: Second: /second/path/ First: /first/path/

```
DS.

---

### Post by ofnuts on 2011-09-23
> **Sprak said:**
> Hi!

I've run into a strange problem regarding a small shell script:

```

#! /bin/sh
FIRSTPATH=/first/path/
SECONDPATH=/second/path/

echo Line 1: Only first: "$FIRSTPATH"
echo Line 2: First: "$FIRSTPATH" Second: "$SECONDPATH"
echo Line 3: Second: "$SECONDPATH" First: "$FIRSTPATH"  

```And the output I get when running the file is:
[CODE]

You code works OK for me.  The result you have could be caused by a carriage return (without line feed) right after $FIRSTPATH"

---

### Post by sisco311 on 2011-09-23
It works for me too, but it's not a bash script. sh is not bash. In Ubuntu, sh is a symlink to dash. Even if sh is a symlink to bash, when invoked with the name sh, bash tries to mimic the startup behavior of historical version of sh, while confirming to the POSIX standard. 

By convention, we capitalize environment variables (PAGER, EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...). All other variable names should contain at least one lowercase letter. Variable names are case-sensitive; this convention avoids accidentally overriding environmental and internal variables.

Also, don't use extensions for your scripts. Scripts define new commands that you can run, and commands are generally not given extensions.

---

### Post by Sprak on 2011-09-23
> **ofnuts said:**
> You code works OK for me.  The result you have could be caused by a carriage return (without line feed) right after $FIRSTPATH"

That must be it. I opened the file in nano and saved it again, and that version works. Both of files look the same to the naked eye, but diff finds a difference between them. That must mean that some of the whitespace/new line characters are different.

```

me@sprak:~$ cat bug_in_bash.sh 
#! /bin/sh
FIRSTPATH=/first/path/
SECONDPATH=/second/path/

echo Line 1: Only first: "$FIRSTPATH"
echo Line 2: First: "$FIRSTPATH" Second: "$SECONDPATH"
echo Line 3: Second: "$SECONDPATH" First: "$FIRSTPATH"   
me@sprak:~$ cat bug_in_bash2.sh 
#! /bin/sh 
FIRSTPATH=/first/path/
SECONDPATH=/second/path/

echo Line 1: Only first: "$FIRSTPATH"
echo Line 2: First: "$FIRSTPATH" Second: "$SECONDPATH"
echo Line 3: Second: "$SECONDPATH" First: "$FIRSTPATH"   
me@sprak:~$ diff bug_in_bash.sh bug_in_bash2.sh 
1,2c1,2
< #! /bin/sh
< FIRSTPATH=/first/path/
---
> #! /bin/sh 
> FIRSTPATH=/first/path/

```


Thanks for the help! :)

---

### Post by Sprak on 2011-09-23
> **sisco311 said:**
> ...
Thanks for the corrections/tips!

---

### Post by ingeva on 2011-09-24
> **Sprak said:**
> Thanks for the corrections/tips!
I sometimes get similar unexplicable errors.
It can often help to type the offending line again in an editor, being careful to not type non-printing characters.

---

