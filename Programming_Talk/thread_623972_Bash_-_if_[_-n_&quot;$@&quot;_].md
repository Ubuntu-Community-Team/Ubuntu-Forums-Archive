---
title: "Bash - if [ -n &quot;$@&quot; ]"
date: 2007-11-26
forum: Programming Talk
---

### Post by Rizado on 2007-11-26
My problem is quite simple, this script of mine isn't working.
```
if [ -n "$@" ]
then
        VICTIM="$@"
        echo "if?"
else
        VICTIM="127.0.0.1"
        echo "else?"
fi
```

What I want is that if i run "./myScript 192.168.0.1" if should make VICTIM=192.168.0.1 and this works fine. But when I run "./myScript" without anything else it should use a default 127.0.0.1 instead.
As far as I know $@ is empty, I've even echoed it to see that it is. But it still doesn't want to run else. What am I doing wrong?

---

### Post by ubuntukerala1980 on 2007-11-26
#!/bin/bash
if [ -n "$1" ]
then
        VICTIM="$1"
        echo "if?"
else
        VICTIM="127.0.0.1"
        echo "else?"
fi

---

### Post by geirha on 2007-11-26
try using ```
[ "$1" != "" ]
``` instead.

---

### Post by Rizado on 2007-11-26
Okay thanks! Using $1 instead of $@ works great, anyone cares to explain what the difference is?

---

### Post by ubuntukerala1980 on 2007-11-26
$1 = First agument supplied after the program/function on execution.

[http://subsignal.org/doc/AliensBashTutorial.html]("http://subsignal.org/doc/AliensBashTutorial.html")

---

### Post by Rizado on 2007-11-26
How come $@ doesn't work when $1 does? If $1 is emtpy, $@ must be empty as well right?

---

### Post by volanin on 2007-11-26
> **Rizado said:**
> How come $@ doesn't work when $1 does? If $1 is emtpy, $@ must be empty as well right?

From the **bash** manpage:
*"When there are no  positional  parameters,  "$@"  and  $@ expand to nothing (i.e., they are removed)."*


So, when you pass no arguments, bash interprets it as:
**if [ -n ]; then...**

Which for some reason evaluates to TRUE.


To get your desired behviour, use:
**if [ -n ""$@"" ]; then...**, which will evaluate to **if [ -n "" ]; then...** in case of no parameters.


Somebody smoked before programming this!
:)

---

### Post by kast on 2007-11-26
So its not just your beans that are roasted \\:D/

---

### Post by Rizado on 2007-11-26
> **volanin said:**
> From the **bash** manpage:
*"When there are no  positional  parameters,  "$@"  and  $@ expand to nothing (i.e., they are removed)."*


So, when you pass no arguments, bash interprets it as:
**if [ -n ]; then...**

Which for some reason evaluates to TRUE.


To get your desired behviour, use:
**if [ -n ""$@"" ]; then...**, which will evaluate to **if [ -n "" ]; then...** in case of no parameters.


Somebody smoked before programming this!
:)Oh my [img]http://www.flashback.info/images/smilies2/noexpression.gif[/img]
That's just stupid... Glad it isn't me [img]http://www.flashback.info/images/smilies2/grin.gif[/img]

---

### Post by markp1989 on 2011-08-13
found this thread when googleing.

this seemed to work for me: 


```
if [ $# -eq 0 ] ; then
    printf "%s\n" "no args given, exiting" 
    exit 1
fi

```

from what i understand $# is read as the number of args, so it reads 0 if there are none.

---

### Post by JupiterV2 on 2011-08-13
Seeing that your variable name for someone's IP address is VICTIM, I'd be curious to know what exactly it is you're doing? I'm not sure anyone on these forums are interested in helping someone do something inappropriate.

---

### Post by ofnuts on 2011-08-13
Simplest way:

victim=${1:-127.0.0.1}

(see [http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion) )

---

### Post by ofnuts on 2011-08-13
> **JupiterV2 said:**
> Seeing that your variable name for someone's IP address is VICTIM, I'd be curious to know what exactly it is you're doing? I'm not sure anyone on these forums are interested in helping someone do something inappropriate.

Well, 

1) if he forgets the address, it applies it to itself....
2) his problem is general enough, and he would find the answer elsewhere 
3) given the current skill level, nothing to fear in the short term :-)

---

### Post by lavinog on 2011-08-15
4)This thread is from November 26th, 2007

The victim=${1:-127.0.0.1} is nice...ty for the info ofnuts.

---

### Post by ofnuts on 2011-08-15
> **lavinog said:**
> 4)This thread is from November 26th, 2007

We are doomed then :)

---

