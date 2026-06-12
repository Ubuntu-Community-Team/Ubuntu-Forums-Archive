---
title: "If then else fi...."
date: 2010-09-04
forum: Programming Talk
---

### Post by jv2112 on 2010-09-04
I am trying to learn if then statements and I have been having issues if the logic goes beyond one If then. See line 46 below. I keep getting these errors with this type of syntax.

Any ideas ? ](*,)



> 

#! /bin/bash

# Tux Box summary

TITLE="$HOSTNAME Status"

CURRENT_TIME=$(date +"%x %r")

TIME_STAMP="Generated $CURRENT_TIME, by $USER"

echo $TITLE

echo "***********************************************************************" 

echo $TIME_STAMP

echo "***********************************************************************"

uptime

echo "***********************************************************************"

df -hTl --total

echo "***********************************************************************"

echo "Home ->"

du -sch ~joe

sleep 10s

echo " Do you want monitor the system ?"
read  htop

if [ $htop = yes ] ; then

htop

fi

if [ $htop != no ] then 

echo  " You Idiot---> It was a yes or no question."

fi   # Error ---->line 46: syntax error near unexpected token `fi'

else

echo "Have a nice day, $USER "

echo "Have a nice day $USER " | espeak 2> /dev/null


fi




---

### Post by davidmohammed on 2010-09-04
```
if [ $htop != no ]**_ ;_** then 

echo " You Idiot---> It was a yes or no question."

**#fi # Error ---->line 46: syntax error near unexpected token `fi'**

else

echo "Have a nice day, $USER "

echo "Have a nice day $USER " | espeak 2> /dev/null


fi
```

---

### Post by GregBrannon on 2010-09-04
You'll get a better response to these kind of questions in the Programming Talk forum.

---

### Post by lisati on 2010-09-04
Moved to "Programming Talk"

Someone who is more skilled in writing shell scripts than myself might see this thread and be able to suggest something.

---

### Post by Galher on 2010-09-04
your mistake is prety obvious. 
it's before line 46.
spent a couple of minutes and you will have the satisfaction of finding it yourself. ;)

---

### Post by jv2112 on 2010-09-04
Thanks  :):guitar:


](*,)  ---- I should have proofed it closer... Couldn't see the forest through the tress..........

---

### Post by Vox754 on 2010-09-04
> **jv2112 said:**
> Thanks  :):guitar:


](*,)  ---- I should have proofed it closer... Couldn't see the forest through the tress..........

By the way, a lot of people think the semicolon (;) after the condition and before "then" is magic, and it just needs to be there:
```

if [ "$bla" != "no" ] ; then
    echo "Yes"
fi

```

It's not like that. The semicolon is used to terminate the current list of commands, and therefore is the same as using a line break.

The code can be written like this:
```

if [ "$bla" != "no" ]
then
    echo "Yes"
fi

```

Which in my opinion is clearer and it avoids silly errors like the one presented in this thread.

However, the former way is deeply rooted in bash scripting tradition, so it's used everywhere without explanation.

---

### Post by jv2112 on 2010-09-05
So "we always did it that way....... "


Plenty of that going on in this world. 


Thanks for the input.

---

