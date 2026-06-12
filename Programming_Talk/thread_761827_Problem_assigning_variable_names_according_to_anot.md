---
title: "Problem assigning variable names according to another variable"
date: 2008-04-21
forum: Programming Talk
---

### Post by primal100 on 2008-04-21
I am writing a program to log all bluetooth MAC addresses which pass a certain point into a MYSQL database. I'm having trouble assigning a value of each MAC address to a different variable.

Line 10 is:

currentbtid${i}=$(sed "$i!d" temp2) 

So if the value of i was 3;

the variable currentbtid3 would be assigned to be the 3rd line of the output of hcitool scan (temp2).

I'm getting the following errors:

./proximitytest3: line 10: currentbtid2=00:19:63:47:30:F7: command not found
'RROR 1102 (42000): Incorrect database name '
./proximitytest3: line 13: -e: command not found

The last two errors are a mystery because I'm using the exact same syntax as in other files where it works - anyway, anyone know whats the causing the first error? Thanks in advance.

Here is the full script:

#!/bin/bash
while (true)
do
	hcitool scan --flush --length=4 > temp1
	sed 's/.*\(..:..:..:..:..:..\).*/\1/' temp1 > temp2
	wc -l temp1 > temp3
	linecount=$(sed 's/ temp1//g' temp3)
i=2
while [  $i -le $linecount  ]; do
currentbtid${i}=$(sed "$i!d" temp2) 
mysql --user=mysql --password=whatever \
	-e "Use BTIDs;" \
	-e "Insert into CurrentBTIDs(BluetoothID) values("$currentbtid${i}");"
let i=i+1
done
done

---

### Post by ghostdog74 on 2008-04-21
use an array instead. See [here]("http://tldp.org/LDP/abs/html/arrays.html") for instructions on how to use arrays

---

### Post by stroyan on 2008-04-21
Assigning to a variable with a name taken from another variable can be done with the eval built-in.
Listing variables matching a prefix can done with ${!prefix}.
Getting the value of a variable with a name taken from another can be done with ${!variable}.
```

i=1;while read L;do v=currentbtid${i}; let i=$i+1; eval "$v=\$L";done < temp2
for v in $(echo ${!currentbtid@});do echo $v, ${!v};done

```

But as ghostdog74 noted, an array can do a better job when you want to index by a single integer.

```

A=( $(<temp2) )
for ((i=0;i<${#A[*]};i++));do echo $i, ${A[i]};done

```

---

