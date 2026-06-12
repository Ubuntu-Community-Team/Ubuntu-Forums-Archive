---
title: "Bash stripping quotes from parameters"
date: 2008-01-22
forum: Programming Talk
---

### Post by mikeym on 2008-01-22
Hi, 

Does anyone know how to avoid bash stripping down parameters when passing them from one script to another?

These are my scripts (as close to sorting out my quotes as I can get them):

init.x
```

#!/bin/bash
PROGRAM=$1
if [ "$PROGRAM" == "" ]; then
	echo "Usage: "
	echo "$0 PROGRAM [parameters]"
	exit 1
fi
shift
while (( "$#" )); do
	if [[ -n "$1" && $1 == *\ * ]]; then
		ARGS="$ARGS \"$1\""
	else
		ARGS="$ARGS $1"
	fi
	shift
done
echo $ARGS
openbox &
feh --bg-scale /home/mikey/Images/Desktop/full_919-linux-background.jpg & 
$PROGRAM $ARGS

```

x.game
```

#!/bin/bash
while (( "$#" )); do
	if [[ -n "$1" && $1 == *\ * ]]; then
		ARGS="$ARGS \"$1\""
	else
		ARGS="$ARGS $1"
	fi
	shift
done
echo $ARGS
xinit ~/bin/init.x $ARGS -- :1

```

Which when I test it with *wine "C:\Program Files\Steam\Steam.exe"* produces what looks to be the correct output from the echos:

```

wine "C:\Program Files\Steam\Steam.exe"
"C:\Program Files\Steam\Steam.exe"

```

But then gives the error:

```

wine: cannot find '"C:\Program'

```

---

### Post by Trumpen on 2008-01-22
> Does anyone know how to avoid bash stripping down parameters when passing them from one script to another?

If the target is not a shell script you could bypass the problem by using xargs:

echo $ARGS | xargs $PROGRAM

Here is an example:
```

$ ./myprog one\ two three
1: one two
2: three
$ var="one\ two three"
$ ./myprog $var
1: one\
2: two
3: three
$ echo $var | xargs ./myprog
1: one two
2: three

```

where the source in C of myprog is: 

[php]
#include <stdio.h>
#include <stdlib.h>

int main(int argc,char ** argv){
int i;
for (i=1;i<argc;i++)
        printf("%i: %s\n",i,argv[i]);

return 0;
}

[/php]

Hope this helps!

---

### Post by yabbadabbadont on 2008-01-22
Does the following work?
```
wine "C:/Program Files/Steam/Steam.exe"
```

---

### Post by ghostdog74 on 2008-01-22
> **mikeym said:**
> 
```

wine: cannot find '"C:\Program'

```
try using single quotes?

---

