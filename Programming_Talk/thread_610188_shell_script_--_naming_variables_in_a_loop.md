---
title: "shell script -- naming variables in a loop?"
date: 2007-11-11
forum: Programming Talk
---

### Post by totalnub on 2007-11-11
hey guys, just had some quick questions about variable naming....

i'm trying to parse a datafile and store the elements into variable names.

Main.dat contains lines of data entries separated by a non-constant whitespace

here's my code:

```

lines=`wc -l Main.dat | cut -f 1 -d ' '`
echo $lines
counter=1

while [ $counter -le $lines ]
do
eval word$counter=`cut -f 1 -d ' ' Main.dat | head -n $counter | tail -n 1`
echo \$word$counter
counter=`expr $counter + 1`
done

```

the problem is that when i run that part of the script, i cannot access the variables that i've created. ie word1, word2, word3, word4, word5

the echo \$word$counter part will echo
$word1
$word2
$word3
$word4
$word5

but if i remove the leading \ all i get is the value for $counter
1
2
3
4
5

i can't find a way to access the variable

any ideas?

---

### Post by kast on 2007-11-11
Have you tryd quoting your VAR in the expr
[B]```

counter=`expr "$counter" + 1`
```[/B]

---

### Post by kast on 2007-11-11
Oh also run you script for debug
[B]
sh -x script[/B]

and post that back

---

### Post by kast on 2007-11-11
Sorry for the three posts before your response!  but you should also quote your VAR in your test strings

[B]```
lines=`wc -l Main.dat | cut -f 1 -d ' '`
echo $lines
counter=1

while [ "$counter" -le "$lines" ]
do
eval word$counter=`cut -f 1 -d ' ' Main.dat | head -n $counter | tail -n 1`
echo \$word$counter
counter=`expr $counter + 1`
done
```[/B]

Now not sure any of that will make the differance, but I will wait now for your reply :)

---

### Post by totalnub on 2007-11-11
well, counter will update, it's just that the variable $word$counter cant be printed....

i shortened the loop, but you get the idea
```

 ./myacct
+ set -v on
lines=`wc -l Main.dat | cut -f 1 -d ' '`
+ wc -l Main.dat
+ cut -f 1 -d  
+ lines=5
echo $lines
+ echo 5
5
counter=4
+ counter=4

while [ $counter -le $lines ]
do




eval word$counter=`cut -f 1 -d ' ' Main.dat | head -n $counter | tail -n 1`
echo $word$counter

counter=`expr $counter + 1`
done
+ [ 4 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 4
+ tail -n 1
+ eval word4=Fruits
+ word4=Fruits
+ echo 4
4
+ expr 4 + 1
+ counter=5
+ [ 5 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 5
+ tail -n 1
+ eval word5=Tennis-racket
+ word5=Tennis-racket
+ echo 5
5
+ expr 5 + 1
+ counter=6
+ [ 6 -le 5 ]


```

---

### Post by totalnub on 2007-11-11
and here's the output with \$word$counter...
```

./myacct
+ set -v on
lines=`wc -l Main.dat | cut -f 1 -d ' '`
+ wc -l Main.dat
+ cut -f 1 -d  
+ lines=5
echo $lines
+ echo 5
5
counter=4
+ counter=4

while [ "$counter" -le "$lines" ]
do

eval word$counter=`cut -f 1 -d ' ' Main.dat | head -n $counter | tail -n 1`
echo \$word$counter

counter=`expr $counter + 1`
done
+ [ 4 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 4
+ tail -n 1
+ eval word4=Fruits
+ word4=Fruits
+ echo $word4
$word4
+ expr 4 + 1
+ counter=5
+ [ 5 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 5
+ tail -n 1
+ eval word5=Tennis-racket
+ word5=Tennis-racket
+ echo $word5
$word5
+ expr 5 + 1
+ counter=6
+ [ 6 -le 5 ]

```

---

### Post by kast on 2007-11-11
Copy and paste this into a  test script and tell me what it does when you run it.

