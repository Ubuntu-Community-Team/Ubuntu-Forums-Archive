---
title: "Question about awk/if/else (not too difficult, I think!)"
date: 2010-10-08
forum: Programming Talk
---

### Post by SuaSwe on 2010-10-08
Hi all,

I'm having some problems with one section of a script I'm writing. The code I have currently looks as follows:

```

cat test | uniq -c | awk '{ if ($1 >1) print $1,$2 }' > test.output

```

... where 'test' is a file containing the following info:

item1
item2
item3
item4
item5
item5
item6
item7

As it stands, the script outputs the count and name(s) of any repeated items in 'test' regardless of whether there is a repeat count or not - so if there isn't, I just get a blank file. What I want is for the script to output the count and name into 'test.output' only *if* an item is repeated in 'test'. Could anyone tip me off on how to do this? 

Cheers!

---

### Post by ghostdog74 on 2010-10-08
use 

```
uniq -D file
```

---

### Post by SuaSwe on 2010-10-08
Guessing that's uniq -d (cap D gives illegal option) and that does look an interesting one - problem is I need the instance count in there as well as the item name. Any ideas? uniq -c obviously means that the rows are all unique, so adding uniq -d doesn't give me any output. Any thoughts on this, such as a way to make uniq look to a certain column? Is that possible?

---

### Post by Blackbug on 2010-10-09
If I understood you correctly..what you want needs to preserve both {print$1} thats the count and {print$2} the value from file.

I wrote a script for it


# storing the output (count)
arr1=(`cat test | uniq -c | awk '{print$1}'`)

# string the output items
arr2=(`cat test | uniq -c | awk '{print$2}'`)

e=0

while [ $e -lt ${#arr1[*]} ]
do
   echo "Count : ${arr1[e]}"

# checks for multiple occurences
   if [ ${arr1[e]} -gt 1 ] 
   then
      echo "Multiple Count: ${arr1[e]}"
   fi  

echo ${arr2[e]}>>file.Output
      e=`expr $e + 1`
     done


I am not sure what exactly you meant, but if above script is useful, let me know.

---

### Post by ghostdog74 on 2010-10-09
```

$ awk 'a[$0]++ { print a[$0],$0 }' file
2 item5

```

---

### Post by SuaSwe on 2010-10-11
That sounds interesting, will try that when I'm next able, cheers!

---

