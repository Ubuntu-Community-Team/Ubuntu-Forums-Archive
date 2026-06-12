---
title: "Basic BASH loop"
date: 2011-06-03
forum: Programming Talk
---

### Post by hailholyghost on 2011-06-03
Hi Linux Experts,

I'm trying to print a file name and then print one number from that file.

For example, I want the result to be:

anneal1.out 0.609
anneal2.out 0.344
...
anneal999.out 4.433

My script is the following:

```
#!/bin/bash

for i in `ls anneal*.out`

do
        grep "Total torsion  penalty" $i | awk '{print $4}' | awk '{print FILENAME, $1}'
done
```

But it will only print out (numbers are correct)
- 1.116
- 0.616
- 1.034
- 0.789
- 2.770

I've also tried "*grep "Total torsion  penalty" $i | awk '{print $4}' | awk '{print {$i}, $1}'*" but that didn't work either.

Thanks for any help you can provide!
-Dave

---

### Post by erind on 2011-06-03
Can you post the* line *or* lines *where the number is located, from one of the files, say:

 ```
grep "Total torsion  penalty" anneal1.out
```

---

### Post by hailholyghost on 2011-06-03
Hi erind,

thanks for replying!

```
grep "Total torsion  penalty" anneal1.out   

```
gives
  ```
Total torsion  penalty:      4.621
```

I pipe that to awk to grab the number, i.e. the 4th column.

---

### Post by erind on 2011-06-03
Assuming there's only **one line** with the number in one file, try this :

```
#!/bin/bash

for i in anneal*.out
 do
      awk '/Total torsion  penalty/ { print FILENAME, $NF }' "$i" 
 done
```Or even this might suffice:

```
awk '/Total torsion  penalty/ { print FILENAME, $NF }' anneal*.out
```

---

### Post by Arndt on 2011-06-03
> **hailholyghost said:**
> 
```
#!/bin/bash

for i in `ls anneal*.out`

do
        grep "Total torsion  penalty" $i | awk '{print $4}' | awk '{print FILENAME, $1}'
done
```

But it will only print out (numbers are correct)
- 1.116
- 0.616
- 1.034
- 0.789
- 2.770


The - characters are there instead of the expected filename, because awk gets sent its input from stdin, not from a file, so it doesn't know the filename.

> 
I've also tried "*grep "Total torsion  penalty" $i | awk '{print $4}' | awk '{print {$i}, $1}'*" but that didn't work either.



$i is the shell variable and $1 is the awk variable, so this can't work, but a small variation ought to work:

```
grep "Total torsion  penalty" $i | awk '{print $4}' | awk "{print \"$i\", \$1}"
```

But why two awks? This should be equivalent:

```
grep "Total torsion  penalty" $i | awk "{print \"$i\", \$4}"
```

---

### Post by hailholyghost on 2011-06-03
> **erind said:**
> Assuming there's only **one line** with the number in one file, try this :

```
#!/bin/bash

for i in anneal*.out
 do
      awk '/Total torsion  penalty/ { print FILENAME, $NF }' "$i" 
 done
```Or even this might suffice:

```
awk '/Total torsion  penalty/ { print FILENAME, $NF }' anneal*.out
```

Thank you so much erind and arndt!  This solved my problem.  Much appreciated!

---

