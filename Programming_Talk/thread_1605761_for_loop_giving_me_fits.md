---
title: "for loop giving me fits"
date: 2010-10-25
forum: Programming Talk
---

### Post by edpatterson on 2010-10-25
I feel like an idiot. I am simply trying to iterate an inner loop for a number of times determined by the outer loop

Instead of seeing the value incremented, all I see is "{299..507..26}
"
It has to be something really, really stupid.

```

X=747
Y=207

XDIS=26
YDIS=25

START=$X
END=$(($START+$(($XDIS*$COLS))))

for i in {$START..$END..$XDIS}
do
  echo $i
done

```

---

### Post by AlphaLexman on 2010-10-25
> **edpatterson said:**
> 
for i in {$START..$END..$XDIS}

I think you have a pattern matching error...
My guess is:
```
for i in ${START..END..XDIS}
```

---

### Post by ghostdog74 on 2010-10-26
> **AlphaLexman said:**
> I think you have a pattern matching error...

wrong
> 
My guess is:
```
for i in ${START..END..XDIS}
```
and wrong. 


@OP
your problem is , brace  expansion is performed before any other expansions. 
```

....
for i in $(eval echo {$START..$END..$XDIS})
do
  echo $i
done


```

---

### Post by edpatterson on 2010-10-26
Thank you so very much! I have to admit I would have never figured out the syntax on my own.

Ed

---

### Post by d3v1150m471c on 2010-10-26
something like this may do you more justice:
```

#!/bin/bash


x="0"
finish="100"

while x=`expr $x + 1`; do
echo $x
[ $finish -eq $x ] && break
done

```

---

### Post by ghostdog74 on 2010-10-26
> **d3v1150m471c said:**
> something like this may do you more justice:
```

#!/bin/bash


x="0"
finish="100"

while x=`expr $x + 1`; do
echo $x
[ $finish -eq $x ] && break
done

```


It could have been written this way, without the need for calling external expr.
```

x=0
finish=100
while [ $x -le $finish ]
do
  echo $x
  ((x++))
done


```
Also, a C style for loop. 

```

for((i=$START;i<=$END;i++))
do
    ...
done

```

---

### Post by edpatterson on 2010-10-28
I thought I had it, but...

I am trying to map the coordinates of a grid, one cell at a time, left to right, top to bottom.
```

R=7     # number of rows (lines)
C=6     # number of columns
X=200   # initial horizontal location
Y=100   # initial vertical location
XDIS=25 # horizontal distance cell to cell
YDIS=26 # vertical distance cell to cell
XORG=$X # used to begin each row
for i in $(eval echo {1..$R}; do  W works, based upon above help
  for j in $(eval echo {1..$C} do # works, based upon above help
    echo "$Y:$X"
    $X=$X+$XDIS
  done
  $X=$XORG
  $Y=$Y+YDIS
done

```
This should be laughably simple but all I can come up with is syntax errors and command not founds.

Ed

---

