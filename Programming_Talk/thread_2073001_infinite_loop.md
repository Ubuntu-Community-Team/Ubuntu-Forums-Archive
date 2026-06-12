---
title: "infinite loop"
date: 2012-10-18
forum: Programming Talk
---

### Post by sunnypt on 2012-10-18
so i'm trying to make a script that asks my name right?
so i have this: 

#!/bin/bash

echo -n  "Please enter your forum name: "
read fname
if [ $fname = "quit" ]; then echo "bye! "
exit
fi
while [ $fname= ]; do
      echo "please insert at least 1 character"
done

so if i don't enter anything, it goes to an endless loop. what i want the script to do  is to go back to this part if i don't put any character there
echo -n  "Please enter your forum name: "
read fname

any help?

---

### Post by drmrgd on 2012-10-18
There's a few things going on there.  But, the first one to look at is your 'while' statement.  I think you want to test for a null string, which uses the '-z' test:

```
while [ -z $fname ]; do
    echo "Please insert at least 1 character"
```

See this for more bash test operators:

[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

That still is not going to fix the problem however,  if $fname is indeed null, then the loop will execute.  However you've given it no place to go.  There's no way for the user to correct their mistake and enter a value for $fname, so the loop just keeps cycling.  You need to give the loop a way out :P

EDIT:  Oh, I also forgot to comment on your first conditional statement.  You've made a classic mistake there and used an assignment operator when you meant to use a test operator.  So, you need to change the statement to be:

```
if [ $fname == "quit" ]; then
    echo "bye!"
    exit
if
```

You also made the same mistake in your second test (the 'while' loop).

---

### Post by pqwoerituytrueiwoq on 2012-10-18
```
while [  -z "$name" ];do
echo "Please enter your forum name: "
read name
if [ "$name" == "quit" ];then # what if there name really is quit?
echo "Bye"
break;
elif [ -z "$name" ];then
clear
echo "If you don't have a name type 'quit' to exit, otherwise..."
fi
done
```

---

### Post by sunnypt on 2012-10-18
> **pqwoerituytrueiwoq said:**
> ```
while [  -z "$name" ];do
echo "Please enter your forum name: "
read name
if [ "$name" == "quit" ];then # what if there name really is quit?
echo "Bye"
break;
elif [ -z "$name" ];then
clear
echo "If you don't have a name type 'quit' to exit, otherwise..."
fi
done
```

ok that works! but i don't understand how..  which line says when to go back to the start when $name is null? and, can i apply these in the middle of a script? like if i have a longer script and wanna do this bit, will it restart the whole script?

---

### Post by Vaphell on 2012-10-19
it's a *while* loop that goes as long as the value is null and repeats everything. When the value provided is 'quit', script goes into a subroutine where *break* is. *Break* makes the instant jump out of the loop 

```
**while [  -z "$name" ];do**
  echo "Please enter your forum name: "
  read name
  **if [ "$name" == "quit" ];then** # what if there name really is quit?
    echo "Bye"
    **break;**
  elif [ -z "$name" ];then
    clear
    echo "If you don't have a name type 'quit' to exit, otherwise..."
  fi
**done**
# break? jump here>

```

there is also *continue* that ends the current run of the loop and starts another one from the top
example showcasing it:
```
while [  -z "$name" ]; do
  echo "from the top"
  continue
  echo "Please enter your forum name: "
  read name
done

--------
from the top
from the top
from the top
...

```
that would be an infinite loop because *continue* would prevent the script from ever reaching *read name* part

---

### Post by sunnypt on 2012-10-19
[QUOTE=Vaphell;12304215]it's a *while* loop that goes as long as the value is null and repeats everything. When the value provided is 'quit', script goes into a subroutine where *break* is. *Break* makes the instant jump out of the loop 

[code]**while [  -z "$name" ];do**
  echo "Please enter your forum name: "
  read name
  **if [ "$name" == "quit" ];then** # what if there name really is quit?
    echo "Bye"
    **break;**
  elif [ -z "$name" ];then
    clear
    echo "If you don't have a name type 'quit' to exit, otherwise..."
  fi
**done**
# break? jump here>
 
hm i think i'm starting to get it, so the elif statement and the break statement make the loop go back to the start right?

---

### Post by Habitual on 2012-10-19
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by Vaphell on 2012-10-19
```
if [ "$name" == "quit" ]; then # what if there name really is quit?
```
you got a problem. Design your script better

> so the elif statement and the break statement make the loop go back to the start right?

not really, break and elif are 2 different branches, they will never be executed together (if something break; else if something_else ...).
loop run goes from **while do** to **done** by itself, once done is reached, script jumps back to **while do** again and redoes everything if the main condition of the loop is true. That's the default behavior. You can influence it with continue and break
**continue** = jump to **while do** and start another loop run if test is true
**break** = leave loop permanently


besides, shouldn't that **break** be replaced with **exit**? you want to end the script, not jump out of the loop to continue the script (logically quit and proper name will do the same thing, get past the while loop with non-empty $name)

---

### Post by sunnypt on 2012-10-19
> **Habitual said:**
> [http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://tldp.org/LDP/abs/abs-guide.pdf](http://tldp.org/LDP/abs/abs-guide.pdf)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

cheers for that :) but i think i might need to understand th command line a bit better, all the commands and all the command extensions and stuff. can someone point me a nice guide for that?

---

### Post by PatrickD-52761 on 2012-10-19
> **sunnypt said:**
> [QUOTE=Vaphell;12304215]it's a *while* loop that goes as long as the value is null and repeats everything. When the value provided is 'quit', script goes into a subroutine where *break* is. *Break* makes the instant jump out of the loop 

[code]**while [  -z "$name" ];do**
  echo "Please enter your forum name: "
  read name
  **if [ "$name" == "quit" ];then** # what if there name really is quit?
    echo "Bye"
    **break;**
  elif [ -z "$name" ];then
    clear
    echo "If you don't have a name type 'quit' to exit, otherwise..."
  fi
**done**
# break? jump here>
 
hm i think i'm starting to get it, so the elif statement and the break statement make the loop go back to the start right?

I'll take a stab at this (the explanation).

The while runs if $name is null (or empty).
The first thing it does is prompt for a name.
Then it reads the response.
It checks if the response is "quit" and if so, it echos "Bye" and then breaks out of the while loop, going to the first line AFTER done.
If the response is not "quit", it clears $name (returns it to null), and prompts them.
It hits the "done" line, and returns to the original "while" line. Because you cleared the name, it goes into the while loop again.

So, it's the elif and **clear** statements that make the while loop run again. The break statement jumps you out of the while loop and goes on to the first statement after the loop.

Also to answer one of your other questions, if you put this into a larger script, the only thing that will repeat is everything inside of the while loop. Unless you do something that causes the entire script to repeat.

Hope this helps clear things up.

Have a great day:)
Patrick.

---

