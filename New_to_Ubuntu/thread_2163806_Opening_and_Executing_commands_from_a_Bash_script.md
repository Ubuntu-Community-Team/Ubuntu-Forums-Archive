---
title: "Opening and Executing commands from a Bash script"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by Cl1ck on 2013-07-19
This is my first post/thread, and I have a quick, and relatively trivial question. I want to open say, 3 different terminals, and have them all execute commands.
Here is an example code, not the REAL code, but close. Now if I put -hold, then it will wait till each process finishes, and then waits for you to exit the terminal, and opens another one, and so on, how would I get it for them all to run simultaneously.
```

#!/bin/bash
PATH=$PATH:/bin/bash
$num
num=1
$pwin
pwin=1
while [ $pwin -lt 4 ] 
do
    xterm  -e tree 
pwin=$(($pwin+$num))
done 

```
I'm not running this on Ubuntu, but that's not important.

---

### Post by Cl1ck on 2013-07-19
I know my code isn't very orthodox, but it's my own style.

---

### Post by steeldriver on 2013-07-19
Hello and welcome to the forum

Try backgrounding each terminal as you launch it i.e.

```
xterm -e tree [COLOR=#0000ff]**&**[/COLOR]
```

Otherwise, I think the shell will wait for control to return from each xterm before continuing

---

### Post by Cl1ck on 2013-07-19
No, that just waits for each process to complete before it opens the next one.
I am very new to Linux(installed yesterday..), could you explain what '&' does, I have a backround in C++ and Powershell, but not Linux.

---

### Post by sudodus on 2013-07-19
Welcome to the Ubuntu Forums :-)

1. As *steeldriver* wrote, add an ampersand, ***&,*** after the xterm command line. It will detach the command from the script, and the script will continue without waiting for you to stop xterm.

```
 xterm -hold -e tree &
```

so the script can start several processes that will run at the same time.

2. I think you should remove the PATH=... command line. PATH is listing the ***directories***, where to search for executable files (binary programs and scripts). /bin/bash is the ***file*** for the shell program and does not belong in PATH.

---

### Post by Cl1ck on 2013-07-19
That works, thanks, now how would I use xterm -hold -e [command] &,
but have switches, for example.
```

ls -a
```
Would I just do ```
 xterm -hold -e ls -a &
```?
Because I don't think that will work.

---

### Post by Cl1ck on 2013-07-19
Nevermind, I tried it, and it worked, thanks for your help.

---

### Post by sudodus on 2013-07-19
Success :KS

That the way to do it: dare try :-) *Edit*: and take regular ***backup*** of your important files (if you try too much ...)

Now please edit your first post in the thread, go advanced and change the [prefix] to SOLVED

---

### Post by Cl1ck on 2013-07-19
No problem, will do, thanks for your help.

---

