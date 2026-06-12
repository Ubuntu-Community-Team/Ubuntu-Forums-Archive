---
title: "help with a bash script to create a html table"
date: 2010-03-06
forum: Programming Talk
---

### Post by dunryc on 2010-03-06
Hi guys as the title says i need a little help i have partisally written a bash script to create a table in html 

> echo "<table>" > table.html


for ((rows=1; rows<=$1; rows++));
	do
	echo "<tr>"  >> table.html


		for ((columns=1; columns<=$2; columns++));
			do
			echo "<td>A</td>"  >> table.html

		done

	echo "</tr>"  >> table.html

done

echo "</table>"  >> table.html

so if i use ./test 3,3

i get the following output 


> A A A
       A A A
       A A A 




for the third arguement in the script i wish to include content that will be replace the A characters in the table this will be in the form of a text file as below 

> 
Apples
Oranges
Bananas
Pears
Kiwis
Plums
Peaches
Grapes
Melons


these would appear in table for as above can any one please give me a heads up as to how i can accomplish this ? Cheers guys

---

### Post by falconindy on 2010-03-06
I wouldn't use a for loop. I also wouldn't specify the number of rows because that will occur naturally based on the number of columns and your input size.

```
#!/bin/bash

if [[ $# -ne 2 ]]; then
    echo "Usage: $0 <columns> <input file>" >&2
    exit 1
fi

# Redirect STDOUT to an html file
exec >> output.html

# Start table
echo "<table>"

count=0 # Initialize a counter for columns
while read line; do
    if [[ $count -eq 0 ]]; then
        # We're at the start of a new row, open it.
        printf "\t<tr>\n"
    fi

    if [[ $count -lt $1 ]]; then
        # Print next line from data file
        printf "\t\t<td>%s</td>\n" "$line"
    fi

    (( count++ ))

    if [[ $count -eq $1 ]]; then
        # We're at the end of a row, close it.
        printf "\t</tr>\n"
        count=0
    fi
done < $2

if [[ $count -ne 0 ]]; then
    # Kludge for when columns doesn't divide equally into data size
    printf "\t</tr>\n"
fi

# End table
echo "</table>"
```

---

