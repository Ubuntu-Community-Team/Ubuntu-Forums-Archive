---
title: "basic script"
date: 2013-10-09
forum: Programming Talk
---

### Post by TeDeJeM on 2013-10-09
Hello. Today at job interview I had to explain what the following script does and how I can improve it. I still have to return the answer to them. Would deeply appreciate any help and even explanation on what every command does.

#!/bin/bash


declare -i I=0
declare -i C=${I}
declare -i M=${I}


cat file.txt | while read C; do
	if [ ${C} -gt ${M} ]; then
		M=$((C));
	fi;
done;


echo ${M}

---

### Post by alan9800 on 2013-10-09
the first line of your script sets I (uppercase i) to 0 (zero); the second and the third lines do the same, but using the value of I instead of setting directly these variables to 0.
The fourth line creates a pipe for reading the file called "file.txt" and for storing its values into C.
The lines from the fifth to the eighth make a test between the values of C and M; if C is greater than M, then M is set to the value of C.
The ninth line shows the value of M.
The script has the purpose of setting M to the smallest value contained in the file called "file.txt".

---

### Post by Vaphell on 2013-10-09
i'd say it looks for the max value not for the min value given c>m => m=c

as for possible improvements:
- unnecessary use of cat, overhead of external commands is a waste if the built-in mechanism exists.  The kosher way of reading files line by line is *while read ...; do ...; done **< file***
- whole if replaced by something like *((C>M)) && ((M=C))* or by *(( M=(C>M?C:M)))*
   --- integer mode of (()) is better for math logic than []
   --- && part is executed only if the preceding expression returns success
   --- it's possible to assign values inside (()) and the ternary operator ?: can be used to achieve the desired effect in one go

---

### Post by apmcd47 on 2013-10-09
Should we be helping with what is essentially homework?

What has not been pointed out yet is the pipe causes the "while ... done" to be executed in a subshell. Regardless of the value of $M at the end of the loop, the value emitted by the code is always 0.

There are two smart-alec answers you can give, one based on the actual output of the original script, and the other using sort. I will let you figure them out yourself; I assume you have access to a bash shell as you are posting to this forum.

I would also make the modifications as per Vaphell's suggestions and tell them why the sort is better than the script.

Andrew

---

### Post by alan9800 on 2013-10-09
> **Vaphell said:**
> i'd say it looks for the max value not for the min value given c>m => m=cyou're right.
I've made confusion while reading the fifth line of the script.
My apologies to the OP for my mistake.

---

### Post by Vaphell on 2013-10-09
> **apmcd47 said:**
> What has not been pointed out yet is the pipe causes the "while ... done" to be executed in a subshell. Regardless of the value of $M at the end of the loop, the value emitted by the code is always 0.

lol true, i wrote about the unnecessary cat right off the bat without looking at the loop body, but then i tested various approaches of compression of the if in a terminal with *done < file* (because i never pipe to while loops) and forgot to mention the subshell issue completely :)

---

### Post by TeDeJeM on 2013-10-10
Truly appreciate your attention guys to this post. Cheers,

---

