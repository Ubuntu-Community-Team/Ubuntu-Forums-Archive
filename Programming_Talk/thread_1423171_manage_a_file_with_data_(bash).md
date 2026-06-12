---
title: "manage a file with data (bash)"
date: 2010-03-06
forum: Programming Talk
---

### Post by katerina85 on 2010-03-06
Hi,
I pass my data in a .txt file. The data are in the format :
8 User1   Attribute0
6 User1   Attribute1
4 User2   Attribute2
4
2 User1   Attribute3
1 User1   Attribute5
1 User2  Attribute8
...........

I want to make a bash script or command so as to print :
------------------------
17 User1  Attribute0
5 User2 Attribute3
------------------------

17 =  8 + 6 + 2 +1     5=4+1
Attribute0 is the first attribute of User1 I meet 
Attribute3 the first attribute of User2

The line which starts with a number and then is Null I want to remove it

Could you help me ???

---

### Post by hyperAura on 2010-03-06
hi i also wanted to learn about bash scripting too so maybe we can do it together..

ive looked the internet and ive found this code which reads a file and counts the number of lines..

#!/bin/sh
  echo enter file name
  read fname
   
   exec<$fname
   value=0
   while read line
   do
            value=`expr $value + 1`;
            echo $value;
   done
   echo "****$value";



do u know how to parse each line?

---

### Post by hyperAura on 2010-03-06
User1val = 0;
User2val = 0;

# loop through input file
while read inputline;
do
  branch=$`echo "$inputline" | cut -d " " -f 2`
  case "$branch" in
    '" User1"')
      let User1val=User1val+1
      ;;
    '" User2"')
      let User2val=User2val+1
      ;;
    *)

this will recognise which user it is and will add 1 each time to the appropriate variable.. this has to be placed in the code from the previous spot where the while is..

---

### Post by katerina85 on 2010-03-06
Thanks a lot for your help.

The problem is that there are not only User1 and User2.

---

### Post by Rany Albeg on 2010-03-06
Please be more specific.
Do you actually want to sum the first column of the text file?
Just in case your answer will be a yes:

cat <file> | awk '{print $1} END {print sum}'

---

### Post by hyperAura on 2010-03-06
u can create as many users as u want.. do u mean that u dont know how many users will be before executing the script??

---

### Post by matchett808 on 2010-03-07
If you can't get this to work properly in bash, try ruby, I have just started with it and its way better than bash at dealing with files....

---

