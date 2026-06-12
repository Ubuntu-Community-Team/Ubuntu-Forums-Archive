---
title: "If matches regular expression then"
date: 2008-04-04
forum: Programming Talk
---

### Post by primal100 on 2008-04-04
I want to create an if condition (in BASH) where if a file contains data, the script will echo something, but if the file is blank nothing happens. I found a way to do this using grep but the grep command itself outputs something anyway when it runs which isn't what I want. What's the best way to do this? Would it better to use case-esac instead of if-fi?

This particular file, if it contains data always begins with a capital letter so the regexp is '^[A-Z]'.Otherwise it will be blank.

So for this part of the file I need

if

$temp13='^[A-Z]' 

then

	echo "$temp11 $temp12, you now have $temp14 $temp15. Please go to room $temp13."

fi

But I get an error
^[A-Z]: command not found

Any ideas? Thanks in advance!

---

### Post by ghostdog74 on 2008-04-04
in that case, you just need to check whether that character is in that file. 
```

while read -r line
do
 case $line in
    [A-Z]* ) echo .....
 esac
done < file

```

---

### Post by WW on 2008-04-04
When you say the file is "blank", do you mean it contains no characters at all?  That is, the file is empty?  (For example, you can create an empty file with the command **touch empty_file**, assuming empty_file doesn't already exist.)  If so, you can use a bash **test**:

**checksize.sh**
```

#!/bin/bash

DATAFILE="mydata.txt"

#
# First check if $DATAFILE exists, then check if it has a size greater
# than zero.
#
if test -e $DATAFILE; then
    # The file exists.
    if test -s $DATAFILE; then
        echo "$DATAFILE is not empty."
    else
        echo "$DATAFILE is empty."
    fi
else
    echo "$DATAFILE does not exist."
fi

```

For example,
```

$ ls
checksize.sh*
$ ./checksize.sh 
mydata.txt does not exist.
$ touch mydata.txt
$ ls
checksize.sh* mydata.txt
$ ./checksize.sh 
mydata.txt is empty.
$ echo "ABC" >> mydata.txt 
$ ./checksize.sh 
mydata.txt is not empty.
$ 

```

---

### Post by primal100 on 2008-04-04
Thanks; didn't know about if test -s; very useful.

Basically I'm extracting information from a time-dependant database. Sometimes, the where command will retrive information, sometimes not, because the where command selects based on the current time. So I needed a way to output a command only when information was actually retrieved.

Thanks a lot!

---

