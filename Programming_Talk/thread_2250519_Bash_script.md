---
title: "Bash script"
date: 2014-10-29
forum: Programming Talk
---

### Post by anakin2 on 2014-10-29
Hi all;
when I write this bash code, I face invalid arithmetic operator error in second if. I can't see any problem in code!
please help me as soon as possible.
Thanks in advance

```

#!/bin/bash

printf " MEASURE_COUNT\\BLOCK_SIZE BLOCK_SIZE=2\t  BLOCK_SIZE=4\t  BLOCK_SIZE=8\t  BLOCK_SIZE=16\n"
TIME1=0 
TIMEOPT=200
BSOPT=0
for((i=2**2;i<2**5;i=i*2));do
printf "\t$i\t"
for((j=2;j<=16;j=j*2));do
g++ -std=c++11 -O2 -D MEASURE_ON -D MEASURE_BLOKSIZE=2 -D MEASURE_COUNT=$i msort_time.cpp
TIME1=$(./a.out)
printf "\t\t$TIME1"
if((i==2**4));then
if(( TIMEOPT>TIME1));then
TIMEOPT=$TIME1
BSOPT=$j
fi
fi
done
printf "\n"
done
```

---

### Post by Vaphell on 2014-10-29
the exact error message would be nice. What does a.out spit out? Maybe it's some float?

---

### Post by anakin2 on 2014-10-29
yes it is float! problem is for that?? this is complete message:

0.0009./autotune.bash: line 14: ((: 0.0009: syntax error: invalid arithmetic operator (error token is ".0009")
        0.0011./autotune.bash: line 14: ((: 0.0011: syntax error: invalid arithmetic operator (error token is ".0011")
        0.0009./autotune.bash: line 14: ((: 0.0009: syntax error: invalid arithmetic operator (error token is ".0009")
        0.0011./autotune.bash: line 14: ((: 0.0011: syntax error: invalid arithmetic operator (error token is ".0011")

---

### Post by Vaphell on 2014-10-29
yes, sadly (( )) are integer based math only. 

you could try bringing the numbers to the integer realm for comparisons and stuff with little hacks (are these numbers of fixed precision?) or outsource the task to awk who does all kinds of math.

can you explain the logic related to timeopt and bsopt?

---

### Post by anakin2 on 2014-10-29
thank you. now how should i compare them?? yes they are fixed precision.
the code wants to print the time taking to run for different special variable ( block size),
and finding best block size from best time.

---

### Post by Vaphell on 2014-10-29
yes, sadly (( )) are integer based math only. 

you could try bringing the numbers to the integer realm for comparisons and stuff with little hacks (are these numbers of fixed precision?) or outsource the task to awk which does all kinds of math.

example of scaling the number up in pure bash
```
$ float2int() { local int p; p=${1#*.}; p=${#p}; int=${1%.*}; int=$(( int*(10**p)+10#${1#*.} )); echo $int $p; }
$ float2int 0.0011
11 4
$ read int prec < <( float2int 0.0011 )
$ echo "$int*10^(-$prec)"
11*10^(-4)
```

can you explain the logic related to timeopt and bsopt?

---

### Post by anakin2 on 2014-10-29
bsopt is best block size and timeopt is best time. I don't get the code you write...

---

### Post by anakin2 on 2014-10-29
I found answer I should use bc. Thank you.

---

