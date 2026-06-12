---
title: "Bash confuses me yet again"
date: 2009-08-10
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-08-10
I wrote this script
[PHP]#!/bin/bash

COMMANDS=`echo $@ | awk -F'-' '{ for (i=1;i<=NF;i++) { \
		 							print "\"" $i "\"" \
								} }' | grep -v "\"\""`

echo $COMMANDS

for CM in $COMMANDS
do
echo NQ $CM
done[/PHP]

to do this
(assuming called test.sh)

```

# ./test.sh -new another -del older
NQ new another
NQ del older

```

yet I get this

```

# ./test.sh -new another -del older
NQ "new
NQ another
NQ "
NQ "del
NQ older"

```

I understand what bash is trying to do, but thats not what I told it to do, I think


basically if you are interested, this is supposed to break command line arguments into sections defined by options. They are to be broken into easily executable function calls

ie.
the new function and the del function

---

### Post by dwhitney67 on 2009-08-10
It would appear that the for-loop is not being kind with your COMMANDS, and is tokenizing them using the white-space as a delimiter.

Have you considered using getopt?
```

#!/bin/bash

set -e

OPTS=`getopt -n $0 -o n:d: --long new:,del: -- $@`

eval set -- "$OPTS"

while true
do
	case "$1" in
		-n|--new)  echo "new = $2"; shift 2 ;;
		-d|--del)  echo "del = $2"; shift 2 ;;
		--)         shift ; break ;;
	esac
done

```
Usage:
```

mygetopt --new another --del older

```
Note the usage of "--new" and "--del"; these could be substituted with "-n" and "-d", respectively.

---

### Post by stroyan on 2009-08-10
Here is a simpler way to approach what you describe.
This uses bash itself to break up arguments at "-" characters.
The IFS variable can be used to control where array assignments are delimited.
I printed the array two different ways.
The first way is more compact.
The second way is more flexible if you want to do something different with the "COMMANDS".
```

#expand arguments with spaces between them.
EXPANDED=$@
#Save original IFS value.
OIFS=$IFS
#Change IFS to break up string at "-" characters.
IFS=-
#Break up expanded string and assign to an array.
COMMANDS=( $EXPANDED )
#Restore original IFS value.
IFS=$OIFS
#Remove leading null array element from before first "-".
unset COMMANDS[0]
echo print as an array
#Print out the array elements one to a line with leading "NQ " prefix.
printf "NQ %s\n" "${COMMANDS[@]}"
echo print as elements
for C in "${COMMANDS[@]}"
do
  echo "NQ $C"
done

```

---

### Post by Mr.Macdonald on 2009-08-11
Thank You stroyan, it is perfect

is the "EXPANDED=$@" simply because $@ is an array (2 questions in 1)

---

### Post by stroyan on 2009-08-11
> **Mr.Macdonald said:**
> is the "EXPANDED=$@" simply because $@ is an array (2 questions in 1)
The "EXPANDED=$@" is done as a separate line just to keep the steps simple.

By the way-
Do be careful of using "$*" when manipulating IFS.
The first character of IFS will be used to delimit the arguments.
That can be good, when it is expected.

---

