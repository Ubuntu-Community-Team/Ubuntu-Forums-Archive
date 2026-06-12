---
title: "Newb shell script question!"
date: 2009-04-08
forum: Programming Talk
---

### Post by Pierre-Alexandre on 2009-04-08
Hello folks,

I am trying to make a script which will calculate the integer part of a square root - using Djikstra's algorithm - in Sh script. I've put this on so far but I keep getting "-le: argument needed" (or something along) errors. I've tried many possible input methods (with the '', "", etc - no change).

Here is my code:
```
#!/bin/sh
echo "Valeur de X ?"
read X
DELTA=32768
Y=0
while [ "$DELTA" -ne "0" ]
do
	Y2=$(($DELTA+$Y))
	Y2=$(($Y2*$Y2))
	if [ $Y2 -le $1 ]; then
		Y=$(($Y+$DELTA))
	else
		DELTA=$(($DELTA/2))
	fi
done
 	


```

Any idea?

---

### Post by lensman3 on 2009-04-08
Run you script with:

bash -vx <script.sh>

The -v for verbose and -x for execute will show the results of each line as it executes or is read.  You should see your error that way.

You can also put the -xv on the #!/bin/bash line in the script.  This works for the sh-shell, bash and the c-shell.

Hope this helps.

---

### Post by lloyd_b on 2009-04-08
> **Pierre-Alexandre said:**
> Hello folks,

I am trying to make a script which will calculate the integer part of a square root - using Djikstra's algorithm - in Sh script. I've put this on so far but I keep getting "-le: argument needed" (or something along) errors. I've tried many possible input methods (with the '', "", etc - no change).

Here is my code:
```
#!/bin/sh
echo "Valeur de X ?"
read X
DELTA=32768
Y=0
while [ "$DELTA" -ne "0" ]
do
	Y2=$(($DELTA+$Y))
	Y2=$(($Y2*$Y2))
	**if [ $Y2 -le $1 ]; then**
		Y=$(($Y+$DELTA))
	else
		DELTA=$(($DELTA/2))
	fi
done
 	


```

Any idea?

The "$1" on the line highlighted above - that's the first command line parameter (of which there's probably none).  I think you intended for this to be "$X"...

Lloyd B.

---

### Post by Pierre-Alexandre on 2009-04-09
Dear god, I feel dumb now ! That was indeed the problem, thanks for your help!

---

