---
title: "cli display/manipulate all the filenames in a dir one at a time"
date: 2011-03-21
forum: Programming Talk
---

### Post by chris1497 on 2011-03-21
how do you display/manipulate all the filenames in a dir one at a time
or feed the results of the ls command into an array?

I'm working on a script that modifies file names and does some other stuff.

normally you can just do a for loop across all the filenames in the directory.

The problem is I'm using sed and awk to manipulate the file names before doing other actions with them.  So I somehow need to display or read the file names one at a time. Here are two simplified versions of the script which kinda work, but not fully.



#!/bin/bash
#script name: ls_script.sh
#using ls
ls | sed 's/_/\ /' | awk '{print $2,"\t",$3,"\t",$4 }' 


#!/bin/bash
#script name: cat_script.sh
#attempting to use cat
for file in *.txt
do
cat file | sed 's/_/\ /' | awk '{print $2,"\t",$3,"\t",$4 }' 
#other actions using output
done

results of scripts:
$ls                                       
file_1_3212011_test10
file_2_3212011_test11
file_3_3212011_test12

$./ls_script.sh
1     3212011     test10
2     3212011     test11
3     3212011     test12

$./cat_script.sh
pages and pages of data from file1
pages and pages of data from file2
pages and pages of data from file3


I still feel like I didn't explain it well.

---

### Post by sisco311 on 2011-03-21
Start here:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

also check out:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

---

### Post by gmargo on 2011-03-22
> **chris1497 said:**
> how do you display/manipulate all the filenames in a dir one at a time or feed the results of the ls command into an array?


Here's a shell script that gets all the names from the current directory into an array.

```

#!/bin/bash
# Using bash to use arrays and arithmetic

# Put basenames of files in $NAMES[] array
declare -a NAMES
declare -i indx=0

OIFS=$IFS
IFS=$'\n'

# Find all entries in this directory.
for FILE in $(ls -A)
do
    NAMES[indx++]="$FILE"
done

# Switch back to normal field separator
IFS=$OIFS

echo "There are ${#NAMES[@]} entries:"
for (( indx=0 ; indx < ${#NAMES[@]} ; indx++ ))
do
    FILE=${NAMES[indx]}
    if [ -d "$FILE" ]; then
        echo "\"$FILE\" is a Directory"
    elif [ -f "$FILE" ]; then
        echo "\"$FILE\" is a Regular File"
    else
        echo "\"$FILE\" is something else"
    fi
done

```

---

### Post by sisco311 on 2011-03-22
Good morning! :)

The prefered method is:
```
for file in *
do
  echo "$file"
done
```
See: [http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)

In most cases you can use parameter expansion insead of an external command like tr, sed or awk:
```

for file in *
do
  echo "${file// /_}"
done

```

See:
```
man bash | less +/"^ +Parameter Expansion"
```

**cat file | command** is another thing you should try to avoid:

Wrong: [color=red]cat file | sed 's/ /_/g'[/color]
Correct: [color=green]sed 's/ /_/g' file[/color]

Wrong: [color=red]cat file | tr ' ' '_'[/color]
Correct: [color=green]tr ' ' '_' < file[/color]

---

### Post by chris1497 on 2011-03-22
gmargo,
Thanks that's just what I needed; worked like a charm. :)

sisco
I'll check out those links when I get a chance.  For the moment I just  needed it to work, even if it isn't eloquent or the preferred way. but thank you. :)

---

