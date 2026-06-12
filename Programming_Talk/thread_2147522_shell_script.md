---
title: "shell script"
date: 2013-05-22
forum: Programming Talk
---

### Post by Rahul04789 on 2013-05-22
Hi Friends,
This is my first unix programme, but I am facing some syntax error. Please tell me where am I making mistake in this code.
Following is the same code which I am trying to run:

echo "This is my first shell programe"
a=1 
c=`ls /media/ | wc -l`
while [ $a -eq 1 ]
do
   echo " System is checking the /media/ folder"
   b= `ls /media/ | wc -l`
if [ $c -ne $b ]  then
echo "a new device found"
$a= ` expr $a + 1 `
fi
done
if [ $c -eq $b ] then
   echo "no new device found"
fi  


I am getting the following syntax error:

[B]./pendrive.sh: line 11: syntax error near unexpected token `fi'
./pendrive.sh: line 11: `fi'


[/B]

---

### Post by Impavidus on 2013-05-22
If you put "then" on the same line as "if" you have to put a ; inbetween. Else move "then" to the next line.
```

if [test]; then
#or
if [test]
then

```

Besides, the last if statement will never be true. Have you found some good guide on the basics of shell scripting?

---

### Post by mörgæs on 2013-05-22
Please keep only one topic in each thread. 
I have moved your posts to Programming Talk.

---

### Post by Rahul04789 on 2013-05-22
echo "This is my first shell programe"
a=1 
c=`ls /media/ | wc -l`
while [ $a -eq 1 ]
do
   echo " System is checking the /media/ folder"
   b= `ls /media/ | wc -l`
if [ $c -ne $b ]; then
echo "a new device found"
$a= ` expr $a + 1 `
fi
done
if [ $c -eq $b ]; then
   echo "no new device found"
fi

error:
 ./pendrive.sh: line 7: 1: command not found
./pendrive.sh: line 8: [: 1: unary operator expected

Still now the above problem occurs.

---

### Post by schragge on 2013-05-22
> **Rahul04789 said:**
> error:
 ./pendrive.sh: line 7: 1: command not found
Remove the space after =
```
b=[highlight][COLOR=#ffd700]_[/COLOR][/highlight]`ls /media/ | wc -l`
```

---

### Post by prodigy_ on 2013-05-22
Is that just for practice or are you going to use the script? For the latter you should consider making some changes:
1) If you're actually looking for *devices*, you should monitor the contents of **/dev** folder (or, even better, use something like **sudo lshw -short -C disk**).
2) If you're looking for newly mounted *file systems*, you could use check **/proc/mounts** file.
3) A loop running continuously without pauses can eat a lot of resources needlessly. You can add **sleep** to mitigate that.

Example:```

#!/bin/bash

i=$(wc -l /proc/mounts | cut -d' ' -f1) # get newlines count from /proc/mounts and assign to $i variable 
while :; do
	sleep 1 # pause for 1 second
	j=$(wc -l /proc/mounts | cut -d' ' -f1)
	[ $j -gt $i ] && echo "Found new mounted filesystem"
	i=$j
done
```
Now, this is still far from perfect (as it's open to race conditions and whatnot) but it'll work most of the time.

---

### Post by Vaphell on 2013-05-22
**$a**= ` expr $a + 1 `

that doesn't look good either

```
           **no spaces here --v**
assignment  *        [COLOR="#006400"]leftside[/COLOR]**=**[COLOR="#0000FF"]rightside[/COLOR]*
   [COLOR="#006400"]<< **$ not on this side** << **[/COLOR]|[COLOR="#0000FF"]** >> **$ on this side** >>[/COLOR]
```

when you see $X think 'get value of X' - that will make it obvious that $X=abc (assign abc to value of X?) doesn't make sense, but abc=$X does (assign value of X to abc).

also forget about **``** and use **$( )** instead, you still have time to save your soul ;-) $( ) does the same but is 10x more readable (no doubt which part opens and which part closes, which can't be said about `` eg `a`b`c`d`e`f`g`) and can't be mistaken for a single quote at a glance.

If you are going to use bash to write your scripts, you can use its **(())** to do the integer math
*a=$( expr $a+1 )* is equivalent to *(( a=a+1 ))* or *(( a++ )) or a=$(( a+1 ))*

---

### Post by Rahul04789 on 2013-05-30
Hey thank u,  got my problem solved.

---

