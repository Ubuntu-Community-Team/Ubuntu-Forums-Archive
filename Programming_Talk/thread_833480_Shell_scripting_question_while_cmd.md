---
title: "Shell scripting question: while cmd"
date: 2008-06-18
forum: Programming Talk
---

### Post by Browser_ice on 2008-06-18
I am rusty in shell scripting and I have started scripting in my Ubuntu 7.10

I am at a dead stop on one stupid error which I admit I cannot figure out.

My script is summarized as :

> #!/bin/sh
CHOICE=""
...
while &CHOICE" != "0" then
do
	clear
	echo "menu"
	echo "1) choice 1"
 	echo "2) choice 1"
	read CHOICE

	case "&CHOICE" in
	1)
		echo "bla bla bla"
		echo "Are you sure (y/n)?"
		read ANSWER
		if "&ANSWER"="y"; then
			...
		fi;;
...
	0)	echo "Good bye!";;
	esac

done
exit


no matter how I code the while condition, it keeps bombinb out from the start saying it cannot find &CHOICE and always points to the last line of code where my done for the while is. 

The while loop only contains a case cmd and all the case subsection are usign the same format.

I tried using (), [], <>, != in combinations with "while condition; then" and "while condition then"

---

### Post by geirha on 2008-06-18
I see two things you need to correct

1. & will send a command to the background. To read a variable named CHOICE, you need to use $CHOICE.

2. 
```

while [ "$CHOICE" != "0" ]; do
  # some stuff
done

```
(no "then" in while)

---

### Post by dtmilano on 2008-06-18
& means background, $ is parameter expansion.

```
#! /bin/sh

CHOICE=""

while [ -z "$CHOICE" ]
do
        clear
        echo "menu"
        echo "1) choice 1"
        echo "2) choice 1"
        read CHOICE
done

echo "CHOICE=$CHOICE"


```

---

