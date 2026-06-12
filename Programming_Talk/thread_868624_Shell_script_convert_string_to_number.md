---
title: "Shell script: convert string to number"
date: 2008-07-24
forum: Programming Talk
---

### Post by svk on 2008-07-24
Hello,

I'm very new to shell scripting in Bash.

I'm trying to figure out how to treat the output of [FONT=Courier New]stat -c %s *filename*[/FONT] as a number, and not as a string.  If you run that command, it will output the size of the file in bytes.

Here's the script I'm working on.  It iterates over every file in the working directory, and attempts to print the cumulative size of all the files over which it iterated so far.

```

#!/bin/bash
# print-cumulative-sizes.sh

declare SIZE=0
declare TOTAL=0

for file in *; do {
    SIZE=`stat -c %s $file`;
    TOTAL=`expr $SIZE+$TOTAL`;
    echo $TOTAL;
}; done

```

The problem should be evident from the output:

[FONT=Courier New]serg@bijou:~/Pictures$ ./print-cumulative-sizes.sh 
1036228+0
970325+1036228+0
1108950+970325+1036228+0
1476318+1108950+970325+1036228+0
1027836+1476318+1108950+970325+1036228+0
1050479+1027836+1476318+1108950+970325+1036228+0
1156703+1050479+1027836+1476318+1108950+970325+1036228+0
1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
960132+1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
1569659+960132+1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
1149074+1569659+960132+1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
4096+1149074+1569659+960132+1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
98528+4096+1149074+1569659+960132+1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
142+98528+4096+1149074+1569659+960132+1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
142+142+98528+4096+1149074+1569659+960132+1215533+1156703+1050479+1027836+1476318+1108950+970325+1036228+0
[/FONT]
See what's wrong?  How can I get bash to treat my $SIZE and $TOTAL variables as numbers, not as strings?

Thank you in advance for any help!

---

### Post by ghostdog74 on 2008-07-24
stat can take in shell wildcards. so there's no need for a loop
```

stat -c %s * | awk '{s=s+$0}END{print "size: "s" bytes"}'

```

else, you can use bc instead of expr
```

echo "1+2" | bc

```

---

### Post by WW on 2008-07-24
ghostdog74's awk solution is short and sweet, but if you want to stick with your bash code, use **let** for the arithmetic:
```

#!/bin/bash
# print-cumulative-sizes.sh

declare SIZE=0
declare TOTAL=0

for file in *; do
    SIZE=`stat -c %s $file`;
    let TOTAL+=SIZE;
    echo $TOTAL;
done

```

EDIT: I've been using C++ lately, so I didn't even notice those curly braces around the statements in the for loop.  BASH doesn't use braces like that.

EDIT 2: This variation uses a single call to stat:
```

#!/bin/bash
# print-cumulative-sizes.sh

declare TOTAL=0

SIZES=`stat -c %s *`
for SIZE in ${SIZES}; do
    let TOTAL+=SIZE
    echo $TOTAL
done
echo "TOTAL=$TOTAL"

```

---

### Post by geirha on 2008-07-24
Your initial script should work if you just add some spaces around the + for the expr-command
```

$ expr 2+2
2+2
$ expr 2 + 2
4

```

You can also use bash's (( )) and $(( )) for integer arithmetics
```
$ TOTAL=0; SIZE=10
$ echo $TOTAL
0
$ ((TOTAL+=SIZE))
$ echo $TOTAL
10
$ echo $((TOTAL+=SIZE))
20

```

---

