---
title: "blank space in directory name giving errors"
date: 2012-01-11
forum: Programming Talk
---

### Post by jamesbon on 2012-01-11
Hi I have many directories which have blank space in their names.I have some scripts to be run on them.
Here is an example script

```
    #!/bin/bash
    docid='/home/deel/PDF/rant/spr 2008 Shree rose Visheshank'
    p=1
    while [ $p -lt 117 ]; do
    cp $docid/$p.pdf ./
    p=$p+1
    done

```
Upon executing the above script I get an error 

```
    cp: cannot stat `/home/deel/PDF/rant/spr': No such file or directory
    cp: cannot stat `2008': No such file or directory
    cp: cannot stat `Shree': No such file or directory
    cp: cannot stat `rose': No such file or directory
    cp: cannot stat `Visheshank/1.pdf': No such file or directory
    ./d2.sh: line 5: [: 1+1: integer expression expected

```
What changes do you suggest so that I can take blank space in directory names.I have tried using double quotes "" but the results are same.

---

### Post by sisco311 on 2012-01-11
Check out BashFAQ 020 and BashPitfalls 002 (links in my signature) and [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression).

```

#!/bin/bash

docid='/home/deel/PDF/rant/spr 2008 Shree rose Visheshank'
p=1

while (( p < 117 )); do
    cp -- "$docid/$p.pdf" ./
    ((p++))
done

```

---

### Post by shashanksingh on 2012-01-11
Im not sure if this mite do it, but could you try:

docid='/home/deel/PDF/rant/spr\ 2008\ Shree\ rose\ Visheshank'

instead of :

docid='/home/deel/PDF/rant/spr 2008 Shree rose Visheshank'

coz thats how spaces are shown in directories I guess.

---

### Post by bcooperizcool on 2012-01-11
Try putting double quotes around the locations.     So "/etc/something/$var"  rather than /etc/something/$var

---

### Post by nothingspecial on 2012-01-11
Sisco311 has nailed the problems here (as usual :p)

1. Quote your variables.

2. Use [[ ]] rather than [  ]

3. Use ((  )) instead of [[  ]] for arithmetic.

Backslashes and quotes will not solve the errors.

---

