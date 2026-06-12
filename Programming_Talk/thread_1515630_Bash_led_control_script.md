---
title: "Bash led control script"
date: 2010-06-22
forum: Programming Talk
---

### Post by kempy1000 on 2010-06-22
Hi I am trying to create a script so that I can type:
```

./LED.sh 4on

```
to turn on the fourth LED.
I want this to work for all four leds and have an off option too.

This is my poor failed attempt below. It does not work. I was wondering if any coders could help please.

The lpt program takes arguments in the form of a decimal.
EG:
```

./lpt 7 turns on the first 3 leds. 
./lpt 8 turns on the last on only.

```
```

#!/bin/bash

. Current_Number
. LED1
. LED2
. LED3
. LED4

function subtract {
        NewNumber=$(($number-$1))
        echo "number=\"$NewNumber\"" > Current_Number
}

function add {
        NewNumber=$(($number+$1))
        echo "number=\"$NewNumber\"" > Current_Number
}

case $1 in
4On)
        if [ $LED4 -eq 0 ]
        then
                add 8
                echo "LED4=\"1\"" > LED4
        fi
        ;;
4Off)
        if [ $LED4 -eq 1 ]
        then
                subtract 8
                echo "LED4=\"0\"" > LED4
        fi
        ;;
3On)
        if [ $LED3 -eq 0 ]
        then
                add 4
                echo "LED3=\"1\"" > LED3
        fi
        ;;
3Off)
        if [ $LED3 -eq 1 ]
        then
                subtract 4
                echo "LED3=\"0\"" > LED3
        fi
        ;;
2On)
        if [ $LED2 -eq 0 ]
        then
                add 2
                echo "LED2=\"1\"" > LED2
        fi
        ;;
2Off)
        if [ $LED2 -eq 1 ]
        then
                subtract 2
                echo "LED2=\"0\"" > LED2
        fi
        ;;
1On)
        if [ $LED1 -eq 0 ]
        then
                add 1
                echo "LED1=\"1\"" > LED1
        fi
        ;;
1Off)
        if [ $LED1 -eq 1 ]
        then
                subtract 1
                echo "LED1=\"0\"" > LED1
        fi
        ;;
esac

/home/chris/scripts/lpt/update.sh

exit 0

```

Thanks

---

### Post by geirha on 2010-06-22
The program doesn't let you read the current number? anyway, assuming you have to remember the number yourself, in a file, I think you want something like:
```

#!/bin/bash
file=some_file
if [[ -r $file ]]; then 
  read number < "$file"
else
  number=0
fi

case $1 in
  [1-4]On) 
    i=$(( 2**(${1%On} - 1) ))
    ((number |= i))
    ;;
  [1-4]Off)
    i=$(( 2**(${1%Off} - 1) ))
    ((number &= 15^i))
    ;;
  *)
    echo "Usage: blah blah"
    exit 1
    ;;
esac
echo "$number" > "$file"

./lpt "$number"

```

---

### Post by kempy1000 on 2010-06-24
Works perfectly thank you very much

---

