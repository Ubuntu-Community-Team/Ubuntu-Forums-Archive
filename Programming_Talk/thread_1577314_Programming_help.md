---
title: "Programming help"
date: 2010-09-18
forum: Programming Talk
---

### Post by Anthony_25802580 on 2010-09-18
Hey guys i am new to this website and i am jumping back into programming after taking a year off and i have a few stupid questions and was wondering if anyone could help me out

---

### Post by Darkness Des on 2010-09-18
Don't ask to ask questions, just ask! I promise, we don't bite. :)

---

### Post by davidmohammed on 2010-09-18
sure - but dont post in this forum - [try here]("http://ubuntuforums.org/forumdisplay.php?f=39") - more knowledgable guys can help you out.

---

### Post by lisati on 2010-09-18
Moved to "Programming Talk".

Fire away with the questions!

---

### Post by Anthony_25802580 on 2010-09-18
alright thanks guys! for every multiple of sixteen i want to add one to a variable. thats the best i can explain it. i thought about putting it in a if statement or for loop but i am a little stuck. havent programmed since nam.

---

### Post by schauerlich on 2010-09-18
Is that for every multiple of 16 in a given range? How many times a number is divisible by 16? etc.

---

### Post by worksofcraft on 2010-09-18
Do you mean something like...

```

int multiplesOf16inNumber = Number / 16;

Number = Number + multiplesOf16inNumber;

```

---

### Post by schauerlich on 2010-09-18
From my understanding it's something like this:

```
multiples_count = 0
for num in range(1, 100):
    if num % 16 == 0:
        multiples_count += 1
```

But it's not very clear what he means.

---

### Post by decoherence on 2010-09-18
As a bash script, with echoes added for illustration

```

counter=0
myvar=0
while true
   do counter=$((counter+1))
   echo "counter says "$counter
   if (( $counter % 16 == 0 ))
      then myvar=$((myvar+1))
      echo "variable says "$myvar
   fi
done
```

you need two variables, one to be a counter which increments with every loop, the other is the variable you're interested in (myvar) which only increments if the counter is divisible by 16. You didn't specify an exit condition so there isn't one.

---

### Post by Anthony_25802580 on 2010-09-18
That helps perfect. thanks a lot i will probably be posting things a lot until i get in the groove of things again.

---

