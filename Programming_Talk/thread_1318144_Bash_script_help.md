---
title: "Bash script help"
date: 2009-11-07
forum: Programming Talk
---

### Post by Purell86 on 2009-11-07
Hi i'm a newbie in scripting and i need help with developing a script that takes 2 lines of numbers from a file and subtracts them and echo's their result.

for instance i have a file test.txt with 
```

200
50

```now i have a script to ADD the two lines of number which is 

```

value=0
while read var
do
value=$(($value + $var))
done < ~/test.txt
echo $value

```but i can't figure out how too subract these two lines and echo the result

---

### Post by Rany Albeg on 2009-11-07
[PHP]#!/bin/bash

value=0
while read var
do
value=$(($var - $value))
done < test.txt
echo $(($value*(-1)))

exit 0[/PHP]

tried to keep it similar to what you wrote.

---

### Post by Purell86 on 2009-11-07
thanks a lot. i knew it was somehow similar just didnt know what to change to get the difference

---

### Post by Rany Albeg on 2009-11-07
You welcome.

---

### Post by ghostdog74 on 2009-11-07
just 2 lines right?
```

# echo $(tr "\n" "-" < file)|bc
150


```

---

### Post by roccivic on 2009-11-07
Also:

To add:
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]cat[/COLOR] textfile
[COLOR="DarkGreen"]12
10
33[/COLOR]
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]echo[/COLOR] $((`[COLOR="Blue"]cat[/COLOR] textfile | [COLOR="Blue"]xargs[/COLOR] -d "\n" | [COLOR="Blue"]sed[/COLOR] 's/ /+/g'`))
[COLOR="DarkGreen"]55[/COLOR]
```

To Substract:
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]cat[/COLOR] textfile
[COLOR="DarkGreen"]33
10[/COLOR]
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]echo[/COLOR] $((`[COLOR="Blue"]cat[/COLOR] textfile | [COLOR="Blue"]xargs[/COLOR] -d "\n" | [COLOR="Blue"]sed[/COLOR] 's/ /-/g'`))
[COLOR="DarkGreen"]23[/COLOR]
```

---

### Post by roccivic on 2009-11-07
Or how about this? :p

To add:

```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]echo[/COLOR] -e [COLOR="Magenta"]"\
#include <stdio.h>\
\n#include <stdlib.h>\
\n\
\nint main (int argc, char *argv[]) {\
\n\tif ( argc > 1 ) {\
\n\t\tint i, sum = 0;\
\n\
\n\t\tfor (i=1; i<argc; i++) {\
\n\t\t\tsum+=atoi(argv[i]);\
\n\t\t}\
\n\t\tprintf(\"%i\\\
\n\", sum);\
\n\t}\
\n\treturn 0;\
\n}"[/COLOR] > sum.c
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]gcc[/COLOR] -Wall -O2 sum.c -o sum
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]sudo mv[/COLOR] ./sum /usr/local/bin/mysum
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]rm[/COLOR] ./sum.c
```

The test file:
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]cat[/COLOR] textfile
[COLOR="DarkGreen"]12
10
33[/COLOR]
```

The sum command (3 words :D):
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]mysum[/COLOR] $([COLOR="Blue"]cat[/COLOR] textfile)
[COLOR="DarkGreen"]55[/COLOR]
```

That works for integers only, for floating numbers it would be something like this:
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]echo[/COLOR] -e [COLOR="Magenta"]"\
#include <stdio.h>\
\n#include <stdlib.h>\
\n\
\nint main (int argc, char *argv[]) {\
\n\tif ( argc > 1 ) {\
\n\t\tint i;\
\n\t\tfloat sum = 0;\
\n\
\n\t\tfor (i=1; i<argc; i++) {\
\n\t\t\tsum+=atof(argv[i]);\
\n\t\t}\
\n\t\tprintf(\"%f\\\
\n\", sum);\
\n\t}\
\n\treturn 0;\
\n}"[/COLOR] > sum.c
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]gcc[/COLOR] -Wall -O2 sum.c -o sum
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]sudo mv[/COLOR] ./sum /usr/local/bin/myfloatsum
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]rm[/COLOR] ./sum.c
```

To substract integers:
```
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]echo[/COLOR] -e [COLOR="Magenta"]"\
#include <stdio.h>\
\n#include <stdlib.h>\
\n\
\nint main (int argc, char *argv[]) {\
\n\tif ( argc > 1 ) {\
\n\t\tint i, diff = atoi(argv[1]);\
\n\
\n\t\tfor (i=2; i<argc; i++) {\
\n\t\t\tdiff-=atoi(argv[i]);\
\n\t\t}\
\n\t\tprintf(\"%i\\\
\n\", diff);\
\n\t}\
\n\treturn 0;\
\n}"[/COLOR] > diff.c
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]gcc[/COLOR] -Wall -O2 diff.c -o diff
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]sudo mv[/COLOR] ./sum /usr/local/bin/mydiff
[COLOR="DarkRed"]roccivic@roccivic-pc:~$[/COLOR] [COLOR="Blue"]rm[/COLOR] ./diff.c
```

---

### Post by ghostdog74 on 2009-11-08
you are doing the unnecessary.

---

### Post by roccivic on 2009-11-08
Yeah, I know, was somewhat bored.

---

