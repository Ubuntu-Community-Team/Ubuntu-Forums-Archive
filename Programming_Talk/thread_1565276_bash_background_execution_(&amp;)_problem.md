---
title: "bash background execution (&amp;) problem"
date: 2010-08-31
forum: Programming Talk
---

### Post by terminator14 on 2010-08-31
In order to force a script to run as root (such as in cases where the script is a daemon and most of its commands require root), I put together a small chunk of code to place at the top of the script:

```
uid=$(/usr/bin/id -u)
if [[ $uid != 0 ]]
then
	echo "This script can only be run or configured by root. Proceeding to run script as root."
	echo
	if [ -s $DISPLAY ]
	then
		sudo $0 $*
	else
		gksu $0 $*
	fi
	exit $?
fi
```

This seems to work reasonably well except for one side effect which I just ran into. Background execution (using & at the end of commands) is ignored. Here's an example:

```
#!/bin/bash
uid=$(/usr/bin/id -u)
if [[ $uid != 0 ]]
then
	echo "This script can only be run or configured by root. Proceeding to run script as root."
	echo
	if [ -s $DISPLAY ]
	then
		sudo $0 $*
	else
		gksu $0 $*
	fi
	exit $?
fi

(sleep 10s; echo hi) &
```

If the script above is named test.sh, and is launched as:

```
./test.sh
```

it will freeze and wait for 10 seconds before giving back the console. If it is run as:

```
sudo ./test.sh
```

on the other hand, it will run '(sleep 10s; echo hi)' in the background as it should and immediately give up the console.

Am I missing something here? Does my method for forcing root execution for a script have a huge flaw, or does it just need a tiny modification?

PS. I tried adding & to the end of the "sudo $0 $*" line and "gksu $0 $*" line but this prevents the script from being able to read input from the terminal.

---

### Post by Vox754 on 2010-09-01
> **terminator14 said:**
> 
...
it will freeze and wait for 10 seconds before giving back the console.


I thought this was interesting. The problem is the nested subshells.

1. Run with root.
```

#!/bin/bash
[B]#
# When this script runs, a subshell is created; we'll call it Shell_1
#[/B]
uid=$(/usr/bin/id -u)

[B]#
# It is root, "uid==0", so this conditional is skipped.
#[/B]
if [[ $uid != 0 ]]
then
	...
fi

[B]#
# This creates a subshell, Shell_1.1,
# but it is run in the background, so Shell_1 returns to the console
#[/B]
(sleep 10s; echo hi) &

```


2. Run without root.
```

#!/bin/bash
[B]#
# A subshell is created; we'll call it Shell_1
#[/B]
uid=$(/usr/bin/id -u)

[B]#
# It is not root, it enters the conditional.
#[/B]
if [[ $uid != 0 ]]
then
	echo "This script can only be run or configured by root. Proceeding to run script as root."
	echo
	if [ -s $DISPLAY ]
	then
		sudo $0 $*  **# It will call this same script,**
	else                **# but creating another subshell, Shell_2,**
		gksu $0 $*  **# and it's child, Shell_2.1,**
	fi                  **# which runs in the background of Shell_2,**
                            **# not in the background of Shell_1**

	exit $?             **# This will finally exit Shell_1**
fi
...

```

1. Run with root
```

Shell_1
    Shell_1.1 &  (10 seconds)

```

2. Run without root
```

Shell_1
sudo

    Shell_2
        Shell_2.1 &  (10 seconds)

```

The console is blocked by Shell_1. It cannot release the console until it's children Shell_2 and Shell_2.1, have finished.

This can be sorted by calling
```

    exec sudo $0 $*

```

The child Shell_2 replaces Shell_1 as the parent, avoiding the creation of nested subshells.

2. Run without root
```

Shell_1
exec sudo

Shell_2
    Shell_2.1 &  (10 seconds)

```

However, in general, you should never call "sudo" inside the script. If the user does not have privileges, the script should tell the user that, and exit.

The user should be forced to obtain privileges externally, either calling the script through "sudo", "su", "gksu", or logging in as "root". That's how system scripts work.

---

### Post by terminator14 on 2010-09-01
Thanks for the detailed explanation. It's very clear and helpful. 

