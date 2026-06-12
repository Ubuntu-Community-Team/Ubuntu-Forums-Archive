---
title: "Question about Bash Scripting &amp; Integers"
date: 2012-08-08
forum: Programming Talk
---

### Post by gigant0r on 2012-08-08
Hi,

Thanks for looking at my question! :)

So, I know that Bash is an untyped system, and I was playing around with a script to switch VT's (I know I can use the CTRL ALT's, but it was more of " i'm bored lets try something.." )

Below is the script:

```
currentterm=$(fgconsole)
echo "Your Current Console is ${currentterm}"
echo " "
echo " "
echo " Which Console Would You Like To Teleport Two? : "
read connum
echo " "
echo "Very Well... Gating to ${connum}"
declare -i param
param=connum

chvt ${param}
```The script works fine, but when I first wrote it, I was trying to do a chvt ${connum} which would result in a command error, as it received a string.  Now I know that bash is an untyped language for the most part, so I did a declare -i connum initially after that which didn't change anything.  I finally fixed the problem by swapping the value to an already declared integer value param, as seen in the code above.

My question is, is this the most efficient way to solve this, or is there another?  I've been working on scripting more lately, because I feel it is an area I'm not the best in.  So any information you can give me would be helpful.

Thanks in advance! :)

---

### Post by Vaphell on 2012-08-08
```
read -p "console number: " connum
chvt $connum
```

works for me
your code on the other hand should not
```
param=connum
```
param value is 'connum' string, not value of connum variable ($connum)

---

### Post by gigant0r on 2012-08-09
Thanks for the quick reply!

I switched out my code with yours and it worked.
When I did the chvt I had the curly brackets around my original parameter ${connum} I saw that you just used {connum} is there a difference?

Thanks!!

---

### Post by Vaphell on 2012-08-09
there is no difference, though {} help to get rid of ambiguosity and are required if you use features of parameter expansion

*text${a}text* requires {} otherwise shell assumes $atext not $a
*${a//X/Y}* value of a with all X replaced by Y. There are more cool things you can do with parameter value.

[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

---

### Post by gigant0r on 2012-08-09
Wow thanks again, and especially for the link - I'm going to play with that this afternoon :)

---

