---
title: "sum up decimal number from text file -bash script"
date: 2013-10-30
forum: Programming Talk
---

### Post by b_o_n_e_z on 2013-10-30
I have a textfile which contains the following

try.txt
```

john,partTime,3
susan,fullTime,2.6
mary,partTime,2.8
dan,fullTime,2

```

first I tried to print all the partTime student which is successful
```

#!/bin/bash

while IFS, read -r -a array; do
    [[  "${array[1]}" == "partTime"  ]] || continue
    printf "%s \n" "${array[0]}" is a ${array[1]} student"
done  <  "try.txt"

```

output
```

john is a partTime student
mary is a partTime student

```

next I also want to sum up all the numbers of the third column in the text file after printing the types of student and it was not  successful
```

#!/bin/bash

while IFS, read -r -a array; do
    [[  "${array[1]}" == "partTime"  ]] || continue
    printf "%s \n" "${array[0]}" is a ${array[1]} student"
   
    for n in "${array[2]}"; do
       total=$( "$total +=$n" | bc )
       echo $total
    done
done  <  "try.txt"

```

output
```

john is a partTime student
+=3: command not found
mary is a partTime student
+=2.8: command not found

```

expected output
```

john is a partTime student
mary is a partTime student
total = 5.8

```
As I am new to bash scripting , I need to seek help from you guys. thanks in advance

---

### Post by steeldriver on 2013-10-30
I don't think you an use += in this context - also you need to **echo** your input to bc

```
       total=$(**echo** "$total **+** $n" | bc )
```

You should also initialize the variable 'total' - also your IFS assignment appears to be wrong (should be IFS**=**, I think)

Not sure why you want to do the sum loop inside the while loop though? do you really want a running total? and I don't think the printf works the way you think it works

FWIW 'awk' is often simpler for this kind of thing e.g.

```
awk -F, 'BEGIN {total=0} ; $2 ~ /part/ {total += $3} ; END {print "Total = " total}' try.txt
```

---

### Post by b_o_n_e_z on 2013-10-30
thanks alot for your advice. yes i forgot to type the = for IFS in my post

---

