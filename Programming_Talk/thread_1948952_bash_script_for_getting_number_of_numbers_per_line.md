---
title: "bash script for getting number of numbers per line"
date: 2012-03-29
forum: Programming Talk
---

### Post by abraxas334 on 2012-03-29
I need a bash script, that reads the line with the fewest number of numbers (not characters) and the largest number of entries into two files.
the original file will be something like:
1 34 5 6 7
23 45 56 67 45 6 5 4
2 3
5 6 7
So in this example i want to read line 2 into an output file A.dat and line 3 into an output file B.dat
numbers can be all way up to the 10000's and are always separated by a space. The number of lines per file may vary but shouldn't be more than 20 or 30.
I can read the file, but after that I get stuck. This is what I have got so far:
[PHP]

#!/bin/bash
var=0;

while read line
do
echo $line;
var=`expr $var + 1`;
done < "myfile"

echo $var;
[/PHP]

---

### Post by CynicRus on 2012-03-29
As an example - a script that reads lines from a file with the numbers and put them:
```

sum = 0; cat total.bytes | while read num ; do sum=`echo $sum+$num" | bc -q` ; done ; echo $sum

```

total.bytes: 
```

1962647
15458
85368
2562448
32110
3920

```

---

### Post by ofnuts on 2012-03-29
> **abraxas334 said:**
> I need a bash script, that reads the line with the fewest number of numbers (not characters) and the largest number of entries into two files.
the original file will be something like:
1 34 5 6 7
23 45 56 67 45 6 5 4
2 3
5 6 7
So in this example i want to read line 2 into an output file A.dat and line 3 into an output file B.dat
numbers can be all way up to the 10000's and are always separated by a space. The number of lines per file may vary but shouldn't be more than 20 or 30.
I can read the file, but after that I get stuck. This is what I have got so far:
[PHP]

#!/bin/bash
var=0;

while read line
do
echo $line;
var=`expr $var + 1`;
done < "myfile"

echo $var;
[/PHP]

To count the words in a given line:
```

num=$(echo $line | wc -w)

```or likeliy more efficient, load in array and count array elements:
```

linearray=($line)
num=${#linearray
[*]}

```

I won't write the whole code, but given the above it is easy to store in two pairs of variables the longest line so far and its word count and the shortest one so far and its word count and print them to files at the end (ie no need to maintain a line count/index)...

---

### Post by Vaphell on 2012-03-29
awk would be perfect for the job
at first line (NR==1) { initialize min, max variables with NF (number of fields) and minline, maxline with $0 (full line) }
for each line { test NF against current min, max and if necessary set them to NF and line variable to $0 }
at the end (END) { print minline > minfile; print maxline > maxfile }

---

