---
title: "Bash Programming For Loop and Parameters question"
date: 2009-07-17
forum: Programming Talk
---

### Post by tdrusk on 2009-07-17
I am trying to write a for loop that takes the parameters that the user inputs and adds them together. There is no limit to the amount of numbers the user is going to input.

So basically I want it to run like

```
addNumbers 6 4 3
13
```

I am having trouble with the addition part. I am doing
```
      8 x=0
      9 
     10 for count in $#
     11 do
     12         x=${count}+x
     13 done    
     14 echo $x
```

but I know it is wrong. Line 12 has the problem. How can I fix it to make it run?

---

### Post by c0mput3r_n3rD on 2009-07-17
```

#!/bin/bash

if [ $# = 0 ]
  then
      echo "Usage: $0 number-list"
fi
sum=0
count=0

while [ $# != 0 ]
  do
      sum=`expr $sum + $1`
      if [ $? != 0 ]
        then
            exit 1
      fi
      cout=$((count+1))
      shift
done

echo "The sum is $sum."
exit 0


```

Their's one way

---

### Post by tdrusk on 2009-07-17
Well let's look back on my program on line 12
```
x=${count}+x
```
What I want to do is add the variable in $1 to variable x, but the next time around make it variable 2. What would I have to change?

---

### Post by c0mput3r_n3rD on 2009-07-17
Let me just ask you; how are you learning BASH right now and do you previous experience in programming?

---

### Post by typedef on 2009-07-17
It seems you've confused a few concepts. $# is a single integer value representing the number of arguments to the script or function. saying 'for count in $#' won't loop from 1 to $#, it will simply execute once with count set to $# (which would be three in the case of your example).

Also, bash has a special syntax for arithmetic. Simply saying x=${count}+x won't do what you think. In your example, it would end up with something like the string 3+x. Arithmetic can be performed as follows:


```
x=$(( count + x ))
```or
```
x=$(( ${count} + ${x} ))
```Lastly, even if your for loop was looping from 1 to the number of arguments, ${count} is going to be 1, 2, 3, 4, etc... not the actual value of the 1st, 2nd, 3rd, or 4th argument. Although there are ways to make this work  I think it is much simpler to use $@ in your for loop.  $@ expands to all of the parameters passed to your program. All that said, this would be my advice on how to do what you're doing:


```

x=0

for arg in $@
do
         x=$(( arg + x ))
done
echo $x

```

edit: just to clarify something you might be misunderstanding, for loops in bash operate on lists, not ranges of integers. this is probable easiest demonstrated by example:

```

a=3
for i in $a; do  echo $i; done

output:
3

for i in 1 2 3; do echo $i; done

output:
1
2
3

for i in `seq 1 100`; do echo $i; done

output (shells out to the seq program):
1
2
...
100

for i in cat banana pig; do echo $i; done

output:
cat
banana
pig

```

---

### Post by ghostdog74 on 2009-07-17
> **tdrusk said:**
> I am trying to write a for loop that takes the parameters that the user inputs and adds them together. There is no limit to the amount of numbers the user is going to input.

So basically I want it to run like

```
addNumbers 6 4 3
13
```

I am having trouble with the addition part. I am doing
```
      8 x=0
      9 
     10 for count in $#
     11 do
     12         x=${count}+x
     13 done    
     14 echo $x
```

but I know it is wrong. Line 12 has the problem. How can I fix it to make it run?

you use the wrong param. use $@

```

count=0
for x in $@
do    
    count=$(( x+count ))
done    
echo $count

```
please read the bash link in my sig to learn more.

---

### Post by ghostdog74 on 2009-07-17
> **c0mput3r_n3rD said:**
> ```

#!/bin/bash

if [ $# = 0 ]
  then
      echo "Usage: $0 number-list"
fi
sum=0
count=0

while [ $# != 0 ]
  do
      sum=`expr $sum + $1`
      if [ $? != 0 ]
        then
            exit 1
      fi
      cout=$((count+1))
      shift
done

echo "The sum is $sum."
exit 0


```

Their's one way

no need to use external command expr if using bash.

---

### Post by c0mput3r_n3rD on 2009-07-17
> **ghostdog74 said:**
> no need to use external command expr if using bash.

Oh really? How else can you write it then?

Besides the other way I demonstrated.

---

### Post by c0mput3r_n3rD on 2009-07-17
By the way, the reason why I asked is because I think you might have gotten too far ahead of yourself possibly in some $h!+ tutorial that starts you off really quickly with out really explaining things (their are a lot out there).

---

### Post by ghostdog74 on 2009-07-17
> **c0mput3r_n3rD said:**
> Oh really? How else can you write it then?

Besides the other way I demonstrated.

you have already used it your own code
```

cout=$((count+1))

```

---

### Post by tdrusk on 2009-07-17
Thanks guys for all your help. There was some great explaining and learning in the quest to find my answer. 
> **typedef said:**
> 
```
x=$(( count + x ))
```or
```
x=$(( ${count} + ${x} ))
```Lastly, even if your for loop was looping from 1 to the number of arguments, ${count} is going to be 1, 2, 3, 4, etc... not the actual value of the 1st, 2nd, 3rd, or 4th argument. Although there are ways to make this work  I think it is much simpler to use $@ in your for loop.  $@ expands to all of the parameters passed to your program. All that said, this would be my advice on how to do what you're doing:


```

x=0

for arg in $@
do
         x=$(( arg + x ))
done
echo $x

```edit: just to clarify something you might be misunderstanding, for loops in bash operate on lists, not ranges of integers. this is probable easiest demonstrated by example:


Thanks for that. I was looking for the #@ variable and now that you have explained it to me it was literally on the page I was looking at #-o. Oh well. Learning is learning.

---

