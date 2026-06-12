---
title: "Shell script - Arrays and sorted"
date: 2011-02-16
forum: Programming Talk
---

### Post by mokachoka on 2011-02-16
I all

I have two arrays that will be used side by side (as a sort of 2 dimensional array)... 

Lets say...

A1 -          A2
5 --- 7
7                   --- 3
2 ---                   2
5 ---                   6
9 ---                   2
6 ---                   1
1 --- 9
3 ---                   3
2 ---                   5

What i would like to do is sort array 1 but not lose the number associated with it in array 2 so it would also sort that, but according to array 1... If that makes sense?

How can this be done? Im using the BASH shell.

---

### Post by Vaphell on 2011-02-16
```
#!/bin/bash

x=( 1 2 4 6 3 9 8 7 5 )
y=( 5 1 2 4 6 3 9 8 7 )

echo BEFORE:
echo ${x[@]}
echo ${y[@]}

tmp=$( for (( i=0; i<${#x[@]}; i++ ))
       do
         echo ${x[i]} ${y[i]}
       done | sort )

x=( $( echo "$tmp" | awk '{print $1 }' ) )
y=( $( echo "$tmp" | awk '{print $2 }' ) )

echo AFTER:             
echo ${x[@]}
echo ${y[@]}
```

i glued corresponding elements together, sorted strings and took column 1 and 2 respectively to create new versions of arrays. I guess it's kinda lame but it works. My example is trivial, more difficult set of data may prove tricky to sort easily (eg. element length not constant)

---

### Post by mokachoka on 2011-02-16
Thanks for your reply, would it make it easier if i said the arrays were defined by the user... What i mean is i ask the user how many (which would be the length of the array) then i loop through and ask the user to input each value into each array...

The input from the user could obviously not be in order... (would make it much easier).
I need it in order for the next part of the script.

```

echo -ne "Please enter number of processes : "
read NUMBER
declare -a processarrival
declare -a processlength


let counter=0
while [ $counter -lt $NUMBER ]
do
[INDENT] echo -ne "Please enter arrival time for process $counter : "
read ANSWER

processarrival[$counter]=$ANSWER

echo -ne "Please enter length for process $counter : "
read ANSWER2

processlength[$counter]=$ANSWER2


let total=$total+$ANSWER2

let counter=$counter+1
[/INDENT]done

```I was hoping for a much simplier solution.

---

### Post by Vaphell on 2011-02-16
bash has very limited set of fancy tools and sometimes you need to be very creative with what you've got.
Do you have to write it in bash? Python has dedicated structures and algorithms right off the bat.

Either way length of the array is not a problem, also my method didn't care about that and it wasn't paricularly long, 1 temp variable + 2 lines. What type of data do elements hold? Is there any specific format?

---

### Post by kurum! on 2011-02-16
bash 4 already comes with associative arrays.

---

### Post by Vaphell on 2011-02-16
won't associative array fail when given repeating keys? i assume we are talking about situation where elements of one set are keys and the other set consists of values (array[x[i]]=y[i])? I agree it is enough when indexing data is unique.

---

