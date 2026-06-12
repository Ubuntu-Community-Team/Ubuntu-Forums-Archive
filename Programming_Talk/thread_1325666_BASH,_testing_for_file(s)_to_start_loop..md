---
title: "BASH, testing for file(s) to start loop."
date: 2009-11-13
forum: Programming Talk
---

### Post by Barriehie on 2009-11-13
Hello all, I've finally got a script, mostly at least, that will do something useful on my machine!  Object is to run all the time and upon detecting image files in a dir. then rename them and move them.  Had it working great until I added in the code to test for the presence of said files to avoid the error being generated when the files didn't exist!

So, somehow it's not evaluating:
```
 if [ -e "/home/barrie/Desktop/temp/pics/*" ] 
```
as true even when their are files in that directory.  What am I missing here???

TIA,
Barrie

```

#!/bin/bash

#
#  Variable Setup
#
LOOPER="TRUE"
OLDDIR="/home/barrie/Desktop/temp/pics/"
NEWDIR="/home/barrie/disk/pics/"
LOGFILE="/home/barrie/log/picsdaemon.log"
declare -a CHARSARRAY=( 'a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9' )
declare -a CHARS
declare -i NUMBER=0
declare -i LOOPCOUNTER=0

#
#  Check for a logfile, if !logfile then create.
#
if [ -e /home/barrie/log/picsdaemon.log ]; then
    LOGFLAG="TRUE"
else
    echo > "/home/barrie/log/picsdaemon.log"
    LOGFLAG="TRUE"
fi

cd $OLDDIR

while [ "$LOOPER" = "TRUE" ]
do

    if [ -e "/home/barrie/Desktop/temp/pics/*" ]
    then

	for file in *
	do
	    while [ $LOOPCOUNTER -lt 10 ]
	    do
		RANDOM=$(date +%N)
		NUMBER=$((RANDOM%62+1))
		CHARS[$LOOPCOUNTER]=${CHARSARRAY[$NUMBER]}
		LOOPCOUNTER+=1
	    done
	    LOOPCOUNTER=0         # ----------------------------- Reset name length counter
	    NEWFILENAME=${CHARS[0]}${CHARS[1]}${CHARS[2]}${CHARS[3]}${CHARS[4]}${CHARS[5]}${CHARS[6]}${CHARS[7]}${CHARS[8]}${CHARS[9]}.jpg
        #
        #  Logfile appendum
        #
        echo $(date +%m-%d-20%y) $(date +%H:%M) $OLDDIR$file $NEWDIR$NEWFILENAME  >> $LOGFILE
        mv $OLDDIR$file $NEWDIR$NEWFILENAME

        declare -a CHARS=  # ------- Reset CHARS array

	done               # ------- End of for file in

    fi

sleep 20                   # ------- Pause, load break!

done                       # ------- Infinite loop, never exit

```

---

### Post by dwhitney67 on 2009-11-13
One would think it would be that simple, but I don't think what you are trying to do is possible.  I think that is why folks use inotify.

---

### Post by sisco311 on 2009-11-13
```
if [ $(ls /home/barrie/Desktop/temp/pics/) ]; then
```

---

### Post by Barriehie on 2009-11-13
I'll have to check out inotify after I give this a break!  

Sisco311, that was giving me a unary operator expected error.

My current running train wreck is this: (notice I said train wreck :))
I've taken the if [ -e <pathtosomefile> ] and done this:

```

PGMSTART=$(ls /home/barrie/Desktop/temp/pics/)
declare STOPLIGHT=${PGMSTART:0:17}
declare STOPPER="ls: cannot access"
if [[ $STOPLIGHT != $STOPPER ]]
then
... run program ...
fi

```

Barrie

---

### Post by sisco311 on 2009-11-13
> **Barriehie said:**
> 

Sisco311, that was giving me a unary operator expected error.



sorry i've tested it with a single file in the directory. d'oh!

this should work:

```
if [ "$(ls /home/barrie/Desktop/temp/pics/)" ]; then
```

---

### Post by Barriehie on 2009-11-13
> **sisco311 said:**
> sorry i've tested it with a single file in the directory. d'oh!

this should work:

```
if [ "$(ls /home/barrie/Desktop/temp/pics/)" ]; then
```

Thanks, I'll try that in a bit.  Started this as an endeavor to learn BASH... :)

Here's my current not so big of a wreck!

```

find /home/barrie/Desktop/temp/pics/ -name *.jpg > /home/barrie/Desktop/temp/pics/go
if [ -s $OLDDIRgo ]
    then
... program ...
fi

```

Edit: Gonna give this a go with python!

---

