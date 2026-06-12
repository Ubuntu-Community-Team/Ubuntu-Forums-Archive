---
title: "Using an array to create a letter/number series"
date: 2009-09-21
forum: Programming Talk
---

### Post by kaibob on 2009-09-21
I wrote a script that generated an array in the following format: A1 B1 A2 B2 A3 B3 A4 B4. The number of items in the A and B series were input by the user as command-line parameters. Thus, if the command line parameters were 2 and 4, the output would be A1 B1 A2 B2 B3 B4. The array is then placed in the following commmand line as ${pages[@]}:

```
pdftk A=odd.pdf B=even.pdf cat ${pages[@]} output combined.pdf
```

I came up with the code shown below, and it works, but I wondered if there is an easier way to do this. I spent some time reviewing the Bash Reference Manual and doing a google search and found some items that might be applicable, but the discussions were brief and beyond my level of understanding right now. Thanks for the help.

```
#!/bin/bash

# Add A-series numbers to array.
i=1
j=0
for i in $(seq ${1}) ; do
   pages[${j}]="A${i}"
   i=$((i+1))
   j=$((j+2))
done

# Add B-series numbers to array.
i=1
j=1
for i in $(seq ${2}) ; do
   pages[${j}]="B${i}"
   i=$((i+1))
   j=$((j+2))
done

# Check array. 
echo ${pages[@]}
```

---