When replacing the "sudo $0 $*" with "exec sudo $0 $*", it does in fact work the way I intended. When replacing "gksu $0 $*" with "exec gksu $0 $*" however, it seems that Shell_1 still waits for Shell_2 to exit which results in the same problem. Is there any reason using "exec" would work for sudo but not gksu?

> **Vox754 said:**
> However, in general, you should never call "sudo" inside the script. If the user does not have privileges, the script should tell the user that, and exit.

The user should be forced to obtain privileges externally, either calling the script through "sudo", "su", "gksu", or logging in as "root". That's how system scripts work.

I understand this, and if I was to write an actual daemon for public use, I would definitely go this route. I am however trying to write a daemon that people who may not know what sudo is may use. A script that doesn't require the user to run itself again with higher privileges seems simpler for beginners to understand. I suppose I could make it print something like "You don't have the right permissions to run this daemon. Please use sudo $0 instead." but for now I'm just trying to figure out why my current implementation fails.

Also, the "exit $?" was meant for Shell_1 to hit in case the user was not running the script as root so that Shell_1 would not continue to run the rest of the script (since Shell_2 was responsible for that now). Using "exec", if I understand correctly, this "exit $?" is unnecessary and will never be reached since Shell_1 will exit as soon as Shell_2 starts up. Is this right?

---

### Post by terminator14 on 2010-09-01
Playing around with it a little bit, I just found something strange. If I get rid of the gksu part completely to end up with:

```
#!/bin/bash
uid=$(/usr/bin/id -u)
if [[ $uid != 0 ]]
then
	echo "This script can only be run or configured by root. Proceeding to run script as root."
	echo
	sudo $0 $*
	exit $?
fi

(sleep 10s; echo hi) &
```

and run it as ./test.sh (with no sudo), Shell_1 actually runs "sudo $0 $*" creating Shell_2, but then Shell_1 continues on to "exit $?" and releases the console immediately while Shell_2 continues to run (sleep 10s; echo hi) in the background. It seems the "gksu" was the problem all along. According to your explanation, which makes sense to me, in this case, Shell_1 should have stopped at "sudo $0 $*" and waited for Shell_2 to return, should it not?

---

### Post by rnerwein on 2010-09-04
> **terminator14 said:**
> Playing around with it a little bit, I just found something strange. If I get rid of the gksu part completely to end up with:

```
#!/bin/bash
uid=$(/usr/bin/id -u)
if [[ $uid != 0 ]]
then
    echo "This script can only be run or configured by root. Proceeding to run script as root."
    echo
    sudo $0 $*
    exit $?
fi

(sleep 10s; echo hi) &
```and run it as ./test.sh (with no sudo), Shell_1 actually runs "sudo $0 $*" creating Shell_2, but then Shell_1 continues on to "exit $?" and releases the console immediately while Shell_2 continues to run (sleep 10s; echo hi) in the background. It seems the "gksu" was the problem all along. According to your explanation, which makes sense to me, in this case, Shell_1 should have stopped at "sudo $0 $*" and waited for Shell_2 to return, should it not?
hi
i guess your problem is --> if you run a shell script in the background then the STDIN is closed by default.
ciao

---

### Post by geirha on 2010-09-07
```
help test
```
What does -s do?

I recommend reading [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) to learn bash. It also teaches good practice.

---

### Post by terminator14 on 2010-09-08
> **geirha said:**
> ```
help test
```
What does -s do?

I recommend reading [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) to learn bash. It also teaches good practice.

Seeing as how `help test` would give you the answer to your own question, I assume your question is rhetorical. -s is mean to check that a file exists and is not empty. $DISPLAY will either show you nothing (in the case where X server is not running) or something similar to ":0.0" if it is. Although I admit I do not fully understand how -s in this case would apply as "" is not a file of any length, this code was recommended by [this post here]("http://www.linuxquestions.org/questions/programming-9/find-out-if-x11-is-running-from-within-perl-or-bash-script-796085/#post4017665") and seems to work on my machine in both cases. Are you implying there is a problem with it?

In any case, the test of the $DISPLAY variable is not the issue here since, whether by coincidence or not, the test works. The problem is the fact that if the script launches itself using gksu, it stops running jobs in the background, even if 'exec' is used.

---

