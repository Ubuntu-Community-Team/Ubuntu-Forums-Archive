---
title: "How to invoke the calculator &quot;bc&quot; in bash script for floating point arithmetic?"
date: 2010-05-15
forum: Programming Talk
---

### Post by bluesmodular on 2010-05-15
Hello,

My main problem right now is doing floating point arithmetic within a  bash script, with variables.

Right now I have a folder called "myExamples" with a script called  "run_example" that runs with no issues.

I plan to
(1) create many folders inside [myExamples], that are named [example10]  [example11]...
each containing an identical copy of (run_example),
(2) modify Line 172 of each copy of (run_example)...
in one copy, it would be 3.00, the next copy would have 3.05, etc. (This  part doesn't work!)

How can I use the available calculator bc code to do floating point  operations?
Thank you for your help!


My code is below -

#!/bin/sh

# run from directory where this script is
cd `echo $0 | sed 's/\(.*\)\/.*/\1/'` # extract pathname

# Make many folders containing executables of slightly different  parameters...
for i in `seq 10 11`;
do
mkdir examples$i
done

# Copy the same file into all the folders where (run_example) and  [examples{num}] are in ~/myExamples
for i in `ls -d */`;
do cp run_example "$i";
done;

# Replace... something... in (run_example) for each folder
bulksize=`expr 6.00`
half=$(( bulksize / 2)) # THIS LINE DOES NOT WORK

for i in `ls -d */`;
do
cat $i/run_example | sed -e '172 s/[0-9]*/\$half/' > $i/run_example #  THIS LINE DOES NOT WORK
half=`expr $half + 0.05`; # THIS LINE DOES NOT WORK
done;



When I replaced 
half=$(( bulksize / 2))
with
half=$bulksize/2 | bc

I got
expr: non-numeric argument

---

### Post by amauk on 2010-05-15
you need to pipe a single text stream into bc

Eg.
```
echo "scale=3; 3.142 * (5^2)" | bc
```

(Scale = num dec. places to use)

---

### Post by bluesmodular on 2010-05-15
Thanks -- But how would you divide a variable called $bulksize by 2, and put the result in a variable called $half?

And inside the for loop, how to keep adding 0.05 to the variable $half?

---

### Post by amauk on 2010-05-15
> **bluesmodular said:**
> Thanks -- But how would you divide a variable called $bulksize by 2, and put the result in a variable called $half?

```
half=$(echo "scale=2; $bulksize / 2" | bc)
```

> **bluesmodular said:**
> And inside the for loop, how to keep adding 0.05 to the variable $half?

```
half=$(echo "scale=2; $half + 0.05" | bc)
```

---

### Post by bluesmodular on 2010-05-15
Thanks it worked!

---

### Post by amauk on 2010-05-15
Btw, it's largely personal preference
but I'd use $() instead of backticks for command substitution

Eg.
```
cd $(echo $0 | sed 's/\(.*\)\/.*/\1/')
```
instead of
```
cd `echo $0 | sed 's/\(.*\)\/.*/\1/'`
```

They're nestable, while backticks are not

Eg.
```
foo=$(echo "123 $(expr 456 + 2) 789 $(echo "scale=2; 321 / 2" | bc)")
```

plus I think it's more portable (between different shells)

---

