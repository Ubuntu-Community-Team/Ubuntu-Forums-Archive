---
title: "An easy one..."
date: 2009-03-02
forum: Programming Talk
---

### Post by vaf on 2009-03-02
Please tell me what I'm doing wrong!!!



i=79  \
j=1   \
while [ $i -gt 0 ]   \
do    \
        j =`expr $i + 1`    \
                if [ -d $SNAPSHOT_RW/hourly.$i ] ; then                 \
                $MV $SNAPSHOT_RW/hourly.$i $SNAPSHOT_RW/hourly.$j ;                     \
                fi;   \
        i=`expr $i - 1`    \

done   \


I get
line 63: syntax error near unexpected token `then'
line 63: `		if [ -d $SNAPSHOT_RW/hourly.$i ] ; then			\'



It should be an easy one! Thanks from a beginner scripter (not even close to a programmer!)
[-o<


I'm trying to create a loop to do this from 79 to 1

if [ -d $SNAPSHOT_RW/home/hourly.2 ] ; then			\
$MV $SNAPSHOT_RW/home/hourly.2 $SNAPSHOT_RW/home/hourly.3 ;	\
fi;
if [ -d $SNAPSHOT_RW/home/hourly.1 ] ; then			\
$MV $SNAPSHOT_RW/home/hourly.1 $SNAPSHOT_RW/home/hourly.2 ;	\
fi;

---

### Post by lloyd_b on 2009-03-02
Well, with the code you posted the space between "j" and "=" in the line```
j =`expr $i + 1`
``` is a bit of a problem :)

Is there a reason you're using expr to evaluate the math?  It's simpler to use bash's internal math routine:
```
j=$((i + 1))
```

Lloyd B.

---

### Post by vaf on 2009-03-02
Hmm thanks. I fixed that but still get the error:

line 65: syntax error near unexpected token `then'
line 65: `		if [ -d $SNAPSHOT_RW/hourly.$i ] ; then

---

### Post by lloyd_b on 2009-03-02
> **vaf said:**
> Hmm thanks. I fixed that but still get the error:

line 65: syntax error near unexpected token `then'
line 65: `		if [ -d $SNAPSHOT_RW/hourly.$i ] ; then
I have no clue.  I pasted your code into a file, and tested it, and that space was the only error I got.

Here's the code I was testing (I removed some redundant semicolons as well as spaces, and formatted it so that it's more readable):
```
#!/bin/bash

i=79
j=1
while [ $i -gt 0 ]; do
    j=$((i + 1))
    if [ -d $SNAPSHOT_RW/hourly.$i ]; then
        $MV $SNAPSHOT_RW/hourly.$i $SNAPSHOT_RW/hourly.$j
    fi
    i=$((i - 1))
done
```

Okay, I tested it as a single-line command (without the line continuation characters).  What was causing the error was the lack of a semicolon on the "j=`expr $i + 1`" line.  Here's the line I was testing:```
i=79; j=1; while [ $i -gt 0 ]; do j=`expr $i + 1`; if [ -d $SNAPSHOT_RW/hourly.$i ]; then $MV $SNAPSHOT_RW/hourly.$i $SNAPSHOT_RW/hourly.$j; fi; i=`expr $i - 1`; done;
```
Lloyd B.

---

