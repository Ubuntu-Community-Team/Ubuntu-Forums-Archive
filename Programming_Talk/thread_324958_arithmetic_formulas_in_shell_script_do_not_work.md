---
title: "arithmetic formulas in shell script do not work?"
date: 2006-12-24
forum: Programming Talk
---

### Post by sgargabonzi on 2006-12-24
Hi guys,

I am a novice, but very glad with my first steps with Ubuntu.
I am following a beginner tutorial for script shell and I am using the Ctrl-Alt (F1 to F6) keys to have my prompt, and create files .sh.

First steps with "echo" ... so far so good.

Now I got stuck with calculating simple products like X*Y. I am trying many variations of the sintax but for example:

echo "I will work out X*Y"
echo "Enter X"
read X
echo "Enter Y"
read Y
echo "X*Y = $X*$Y = $[X*Y]"

prints me the actual string "$[X*Y]" and not its value (e.g. if X is 2 and Y is 3 I would expect to have "6" on the screen).

I tried with expr also but still no success. E.g. this script:

t= 'expr 7*4'
echo $t

just does not work. Also tried to use the escape "\" before the "*", but nothing..

Thank you very much in advance fellows!

---

### Post by Tomosaur on 2006-12-24
Try using the 'let' command:

```

let Z = "$X * $Y"

```
or something similar.
Type 'man let' into the terminal to check it out, since I can't remember the exact usage.

---

### Post by sgargabonzi on 2006-12-24
Thanks, I tried, but I guess the let command is not available with this Ubuntu distribution.

Typing 'man let' or also 'which let' is not giving me any result...

---

### Post by Tomosaur on 2006-12-24
Let is available, I've used it before. Perhaps you need to check repositories for it?

---

### Post by sgargabonzi on 2006-12-24
Can I ask you how to do that? I am definitely a beginner ...
I appreciate your help! Thanks...

---

### Post by rahufnagl on 2006-12-24
Try something similar to this...

```

echo `expr $x \* $y`

```

The backwards single quote, accent grave, is for command substitution, and the "\*" tells expr that it is multiplication, not a file matching metacharacter.

---

### Post by lloyd mcclendon on 2006-12-24
google for advanced bash scripting guide

look at the part on arithmetic expansion, $((x * y))

---

### Post by sgargabonzi on 2006-12-24
Hey guys,

it finally works, I used the normal single quote instead of the backwards single quote, so as rahufnagl suggested, the expression 

echo `expr $x \* $y`

is working fine.

Thank you all for the other suggestions!

---

