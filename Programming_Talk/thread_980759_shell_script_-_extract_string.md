---
title: "shell script - extract string"
date: 2008-11-13
forum: Programming Talk
---

### Post by ufis on 2008-11-13
I have a text file with key=value pairings like:
```
abc=0This is abc
xyz=2This is xyz
abcde=1This is abcde
```
I need a shell script (my attempt posted below) that takes in the key and outputs the value broken up in 2 parts, the first digit and the rest.

What I have is the following:

```
#!/bin/sh

#use -F"$1=" (adding = to input param) to avoid abcde being found as abc
#could also make thefile.txt as input param I guess
sst=$(awk -F"$1=" '$2 != "" {print $2}' thefile.txt)

echo $sst

trc=`expr substr "$sst" 1 1`
tro=`expr substr "$sst" 2 150`

echo $trc
echo $tro
```

This works for me, but in the interest of learning more: Is there a better way to do this?
Is there a better way to do tro=`expr substr "$sst" 2 150` ... the idea is to read from the second character to the end of the line.

Any input/suggestions welcome.

---

### Post by ghostdog74 on 2008-11-13
```

awk -F"=" '{print substr($2,2)}' file

```
```

awk 'BEGIN{FS="=[0-9]+"}{print $2}' file

```

---

### Post by Cracauer on 2008-11-13
Trying to avoid additional processes:

```

IFS="="
while read line ; do
        set -- $line
        echo first: "'$1'"
        echo second: "'$2'"
done < mydata.txt

```

---

### Post by ufis on 2008-11-14
I now realise my original post may have been a little misleading.

My original script should NOT have been the one I was testing with but the one I would actually use.

This script will be used with [nagios]("http://www.nagios.org/") so it will need an exit code (the first digit of the value) to indicate OK, WARNING, CRITICAL status to nagios.

The actual script:
[PHP]#!/bin/sh

sst=$(awk -F"$1=" '$2 != "" {print $2}' thefile.txt)

trc=`expr substr "$sst" 1 1`
tro=`expr substr "$sst" 2 150`

echo $tro
exit $trc #exit code for nagios[/PHP]

I will look at the two replies and see what of that I can use, or just keep it in mind for the future.

---

### Post by ghostdog74 on 2008-11-14
the best thing to do is to show a sample of your input file you want to get information from and the final output you want.

---

### Post by ufis on 2008-11-14
> **ghostdog74 said:**
> the best thing to do is to show a sample of your input file you want to get information from and the final output you want.
Ok.

I have a text file, lets call it thefile.txt, that looks like:
```
abc=0This is abc
xyz=2This is xyz
abcde=1This is abcde
```
key=value mappings.

Now I have a shell script, lets call it thescript.sh that I would like to call like
```
./thescript.sh thefile.txt xyz
```
The shell script should go to the text file, find the key specified (xyz) and get the value associated with it.

This value should then be broken up into a code (the first digit of the value) and a message (the rest of the value). For this example it should be code:2, message:This is xyz.

The message should then be sent to the standard output.

The shell script should then exit with the exit code being the code extracted from the value.

---

### Post by ghostdog74 on 2008-11-14
```

#!/bin/bash

thefile=$1
key=$2

awk -v key="$key" 'BEGIN{FS="="}
$2 ~ key{
 r=gensub("([0-9]+)(.*)","\\1:\\2","g",$2)
 split(r,result,":") 
 print "code: " result[1]
 print "message: " result[2]
}
' $thefile

```

---

### Post by unutbu on 2008-11-14
ufis, is it ever the case that in your text file a key like abcde comes before abc?
```

abcde=1This is abcde
abc=0This is abc
xyz=2This is xyz
```

If so, the awk script as it now stands will not pick out the right line when searching for the 'abc' key. It also does not return the exit code. I don't know awk well enough to fix the former problem. The latter problem is easy: just change
[php]
 print "code: " result[1]
 print "message: " result[2][/php]

to 
[php]
 print "message: " result[2]
 exit result[1][/php]

If you don't mind relaxing the shell script requirement, here is a python script which does what you want:
[PHP]
#!/usr/bin/env python
import sys
import re
filename=sys.argv[1]
key=sys.argv[2]
for line in open(filename,'r'):
    if line.startswith(key+'='):
        codemsg=line.split('=')[1]
        match=re.match('(\d+)(.*)',codemsg)
        if match:
            code=int(match.group(1))
            msg=match.group(2)            
        else:
            print 'codemsg pattern not found'
            sys.exit(99)
        break
try:
    print 'message:%s'%msg
    sys.exit(code)
except NameError:
    print 'key %s not found'%key
    sys.exit(99)
[/PHP]
If the key can not be found in the file, or if it can not parse the codemessage format, the above script returns exit code 99. 

If you call the python script 'thescript.py', then you can call it from a shell script:
[PHP]#!/bin/bash
thefile=$1
key=$2
thescript.py "$thefile" "$key"
echo $?[/PHP]
and access the exit code through the $? variable.

---

