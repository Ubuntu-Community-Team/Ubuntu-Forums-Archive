---
title: "sed second expression fails in bash script"
date: 2010-09-05
forum: Programming Talk
---

### Post by saphil on 2010-09-05
The basic idea was to replace 2 placeholders in 180 text files with correct values.
```
wolf@telcontar:~/test/SET 1$ sed -e 's/INSERTCBID/arrowstar7/g' -e 's/SIGNATURE/"Wolf Halton"/g' *.txt 
```This worked just as expected, however when I put the line in a shell script, the second expression failed.

```

#!/bin/sh
clear
if [ "$4" ]
then
  echo ' '
  echo '+++++++++++++++++++++++++++++++++++++++++++++++'
  echo ' '
  echo ' '
  echo "The clickbank ID Placeholder was -> $1, is that right?"
  echo "and you want to replace that with -> $2. Is that right as well?"
  echo ' '
  echo "The Signature placeholder was -> $3, is that right?"
  echo "You wrote your name as -> $4. Is that right as well?"
  echo ' '
  echo "if these were not correct, press [ctrl] c"
  echo "in the next 23 seconds, and try again"
  sleep 23
  echo 'a whole lot of files are about to be going past.  This is normal'
  sleep 7 # this lets the user get prepared for the script to work
  sed -e 's/$1/$2/g' *.txt -e  's/$3/$4/g' *.txt
  sleep 2 # this lets the user catch a breath.
  echo 'all files done'
else
  echo ' '
  echo '++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++'
  echo ' '
  echo ' '
  echo "To run this script successfully you need to use four arguments"
  echo ' '
  echo 'This app is going to change the "placeholder" words, for instance'
  echo '"INSERTCBID" and "SIGNATURE" with your clickbank ID and your name.'
  echo 'Put your placeholders clickbank ID and name after the file name like '
  echo ' '
  echo 'bash clickswitcher.sh INSERTCBID clickstar44 SIGNATURE "Bill Fescue"'
  echo ' '
  echo 'You have to remember to put your name in quotes if it is more than'
  echo ' one word, like "Bill Fescue" or "Mary Martin"'
  echo 'but you do not need any commas between the arguments'
  echo ' '
  echo 'If you got your placeholders wrong, you can just run the script again'
  echo "It probably didn't change anything."
  echo 'If you got your ClickBank ID or name  wrong, you can just run the '
  echo 'script again using the ClickBank ID and Name you put in wrong as '
  echo 'your new placeholders'
  echo 'Running the script without arguments will get you this help menu again'
fi

```Oddly the first time I did this, I had set up a hard-coded set script and an unset script, and the unset script would unset the commandline sed line above.  

The script sees all the variables ... What am I missing?
```
The clickbank ID Placeholder was -> INSERTCBID, is that right?
and you want to replace that with -> arrowstar7. Is that right as well?

The Signature placeholder was -> SIGNATURE, is that right?
You wrote your name as -> Wolf Halton. Is that right as well?

if these were not correct, press [ctrl] c
in the next 23 seconds, and try again
^C
wolf@telcontar:~/test/SET 1$ 

```

---

### Post by ghostdog74 on 2010-09-05
use double quotes

```

sed "s/$1/$2/g;s/$3/$4/g" *.txt

```

---

### Post by saphil on 2010-09-05
That's perfect.  I think the examples I have been finding are old sed, perhaps.

---

