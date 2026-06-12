---
title: "deleting part of filename"
date: 2007-10-18
forum: Programming Talk
---

### Post by nickoli on 2007-10-18
I'm working on a small program called dropend the objective of the program is this. I am to write a program that removes the characters given as the second argument from the end of the name of a file that was given as the first argument. 
Example.   dropend myfile.new .new
Will rename myfile.new to myfile. 
I've been working on this for a couple of days and I'm not sure I'm taking the right approach. I'm pretty much a novice and I'm new to regular expressions and sed. So I was hoping to obtain some help here. So far this is what I have.

echo $1 $2 | sed 's/\(.*\)\( .*\)/\2/' >temp 
echo $1 >temp2

Like I said the name of the file is dropend and its set to execution so it works on my computer but right now all it does is send the two command arguments to temp files. I'm not sure my approach is even close to acceptable feel free to give me as much criticism. I just want the program to work, plus I need to learn this because its for my unix programming class which I'm totaly bombing so far. I need to pass this class badly. Any help is greatly appreciated. Thanks.

---

### Post by ghostdog74 on 2007-10-19
use bash
```

# v=myfile.new
# b="new"
# echo ${v%.$b}
myfile

```

---

### Post by nickoli on 2007-10-19
sorry I should have mentioned that I need to assume that the file name will not always be the same and both the filename and the part of the filename that will be deleted will be passed as arguments to the program.

---

### Post by dwhitney67 on 2007-10-19
How about this?  It drops the string from anywhere within the filename.

[PHP]#!/bin/bash

# Check that the command line has at least two arguments, the original
# filename and the string to drop from the filename.  If not, then print
# the usage of the script and exit.
#
# Note that $0 represents the name of this script, $1 the filename, and
# and $2 the string to be dropped.
if [ $# -ne 2 ]
then
        echo "Usage: $0 [filename] [string to drop within filename]"
        exit 0
fi

# unnecessary declarations done for clarity (in other words,
# $1 and $2 could have been used elsewhere as appropriate)
filename=$1
drop=$2

# examine the filename string; substitute any occurrence of the
# drop string with a null (zero length) string.
#
# Once again, an unnecessary declaration
newfilename=`echo $filename | sed -e "s/$drop//"`

# perform the operation of moving the file to the new name
mv $filename $newfilename[/PHP]

---

### Post by nickoli on 2007-10-19
Thanks alot that worked. I appreciate it alot. If it wouldn't be too much of a bother could you please explain it for me so that I can understand how and why it works as well as it does.

---

### Post by dwhitney67 on 2007-10-19
I edited my post to include comments.  Hopefully that will provide you with the explanations you seek.

---

### Post by nickoli on 2007-10-19
Once again I appreciate your help in this matter your comments help a lot. I will continue to play with it until i fully understand it. You saved me. This class has a larger learning curve than my unix 121 class. I should have paid more attention during the first couple of weeks when the instructor went over sed, but he went pretty fast. Anyhow thanks.

---

