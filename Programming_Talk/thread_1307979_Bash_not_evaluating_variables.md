---
title: "Bash not evaluating variables"
date: 2009-10-31
forum: Programming Talk
---

### Post by I[AM]SMRT on 2009-10-31
Ok, so I've been staring at this script for the past hour to no avail. Basically, I want to pass arguments to a C program I wrote, both with arguments of the bash script and variables calculated in the bash script. For some reason it's not working, here's the script where it is right now:

```
#!/bin/bash

# Wrapper script for finding modes, outputting data as Frequency vs Amplitude

NUMPOS=$(cat $1 | awk '/^position/' | wc -l)
LINES=$[$(cat $1 | wc -l)-5-$NUMPOS]
NUMFREQ=$[$LINES/$NUMPOS]

mkdir split_$1
cp -t split_$1 drumdata $1
cd split_$1
./drumdata $1 $NUMPOS $NUMFREQ
rm drumdata $1
```
This gives me the error: ./getModes.sh: line 19: 26946 Segmentation fault      ./drumdata $1 $NUMPOS $NUMFREQ

So I tried a different method with array variables

```
#!/bin/bash

# Wrapper script for finding modes, outputting data as Frequency vs Amplitude

NUMPOS=$(cat $1 | awk '/^position/' | wc -l)
LINES=$[$(cat $1 | wc -l)-5-$NUMPOS]
NUMFREQ=$[$LINES/$NUMPOS]

args[0]=$1
args[1]=$NUMPOS
args[2]=$NUMFREQ

mkdir split_$1
cp -t split_$1 drumdata $1
cd split_$1
./drumdata ${args[@]}
rm drumdata $1
```
Which gives me the error: ./testModes: line 22:  7945 Segmentation fault      ./drumdata "${args[@]}"

Which makes me want to cry because I wrote a script to test array variable behavior:

```
File Edit Options Buffers Tools Sh-Script Help                                  
#!/bin/bash                                                                     

args[0]=test
args[1]=getModes.sh
args[2]=drumdata.c

cp -t asdf ${args[@]}
```
And it works :(. Why aren't my variables being evaluated?

---

### Post by Hyporeal on 2009-10-31
From the error message, it looks like drumdata is crashing. You don't see the variables evaluated because it's supposed to be a debug message, printing the line of the script that caused the crash. Try having drumdata print its parameters before doing anything else -- this will conclusively tell you whether the variables are getting evaluated by the script or not.

---

