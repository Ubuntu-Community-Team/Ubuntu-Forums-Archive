---
title: "Loops with .sh"
date: 2010-11-06
forum: Programming Talk
---

### Post by Reddoug on 2010-11-06
Hi All

Trying to figure out how I can accomplish this. What I have will put out N is 1 through 99.  Have been trying to find something similar and try and figure this out without any luck. 

Thanks, Doug  



#!/bin/sh
echo -n "Try and guess a number between 1 and 99"
echo -n "Enter a number:      "
read number
N=1
while [ "$N" -le 99 ] 
do
   echo N is $N
   N=`expr $N + 1`
done

---

### Post by Arndt on 2010-11-06
> **Reddoug said:**
> Hi All

Trying to figure out how I can accomplish this. What I have will put out N is 1 through 99.  Have been trying to find something similar and try and figure this out without any luck. 

Thanks, Doug  



#!/bin/sh
echo -n "Try and guess a number between 1 and 99"
echo -n "Enter a number:      "
read number
N=1
while [ "$N" -le 99 ] 
do
   echo N is $N
   N=`expr $N + 1`
done

What is it that you want to do?

---

### Post by Reddoug on 2010-11-07
Hi
I am wanting to guess a number between 1 and 99. Tell the player they are to low or high or correct. I have been reading different books but can not figure out about to high or low.  

Thanks, Doug

---

### Post by Arndt on 2010-11-07
> **Reddoug said:**
> Hi
I am wanting to guess a number between 1 and 99. Tell the player they are to low or high or correct. I have been reading different books but can not figure out about to high or low.  

Thanks, Doug

I suggest you write some pseudocode first, that simply expresses the logic, and then put it into a particular language, sh in this case. Pseudocode can look any way you want, as long as it expresses what you want.

You have one number X which is the number to guess, and a number Y which the user inputs as a guess, and which varies. The program compares X and Y and says whether Y is high or low, and then reads a new Y.

How is X generated to begin with?

What books did you read on the subjects?

---

### Post by Crazedpsyc on 2010-11-07
I suggest this method to get a random number:
```
[FONT=monospace]
[/FONT]RANGE=[FONT=monospace]99
[/FONT]echo[FONT=monospace]
[/FONT]number=$RANDOM[FONT=monospace]
[/FONT]let "number %= $RANGE"[FONT=monospace]
[/FONT]echo "$number"

```
Put that in your while loop to generate a random number from 1 to 99 each time

---

### Post by Reddoug on 2010-11-07
Linux Pocket Guide, Classic Shell Scripting, and Unix & Linux are books I have been reading. I will try the suggestions.

Thanks, Doug

---

### Post by Reddoug on 2010-11-09
Hi

Found a random number generator to generate two digit number.

RANDOM=`date+%N \ cut -c8-`

Thanks, Doug

---

