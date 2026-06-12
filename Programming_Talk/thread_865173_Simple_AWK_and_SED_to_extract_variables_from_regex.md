---
title: "Simple AWK and SED to extract variables from regex"
date: 2008-07-20
forum: Programming Talk
---

### Post by mikeym on 2008-07-20
Hi,

Sorry about this but I really do find AWK and SED about as clear as mud, and every time I come back to them I find that I've forgotten how to use them again and it takes me hours to work it out.

OK so having got that of my chest.

I want to take a regular expression - in this case the crop value from mplayer "600:480:20:80" - and extract the variables into bash so they're stored in 

WIDTH 
HEIGHT 
LEFT
TOP

now the regex is something like this 

```

\([[:digit:]]*\):\([[:digit:]]*\):\([[:digit:]]*\):\([[:digit:]]*\)

```

part of the problem is I don't even know which one I want to use half the time AWK or SED

Anyway I'll let you decide.

---

### Post by mssever on 2008-07-20
One approach is ```
str="600:480:20:80"
WIDTH=$(echo $str | awk -F ':' '{ print $1 }')
HEIGHT=$(echo $str | awk -F ':' '{ print $2 }')
LEFT=$(echo $str | awk -F ':' '{ print $3 }')
TOP=$(echo $str | awk -F ':' '{ print $4 }')
```This is ugly, but it works. When it comes to regex stuff, I find sed annoying, and my knowledge of awk is laughable. I prefer to use Ruby for regex tasks.

Oh, you might also be able to do something like ```
WIDTH=$(echo $str | sed 's/\([[:digit:]]*\):\([[:digit:]]*\):\([[:digit:]]*\):\([[:digit:]]*\)/\1/')
```Replacing the \1 with the proper backreference.

ghostdog74 is our resident expert on these types of issues.

---

### Post by WW on 2008-07-20
Your pattern is simple enough that there is no need for sed, awk, or any regex processing.  You can do what you want with a few lines of bash.  For example,

cvsplit.sh
```

#!/bin/bash

cv="600:480:20:80"
IFS=":"
values=( $cv )
IFS=" "
# values is now an array containing the four numbers.

WIDTH=${values[0]}
HEIGHT=${values[1]}
LEFT=${values[2]}
TOP=${values[3]}
echo "WIDTH=$WIDTH, HEIGHT=$HEIGHT, LEFT=$LEFT, TOP=$TOP"

```

Sample run:
```

$ ./cvsplit.sh 
WIDTH=600, HEIGHT=480, LEFT=20, TOP=80
$ 

```

---

### Post by mikeym on 2008-07-20
Thanks,

I had just come up with somthing almost exactly like 

```

str="600:480:20:80"
WIDTH=$(echo str | awk -F ':' '{ print $1 }')
HEIGHT=$(echo str | awk -F ':' '{ print $2 }')
LEFT=$(echo str | awk -F ':' '{ print $3 }')
TOP=$(echo str | awk -F ':' '{ print $4 }')

```

I haven't realy explored arrays in bash, however I like this method because you could format more complex strings into a simple form like this using SED then split them.

```

cv="600:480:20:80"
IFS=":"
values=( $cv )
IFS=" "
# values is now an array containing the four numbers.

WIDTH=${values[0]}
HEIGHT=${values[1]}
LEFT=${values[2]}
TOP=${values[3]}
echo "WIDTH=$WIDTH, HEIGHT=$HEIGHT, LEFT=$LEFT, TOP=$TOP"

```

---

### Post by mssever on 2008-07-20
I think that WW's solution is quite a bit better than mine. I've forgotten a lot of the details of Bash scripting, since I no longer use Bash for anything non-trivial.

---

### Post by ghostdog74 on 2008-07-20
@OP, regular expressions are powerful but if you are not careful, it can become quite a mess. If you really want to use awk, here's another way 
```

# t="600:480:20:80"
# set -- $(echo "$t" | awk -F":" '{print $1,$2,$3,$4}')
# echo $1
600
# echo $2
480

```

using bash
```

# t="600:4:2:1"
# set -- ${t//:/ }
# echo $1
600
# echo $2
4
# echo $3
2


```

---

