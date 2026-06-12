---
title: "bash for range variables plz help"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-06-04
im trying to make a shell script that makes us of a for loop range but i cant seem to work variables into the range. here's what i have:

```

echo from:
read -a from
echo to:
read -a to
for i in {$from..$to}
do
   echo $i
done

```

for the output i  get "from..to" with from and to replaced with the numbers i put in which would be the same thing as "echo $from..$to". it seems to be ignoring the for part and just setting the variable. what am i doing wrong? TIA

---

### Post by codemaniac on 2012-06-04
> **z3nhakr said:**
> im trying to make a shell script that makes us of a for loop range but i cant seem to work variables into the range. here's what i have:

```

echo from:
read -a from
echo to:
read -a to
for i in {$from..$to}
do
   echo $i
done

```

for the output i  get "from..to" with from and to replaced with the numbers i put in which would be the same thing as "echo $from..$to". it seems to be ignoring the for part and just setting the variable. what am i doing wrong? TIA
Try the below 
```
echo from:
read -a from
echo to:
read -a to
for i in `seq $from $to`
do
   echo $i
done
```

---

### Post by z3nhakr on 2012-06-04
heyhey it works! i was trying to avoid this because i read it was outdated. is that so?
[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

---

### Post by codemaniac on 2012-06-04
> **z3nhakr said:**
> heyhey it works! i was trying to avoid this because i read it was outdated. is that so?
[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)

There are also alternative options available in bash which lets you iterate through a range of numbers .
C style for loop .  


```
for ((i=$from;i<=$to;i++))
do
        echo $i
done
```

---

