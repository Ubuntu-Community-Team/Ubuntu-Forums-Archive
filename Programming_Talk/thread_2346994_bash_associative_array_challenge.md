---
title: "bash associative array challenge"
date: 2016-12-20
forum: Programming Talk
---

### Post by immortal.morph on 2016-12-20
i have a folder containing files with different names in filename
for example 
20161201_1235_jan_created_file.txt
20161205_2113_piet_created_file.txt
20161207_1511_kees_created_file.txt
20161210_1735_jan_edited_file.txt

now i would like to create two arrays one containing the name and how many occurrences  of that person and a second array that has the name of the person the action, timestamp and filename affected which is in the textfile

for the first array i have done the following 

```
#!/bin/bash
declare -A array2d
for f in *.txt; do
        name=$(echo $f | cut -f3 -d_)
        num=$(echo ${array2d[$name]})
        ((num++))
        array2d[$name]=$num
done
```

i have no idea how to solve the second part

for the first part is there any shorter way to do this

thanks in advance for any assistance

---

### Post by Keith_Helms on 2016-12-22
The problem with the second array is you have multiple rows for each person and each contains 3 values - timestamp, action, and filename.  One solution is to create a bunch of variable names on the fly, like this:
```
#!/bin/bash

testdata="20161201_1235_jan_created_file.txt 20161205_2113_piet_created_file.txt 20161207_1511_kees_created_file.txt 20161210_1735_jan_edited_file.txt"
declare -A array2d
for f in $testdata; do
    name=`echo $f | cut -f3 -d_`
    num=${array2d[$name]}
    ((num++))
    array2d[$name]=$num
    timestamp=`echo $f | cut -f1-2 -d_`
    action=`echo $f | cut -f4 -d_`
#    filename=`cat $f`
    filename="dummy_file.txt"
# Manufacture variable names by concatenating the name, number, and a string suffix
# NOTE:  this will NOT work if any of the variables contain spaces
    eval ${name}${num}ts="$timestamp"
    eval ${name}${num}a="$action"
    eval ${name}${num}fn="$filename"
done

# Print the data stored in the manufactured variable names
for name in ${!array2d[@]}; do
    echo $name
    recs=${array2d[$name]}
    for (( idx=1; idx<=$recs; idx++ ))
    do
        eval timestamp="\$${name}${idx}ts"
        eval action="\$${name}${idx}a"
        eval filename="\$${name}${idx}fn"
        echo "$idx timestamp $timestamp action $action filename $filename"
    done
done
```

The commented out assignment for filename assumes that each file contains a single line with a filename.

The output using the test data string is:
```
$ test.sh
jan
1 timestamp 20161201_1235 action created filename dummy_file.txt
2 timestamp 20161210_1735 action edited filename dummy_file.txt
piet
1 timestamp 20161205_2113 action created filename dummy_file.txt
kees
1 timestamp 20161207_1511 action created filename dummy_file.txt

```

---

### Post by immortal.morph on 2016-12-22
Thanks Keith it does exactly what i hoped for!!

---

### Post by Habitual on 2016-12-22
> **immortal.morph said:**
> for the first array i have done the following 

```
#!/bin/bash
declare -A array2d
for f in *.txt; do
        name=$(echo $f | cut -f3 -d_)
        num=$(echo ${array2d[$name]})
        ((num++))
        array2d[$name]=$num
done
```
Mad Props.

> **immortal.morph said:**
> i have no idea how to solve the second part
A little humility is a wonderful thing. Honest and Fresh. :)

That is how questions are ***asked***, IMO.

---

