---
title: "looping and concatinating onto the same string in bash"
date: 2009-07-08
forum: Programming Talk
---

### Post by boson-spin on 2009-07-08
I'm quite new to bash

Basically I'm trying to loop through each item in an array and add them to the end of a string.

At the moment I have:
```


for (( i = 1; i < ${#ANARRAY[@]}; i++ ))
do
      $CONCAT = ${CONCAT} ${ARGARRAY[$i]}
done


```

But it is not at all happy about this. I'm trying to get it so the array consists of, for example, [a b c d] and
$CONCAT will be:
a b c d

Thanks for any help

---

### Post by ghostdog74 on 2009-07-08
what exactly are you wanting to do eventually?

---

### Post by c0mput3r_n3rD on 2009-07-08
Well you want to assign those values to the variable, so you don't want to use $CONCAT = ...  just CONCAT = ...

Think about in the for loop, you say for ( i = 1 ... ), not for ($i = 1 ...)

---

### Post by stroyan on 2009-07-08
If you actually meant to use "ARGARRAY" twice rather than "ANARRAY" and "ARGARRAY", then you don't need to use an explicit loop at all.  If you meant to concatenate to a previous value of "CONCAT" then you could use
CONCAT+=" $ARGARRAY[@]"
If you meant to assign to "CONCAT" without keeping a previous value, then you could use
CONCAT="$ARGARRAY[@]"

You should be aware that the index values of an array are not always contiguous.
And they do not necessarily start with an index of 1.  Assigning with
ANARRAY=( a b c d )
will start with an index of 0.
You can robustly get a list of the index values for an array with "${!A[@]}".
Here is your two array version with a more robust loop.  It gets the index values for "ANARRY" and uses them to look up elements of "ARGARRAY".

for i in ${!ANARRAY[@]}
do
      $CONCAT+=" ${ARGARRAY[$i]}"
done

---