[B]```
#!/bin/sh

lines=`wc -l Main.dat | cut -f 1 -d ' '`
echo $lines
counter=1

while [ "$counter" -le "$lines" ]
do
eval word"$counter"= `cut -f 1 -d ' ' Main.dat | head -n $counter | tail -n 1`
echo $word$counter
counter=`expr $counter + 1`
donee
```[/B]

---

### Post by kast on 2007-11-11
watch the typo on the **DONE** sorry.

---

### Post by totalnub on 2007-11-11
```
./shelltest
+ wc -l Main.dat
+ cut -f 1 -d  
+ lines=5
+ echo 5
5
+ counter=1
+ [ 1 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 1
+ tail -n 1
+ eval word1= Basketball
+ word1= Basketball
eval: 1: Basketball: not found
+ echo 1
1
+ expr 1 + 1
+ counter=2
+ [ 2 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 2
+ tail -n 1
+ eval word2= Candy
+ word2= Candy
eval: 1: Candy: not found
+ echo 2
2
+ expr 2 + 1
+ counter=3
+ [ 3 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 3
+ tail -n 1
+ eval word3= Car
+ word3= Car
eval: 1: Car: not found
+ echo 3
3
+ expr 3 + 1
+ counter=4
+ [ 4 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 4
+ tail -n 1
+ eval word4= Fruits
+ word4= Fruits
eval: 1: Fruits: not found
+ echo 4
4
+ expr 4 + 1
+ counter=5
+ [ 5 -le 5 ]
+ cut -f 1 -d   Main.dat
+ head -n 5
+ tail -n 1
+ eval word5= Tennis-racket
+ word5= Tennis-racket
eval: 1: Tennis-racket: not found
+ echo 5
5
+ expr 5 + 1
+ counter=6
+ [ 6 -le 5 ]

```


do you have aim/msn/yahoo? pm me if you do :)

---

### Post by kast on 2007-11-11
aim name is hatekast

---

### Post by kast on 2007-11-11
Still no luck! :)

---

### Post by pmasiar on 2007-11-12
You may want to parse the file in Python, and store lines in array. If file is big, dbm is very simple database (and included in core Python).

---

### Post by ghostdog74 on 2007-11-12
how does your main.dat look like, and what is the output format that you want.?

---

### Post by totalnub on 2007-11-12
the .dat file i'm attaching has 5 lines. the actual .dat file has an unknown number of lines separated by an unknown amount of whitespace. i have to have this strictly in shell, no python, (although that would be alot easier). 

here's the link:
[www.eng.fsu.edu/~bielacl/files/Main.dat](www.eng.fsu.edu/~bielacl/files/Main.dat)

thanks for the ideas and help :)
i'm too tired and need sleep

---

### Post by ghostdog74 on 2007-11-12
> **totalnub said:**
> the .dat file i'm attaching has 5 lines. the actual .dat file has an unknown number of lines separated by an unknown amount of whitespace. i have to have this strictly in shell, no python, (although that would be alot easier). 

here's the link:
[www.eng.fsu.edu/~bielacl/files/Main.dat](www.eng.fsu.edu/~bielacl/files/Main.dat)

thanks for the ideas and help :)
i'm too tired and need sleep

i had asked, what is the output format that you want to get from the 5 lines of sample file? 
ie.
input file  -----> shell script(black box) ------------> output

I am not asking about the black box part. I am asking about the output part

---

### Post by geirha on 2007-11-12
What is the intent of the script exactly? Bash has arrays btw, is the intent to do something like this?

```
#!/bin/bash
declare -a word
lines=`wc -l Main.dat | cut -f 1 -d ' '`
echo $lines

counter=1
for w in `cut -d' ' -f1 Main.dat`; do
    word[$counter]=$w
    echo ${word[$counter]}
    counter=$(($counter + 1))
done

```

---

### Post by totalnub on 2007-11-12
sorry about bailing out lastnight. the assignment was due late last night. but i still want to figure this out for my own knowledge.

the output really doesn't matter, but i have to put the files into their own .dat files based on the second field. i also need to be able to use flags that will output only selected fields (i.e. -p for price which is the last field would output the first field, for identification, and the last field)

my main concern was with getting the script to echo my variables using a counter variable as an index

gonna try what's suggested now

oh, and it has to all be in bourne shell....so no arrays

---

