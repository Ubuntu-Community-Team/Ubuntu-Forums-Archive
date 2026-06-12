---
title: "Bash scripting menu help!"
date: 2011-03-30
forum: Programming Talk
---

### Post by Raeannmac on 2011-03-30
Hey guys!
I'm writing a script and can't for the life of me figure out why I keep getting this error message:

bash: Assign3.sh: line 49: syntax error near unexpected token `done'
bash: Assign3.sh: line 49: `done'

here's the code:

#!/bin/bash
echo "Select one of the options."
echo "a. List all files in the present working directory"
echo "b. Display today's date and time."
echo "c. Invoke shell script for Problem #1 above"
echo "d. Display whether a file is a \"simple\" file or a \"directory\" "
echo "e. Create an archive of your home directory for backup purposes"
echo "f. Start a remote login session to the server atlas.sheridanc.on.ca"
echo "g. Give information on all users currently logged on"
echo "x. Exit"
echo -n "Enter your option here:"

read option
case $option in
  a) ls -l
     ;;
  b) `date`
     ;;
  c) #problem 1
     echo "Enter a path to search from home"
     read fpath
     #find $fpath
     if [ -s $fpath ]
     then
     set [ ls -l $fpath ]
     echo `$fpath $6 $3 $5 $7 $8`
     else
     rm -r $fpath
     fi
     ;;
  d) echo "Enter file name"
     read $filename
     if [ -d ]
     then
       echo this is a directory
     fi
     ;;
  e) tar -cvf /~ home.tar
     ;;
  f) echo "Enter in your username"
     read $username
     ssh `$username@atlas.sheridanc.on.ca`
     ;;
  g) who
     ;;
  x) exit
     ;;
esac
done


Any help would be greatly appreciated!

Thanks :)

---

### Post by robots.jpg on 2011-03-30
Did you originally have the whole thing enclosed in a while loop?  Your 'done' statement doesn't appear to belong to anything.

---

### Post by lloyd_b on 2011-03-30
You're getting that error message because there's no "do" to match to that "done".

Are you trying to have that thing loop?  If so, you want something like:```

while true; do
   echo "1. Do something"
   echo "2. Do something else"
   echo "3. Quit"
   echo -n "Option ->"

   read choice
   case $choice in
      1) echo "You chose to do something"
         ;;
      2) echo "You chose to do something else"
         ;;
      3) break
         ;;
   esac
done
```

Lloyd B.

---