### Post by geirha on 2010-09-08
Oh, I see! It works by accident. You used [ instead of [[ AND didn't quote the variable. If DISPLAY is empty, [ -s $DISPLAY ] becomes [ -s ], only one argument (not counting the mandatory, closing ]), which is basicly the same as [ -n -s ]; it tests whether the string "-s" is non-empty (which it is).

Anyway, the correct way to check if the DISPLAY variable is not set or empty, is [[ -z $DISPLAY ]] or [[ ! $DISPLAY ]]  (note that with [[ you don't need to quote that variable because bash won't do word-splitting or globbing in that case.)

[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

Anyway, use gksudo instead of gksu, and you want "$@" instead of $*, and quotes around $0.

```

if ((EUID != 0)); then
    if [[ $DISPLAY ]]; then
        gksudo "$0" "$@"
    else
        sudo "$0" "$@"
    fi
fi

```

Also note that relying on $0 like that is not safe.

[http://mywiki.wooledge.org/BashFAQ/028](http://mywiki.wooledge.org/BashFAQ/028)

---

### Post by terminator14 on 2010-09-14
> **geirha said:**
> Oh, I see! It works by accident. You used [ instead of [[ AND didn't quote the variable. If DISPLAY is empty, [ -s $DISPLAY ] becomes [ -s ], only one argument (not counting the mandatory, closing ]), which is basicly the same as [ -n -s ]; it tests whether the string "-s" is non-empty (which it is).

Anyway, the correct way to check if the DISPLAY variable is not set or empty, is [[ -z $DISPLAY ]] or [[ ! $DISPLAY ]]  (note that with [[ you don't need to quote that variable because bash won't do word-splitting or globbing in that case.)

[http://mywiki.wooledge.org/BashFAQ/031](http://mywiki.wooledge.org/BashFAQ/031)

Anyway, use gksudo instead of gksu, and you want "$@" instead of $*, and quotes around $0.

```

if ((EUID != 0)); then
    if [[ $DISPLAY ]]; then
        gksudo "$0" "$@"
    else
        sudo "$0" "$@"
    fi
fi

```

Also note that relying on $0 like that is not safe.

[http://mywiki.wooledge.org/BashFAQ/028](http://mywiki.wooledge.org/BashFAQ/028)

This experiences the exact same problem. First, if you don't include the "exit "$?"" inside the EUID if statement, the script runs twice. Second, in the exact same way as the examples above, if you launch it with "sudo ./test.sh", it works as it should. If you don't, and it tries to run the gksudo command, it stays frozen, waiting for the background execution commands to finish before releasing the console. Here's an example of a script implementing your method:

```
#!/bin/bash
if ((EUID != 0)); then
    echo "This script can only be run or configured by root. Proceeding to run script as root."

    if [[ $DISPLAY ]]; then
        gksudo "$0" "$@"
    else
        sudo "$0" "$@"
    fi
    exit "$?"
fi

(sleep 10s; echo hi) &

```

Try to run it as ./test.sh (no sudo) and see if it releases the console right away. It doesn't.

---

### Post by geirha on 2010-09-14
Err, right, I intended to use exec, in which case the exit would be unnecessary, but I forgot either. 

Anyway, I do see what you mean now. gksudo is waiting for all children to complete, while sudo doesn't. I guess your best option to get around that is to run the background job with nohup.

```
nohup bash -c 'sleep 10; echo hi' >/dev/null 2>&1 &
```

---

### Post by terminator14 on 2010-09-16
> **geirha said:**
> ```
nohup bash -c 'sleep 10; echo hi' >/dev/null 2>&1 &
```

This comes close to working, as it no longer gets hung up on that line. Unfortunately when trying to implement this, as in the following code, more problems become apparent:

```
#!/bin/bash
if ((EUID != 0)); then
    echo "This script can only be run or configured by root. Proceeding to run script as root."

    if [[ $DISPLAY ]]; then
        gksudo "$0" "$@"
    else
        sudo "$0" "$@"
    fi
    exit "$?"
fi

echo -n "Hi. What's your name?: "
read NAME
echo "Hi $NAME"
nohup bash -c 'sleep 10' >/dev/null 2>&1 &

```

When running the script as ./test.sh, the script will hang on the "read NAME" line. The strange thing is that this only happens if your sudo timeout hasn't expired yet. If you run "sudo -k" to force it to expire and run ./test.sh again, the gksudo popup will appear, and once you enter the password, the "read NAME" line is skipped altogether - the script doesn't pause at that line at all for you to enter input.

---

