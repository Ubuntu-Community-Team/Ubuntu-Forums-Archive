---
title: "Problem with bash script and sed"
date: 2007-10-28
forum: Programming Talk
---

### Post by tarasbulba on 2007-10-28
Hello i'm totally newbie on programming. I'm working on this bash script:
[HTML]#!/bin/sh
# Get the path of this script
cwd=`dirname $0`

if ( test -d "/usr/bin/totem" );then
  sed '65d' $cwd/file.txt>$cwd/file1.txt
  mv $cwd/file1.txt $cwd/file.txt
fi[/HTML]
It should check if totem is installed and delete line 65 in file.txt.Here is my problem,this script doesn't delete line 65 from file.txt.But if i write the script like this:
[HTML]#!/bin/sh
# Get the path of this script
cwd=`dirname $0`
  sed '65d' $cwd/file.txt>$cwd/file1.txt
  mv $cwd/file1.txt $cwd/file.txt[/HTML]
it deletes line 65.Please help

---

### Post by ghostdog74 on 2007-10-28
try:

```

...
if [ -d "/usr/bin/totem" ];then
 ....
fi

```

---

### Post by tarasbulba on 2007-10-28
> **ghostdog74 said:**
> try:

```

...
if [ -d "/usr/bin/totem" ];then
 ....
fi

```
I've tried your suggestion but it don2t work. :(

---

### Post by geirha on 2007-10-28
from "man [":
```
       -d FILE
              FILE exists and is a directory

```
/usr/bin/totem is a file, not a directory, so obviously it evaluates to false.
```
       -f FILE
              FILE exists and is a regular file

```

---

### Post by ghostdog74 on 2007-10-28
> **tarasbulba said:**
> I've tried your suggestion but it don2t work. :(

unless "totem" is a directory, otherwise, use -f , if its a file.

---

### Post by tarasbulba on 2007-10-28
> **ghostdog74 said:**
> unless "totem" is a directory, otherwise, use -f , if its a file.
I have used -f but it seems that does not work
[HTML]if [ -f "/usr/bin/totem" ];then
  sed '65d' $cwd/file.txt>$cwd/file1.txt
  mv $cwd/file1.txt $cwd/file.txt
fi[/HTML]
gives "Syntax error: "fi" unexpected (expecting "then")"

---

### Post by geirha on 2007-10-28
Odd, I copy/pasted the code, and it works fine here, though I would use sed -i instead of using two files ...
```
 [ -f /usr/bin/totem ] && sed -i '65d' $cwd/file.txt 
```

---

### Post by tarasbulba on 2007-10-29
> **geirha said:**
> Odd, I copy/pasted the code, and it works fine here, though I would use sed -i instead of using two files ...
```
 [ -f /usr/bin/totem ] && sed -i '65d' $cwd/file.txt 
```
Thank you very much this did the trick :)

---

