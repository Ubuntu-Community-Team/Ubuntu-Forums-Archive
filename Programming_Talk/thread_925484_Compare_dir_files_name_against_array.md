---
title: "Compare dir files name against array"
date: 2008-09-20
forum: Programming Talk
---

### Post by aliahsan81 on 2008-09-20
Hi ALL,

I am making a script that search all then worldwriteable dir in documentroot.I have manage to find all the dir now i want to match each file extension in worldwriteable against a list of array which contain extension like php html etc,if i find any file with the following extension then print dirname. Dont see to get any idea how i do that.i past my code for review and comments


#!/bin/bash

list[0]="php"
list[1]="html"
Docroot[0]="/var/www/html/"

export IFS=$'\n'

# Loop through our array.
for x in ${Docroot[@]}
do
# Find all directories & subdirectories
for i in $(find $x -type d -perm /o=w )
do

for j in $(ls -l $i)
do


echo $j

done
done
done


Output

total 8
drwxrwxrwx 2 root root 4096 2008-09-19 18:44 abc
-rw-r--r-- 1 root root 0 2008-09-10 17:21 abc2.php
-rw-r--r-- 1 root root 0 2008-09-10 17:21 abc3.php
-rw-r--r-- 1 root root 0 2008-09-10 17:21 abc.php
drwxrwxrwx 2 root root 4096 2008-09-19 01:53 gallery
-rw-r--r-- 1 root root 0 2008-09-19 18:43 abc.php

---

### Post by ghostdog74 on 2008-09-20
```

find . -type d -perm /o=w | while read DIR
do  
   find "$DIR" -type f \( -name "*.html" -o -name "*.php" \) -print
done


```

---

### Post by aliahsan81 on 2008-09-21
Thx ghostdog74,Your code was great,But i m facing a problem.Now i have the file name and dir name which contain all the php and html file.I want to print only the dir name example like this.An other problem is this see my out put plz.

What i want :)

/var/www/abc count 3  ### mean its has 3 php OR html files in it same for all dir.i am doing  concatenation but not working for me i modify you code.I know its a simple thing but i m new to bash.


find /var/www/html -type d -perm /o=w | while read DIR
do
test=$(find "$DIR" -type f \( -name "*.html" -o -name "*.php" \) -print )


$test2="$test2 $test"
done

print $test2




OutPut + problem


/var/www/html/phpBB3/language/en/common.php
/var/www/html/phpBB3/includes/utf/data/search_indexer_95.php: No such file or directory
./test.sh: line 10: = /var/www/html/test2/abc.php: No such file or directory
./test.sh: line 10: = : command not found
./test.sh: line 10: = : command not found

---

### Post by ghostdog74 on 2008-09-21
to count, you  can use wc -l. pipe the find output to wc -l

---

### Post by aliahsan81 on 2008-09-21
I did exactly what before you post  wc -l but giving a wrong count,its giving count of dir inside other dir i past u ls -l output.But thx,And how can i do print like this i dont wana print file name 
/var/www/html/test  3
We can deal with count but first part is important.Thx in advance.


/var/www/html/test3/abc.php
/var/www/html/test3/abc3.php
/var/www/html/test3/abc/abc.php
/var/www/html/test3/abc/abc2.php
/var/www/html/test3/abc2.php 5

LS -L

drwxrwxrwx 2 root root 4096 2008-09-19 18:44 abc
-rw-r--r-- 1 root root    0 2008-09-10 17:21 abc2.php
-rw-r--r-- 1 root root    0 2008-09-10 17:21 abc3.php
-rw-r--r-- 1 root root    0 2008-09-10 17:21 abc.php
drwxrwxrwx 2 root root 4096 2008-09-19 01:53 gallery

---

### Post by ghostdog74 on 2008-09-21
```

find . -type d -perm /o=w | while read DIR
do  
   find "$DIR" -type f \( -name "*.html" -o -name "*.php" \) | awk '{count[$0]++}END{
  for ( i in count ) print i,count[i]
}'
done

```

---

### Post by aliahsan81 on 2008-09-22
Hi thx yor realy help full.I need to know how to check if dir is empty

see what i did.

let test=0
find /var/www/html -type d -perm /o=w | while read DIR
do
  #  echo $DIR 
test=$(cd "$DIR"; ls *.html *.php 2>/dev/null | wc -l)



if [ "$test" != "0" ]
   then
     echo "$DIR $test"
   fi

done

Output

/var/www/html/test3 4
/var/www/html/test3/abc 2
/var/www/html/test/abc 1
/var/www/html/test2 1

---

### Post by aliahsan81 on 2008-09-22
Thx Alot

---

