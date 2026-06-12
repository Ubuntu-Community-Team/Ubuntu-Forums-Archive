---
title: "[SOLVED] simple bash script please help."
date: 2008-09-30
forum: Programming Talk
---

### Post by rosj04 on 2008-09-30
This is driving me crazy.. I've never fiddled with bash scripts before but i have taken a couple of c++ courses (years ago, so 99% is forgotten) 

What I'm looking for is a simple bash script that checks if compiz is running, and if so runs a command. If compiz is not running it keeps checking until it is. 

Simple enough ey? one would think so.. but I can't for the life of me remember how I should write it down. 

all I'm thinking is some kind of while loop like this:


> #!/bin/bash

CHANGE=0
while [ $CHANGE == 0 ]; do
	if ps -e | grep compiz; then
	CHANGE=1
	fi
done

if [ $CHANGE == 1 ]; then
<insert command here>
fi

Which doesn't work (not suprisingly).

My searching skills must be in a horrendous state because I've been searching this forum and google for close to 2 hours now without any luck. 

Any help would be much appreciated :(

---

### Post by drubin on 2008-09-30
Firstly welcome to the forums.  

This would not be the best place to post a question related to programming and bash.  A better place would be [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39")

For the mods: Could you move this. 

here are some links that might point you in the correct direction
[http://ubuntuforums.org/showthread.php?t=702434](http://ubuntuforums.org/showthread.php?t=702434)
[http://www.franzone.com/2007/09/23/how-can-i-tell-if-my-bash-script-is-already-running/](http://www.franzone.com/2007/09/23/how-can-i-tell-if-my-bash-script-is-already-running/)

---

### Post by rosj04 on 2008-09-30
thank you for the welcome, 

and I'm sorry if I posted it in the wrong place, I just thought "absolute beginner.. yep that sounds about right" :D

---

### Post by KIAaze on 2008-09-30
Well, I'd say you've already done all the work.
Your script works after just a few modifications:
```
#!/bin/bash
PROG=compiz
CHANGE=0

while [ $CHANGE == 0 ]; do
if ps -e | grep $PROG; then
CHANGE=1
fi
done

if [ $CHANGE == 1 ]; then
	echo "yes, it's running. :)"
fi 

```
using PROG=compiz and $PROG is optional, but it allows changing the program you are checking for more easily.
(I tested the script with "top".)

---

### Post by Nepherte on 2008-09-30
> **rosj04 said:**
> This is driving me crazy.. I've never fiddled with bash scripts before but i have taken a couple of c++ courses (years ago, so 99% is forgotten) 

What I'm looking for is a simple bash script that checks if compiz is running, and if so runs a command. If compiz is not running it keeps checking until it is. 

Simple enough ey? one would think so.. but I can't for the life of me remember how I should write it down. 

all I'm thinking is some kind of while loop like this:




Which doesn't work (not suprisingly).

My searching skills must be in a horrendous state because I've been searching this forum and google for close to 2 hours now without any luck. 

Any help would be much appreciated :(
Your script works without changes here (tested with compiz). Code seems fine to me as well (deuh, cause it works here). What command are you trying to run when compiz is active? You made the script executable too right?

---

### Post by KIAaze on 2008-09-30
A simpler version:
```
#!/bin/bash
PROG=compiz

until ( ps -e | grep $PROG ); do
	echo >/dev/null #because we can't have an empty loop
done

echo "yes, it's running. :)"

```

edit: Another one which uses $? (=exit status of last command):
```
#!/bin/bash
PROG=compiz

ps -e | grep $PROG
until [ $? -eq 0 ] ; do
        ps -e | grep $PROG
done

echo "yes, it's running. :)"

```

---

### Post by drubin on 2008-09-30
> **rosj04 said:**
> thank you for the welcome, 

and I'm sorry if I posted it in the wrong place, I just thought "absolute beginner.. yep that sounds about right" :D

No worries every one must start at one point.
Reported: asked them to move it for you :) (Maybe you will get other points of views.)

---

### Post by Rocket2DMn on 2008-09-30
Moved to Programming Talk.

---

### Post by rosj04 on 2008-09-30
TY KIAaze, your versions worked very well and were more elegant so kudos :)

Nepherte, hmm, dont know why my own script failed.. because when I tried it now it worked like a charm as well.

Edit: On further investigation it was my own fault, I tried to implement my original script to solve a problem I had, without checking if the script itself worked. As it turns out compiz was the wrong process to check for to fix the problem but when I on a whim checked for compiz.real it was all solved :)

---

### Post by nowshining on 2008-10-01
hmmm all scrips i tried on my machine say yes compiz is running, but it's not :/ but the process ids change

 1845 pts/1    00:00:00 compizchecker
yes, it's running. :)


then

 1848 pts/1    00:00:00 compizchecker
yes, it's running. :)

---

### Post by KIAaze on 2008-10-01
Mmh, I think you misunderstood what the "PROG=" line is for.

I first tried finding a program called "compizchecker" and the closest I found was this one: [http://ubuntuforums.org/showthread.php?p=4905984](http://ubuntuforums.org/showthread.php?p=4905984)

But it's named "./compiz-check".

I suppose you named your script "compizchecker" and wrote "PROG=compizchecker" in it.
Am I right?

The "PROG=" line is meant to choose the program you want to check for.
ex1: test if "top" is running:
```
#!/bin/bash
#program/process to check for
PROG=top

ps -e | grep $PROG
until [ $? -eq 0 ] ; do
        ps -e | grep $PROG
done

echo "yes, it's running. :)"

```

ex2: test if "compiz" is running:
```
#!/bin/bash
#program/process to check for
PROG=compiz

ps -e | grep $PROG
until [ $? -eq 0 ] ; do
        ps -e | grep $PROG
done

echo "yes, it's running. :)"

```
The name you give the script itself doesn't matter at all and you can leave "compizchecker" as name.

The reason the process number kept changing is obviously because the script always got launched with a new process number and checks if it is itself running. ;)

edit: A more advanced version which takes one argument and gives usage instructions if no argument is given:
```
#!/bin/bash
if [ $# -ne 1 ]
then
        echo
        echo "This shellscript will keep running until a certain process is running and then tell you it's running and exit."
        echo "usage :"
        echo "`basename $0` <program/process to check for>"
        exit 0
fi

PROG=$1

ps -e | grep $PROG 
until [ $? -eq 0 ] ; do
	ps -e | grep $PROG 
done

echo "yes, it's running. :)"
```

$# = nb of arguments
-ne = not equal
`basename $0` = trick to get the name of the shellscript ($0 = full path to the script (argument 0 of the command))

---

### Post by nowshining on 2008-10-01
> **KIAaze said:**
> Mmh, I think you misunderstood what the "PROG=" line is for.

I first tried finding a program called "compizchecker" and the closest I found was this one: [http://ubuntuforums.org/showthread.php?p=4905984](http://ubuntuforums.org/showthread.php?p=4905984)

But it's named "./compiz-check".

I suppose you named your script "compizchecker" and wrote "PROG=compizchecker" in it.
Am I right?

The "PROG=" line is meant to choose the program you want to check for.
ex1: test if "top" is running:
```
#!/bin/bash
#program/process to check for
PROG=top

ps -e | grep $PROG
until [ $? -eq 0 ] ; do
        ps -e | grep $PROG
done

echo "yes, it's running. :)"

```

ex2: test if "compiz" is running:
```
#!/bin/bash
#program/process to check for
PROG=compiz

ps -e | grep $PROG
until [ $? -eq 0 ] ; do
        ps -e | grep $PROG
done

echo "yes, it's running. :)"

```
The name you give the script itself doesn't matter at all and you can leave "compizchecker" as name.

The reason the process number kept changing is obviously because the script always got launched with a new process number and checks if it is itself running. ;)

edit: A more advanced version which takes one argument and gives usage instructions if no argument is given:
```
#!/bin/bash
if [ $# -ne 1 ]
then
        echo
        echo "This shellscript will keep running until a certain process is running and then tell you it's running and exit."
        echo "usage :"
        echo "`basename $0` <program/process to check for>"
        exit 0
fi

PROG=$1

ps -e | grep $PROG 
until [ $? -eq 0 ] ; do
	ps -e | grep $PROG 
done

echo "yes, it's running. :)"
```

$# = nb of arguments
-ne = not equal
`basename $0` = trick to get the name of the shellscript ($0 = full path to the script (argument 0 of the command))

no i didn't change a thing, I just copied and pasted and named the file compizchecker or whatever...hmmm

---

### Post by KIAaze on 2008-10-01
Sorry, my fault for not testing it for real with compiz (don't have it installed).
The "ps -e | grep compiz" command searches for all processes containing "compiz", not for processes named exactly "compiz".
And since your script name contains compiz, it supposes that compiz is already running.

Here's an improved script fixing that problem.
It should work if named "compizchecker" or "checkcompiz". (just don't name it "compiz"! ^^)

```
#!/bin/bash
if [ $# -ne 1 ]
then
        echo
        echo "This shellscript will keep running until a certain process is running and then tell you it's running and exit."
        echo "usage :"
        echo "`basename $0` <program/process to check for>"
        exit 0
fi

PROG=$1

ps -e | grep "\b$PROG\b" 
until [ $? -eq 0 ] ; do
	ps -e | grep "\b$PROG\b" 
done

echo "yes, it's running. :)"

```

---

### Post by ghostdog74 on 2008-10-01
> **rosj04 said:**
> 
What I'm looking for is a simple bash script that checks if compiz is running, and if so runs a command. If compiz is not running it keeps checking until it is. 

```

while true
do
   ps -ef |grep kmess|grep -v grep && ( echo "Put your command here" ) && break
   sleep 10
done

```

---

### Post by KIAaze on 2008-10-02
Mmh, I didn't know about "break".
But why complexify things by using "ps -ef" + grep/invert grep?

```

#!/bin/bash
while true
do
   ps -e |grep "\bcompiz\b" && ( echo "Put your command here" ) && break
done

```
Script improvement continues.
:P

---

### Post by ghostdog74 on 2008-10-02
```

pidof compiz > /dev/null 2>&1 && echo "ok"

```

---

### Post by KIAaze on 2008-10-02
I give up. :)
Except that I'd remove the  "> /dev/null 2>&1".
```
while true
do
   pidof compiz && ( echo "Put your command here" ) && break
done

```

---

