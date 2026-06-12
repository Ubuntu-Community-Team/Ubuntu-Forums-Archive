---
title: "bash: varying variable (ie $VAR$NUM)"
date: 2009-02-03
forum: Programming Talk
---

### Post by alphaniner on 2009-02-03
Is it possible to use 'varying variables' in a bash script?

For example, say I have a variable NUM which is 3.  And I have a number of variables VAR1 VAR2 and VAR3.  Is there a way to use a loop to make use of (as output) the VAR variables?  For example, I first tried
```

CT=1

while [ "$CT" -le "$NUM" ]
do
     echo $VAR$CT
     CT=$(( $CT + 1 ))
done
```
which output the value of CT.

I also tried
```
echo $VAR`echo $CT`
```
which also output the value of CT.

And
```
echo '$'VAR$CT > file
```
which output (literally) $VAR1 to a file then
```
cat file |echo
```
which output nothing.  Strange, but I guess that's what happens when you try to do something the code isn't designed to do.  So, can it be done?

---

### Post by lloyd_b on 2009-02-03
What you probably need is an "Array":
```
#!/bin/bash

CT=1
NUM=4
VAR[1]="Fred"
VAR[2]="Wilma"
VAR[3]="Barney"
VAR[4]="Betty"

while [ "$CT" -le "$NUM" ]
do
     echo ${VAR[$CT]}
     CT=$(( $CT + 1 ))
done
```

Produces the following output:
```
lloyd@dell:~/stuff$ ./arrays.sh
Fred
Wilma
Barney
Betty
```

Is this what you're trying to do?

Lloyd B.

---

### Post by alphaniner on 2009-02-03
Good work deciphering my madness.  That's exactly what I was trying to do.

```
lloyd_bTHANKYOU=$(( $lloyd_bTHANKYOU + 1 ))
```

---

### Post by slakkie on 2009-10-04
You can do this with eval as well:

```

!/bin/bash

bar1=bar
bar2=bartwo
bar3=barbarbar

foo=3

myvar=$(eval echo '$bar'$foo)
echo $myvar

```

Oops, sorry for kicking this old thread, didn't realize it was old..

---

### Post by lloyd_b on 2009-10-04
> **slakkie said:**
> You can do this with eval as well:

```

!/bin/bash

bar1=bar
bar2=bartwo
bar3=barbarbar

foo=3

myvar=$(eval echo '$bar'$foo)
echo $myvar

```

Oops, sorry for kicking this old thread, didn't realize it was old..

Yeah, that is a bit of a "necropost"....

At any rate, while the "eval" version will work, it's less efficient than using bash's inbuilt functions for the same job:
```
#!/bin/bash

VAL1="fred"
VAL2="wilma"
VAL3="barney"
VAL4="betty"

for CURRENT in {1..4}; do
    VARNAME="VAL$CURRENT"
    echo ${!VARNAME}
done
```The "!" in that echo tells bash to find the value of the variable name contained in VARNAME, rather than the value of VARNAME itself.

Lloyd B.

---

