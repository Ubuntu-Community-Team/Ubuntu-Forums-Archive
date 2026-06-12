---
title: "Bash script need help with Loop"
date: 2009-11-22
forum: Programming Talk
---

### Post by Purell86 on 2009-11-22
hey i need some help with a loop statement.  i know i'm close at least i think i am.

i have a file called colors.txt that has this in it:

```

white
black
red
blue
yellow

```

now im making a small script that asks the user "choose a color" and if the user spells the word incorrectly or chooses a color thats not in the list i need to loop it by asking the user" try again"

i thought i could try it using the while loop but im having problems with it:

```

#!/bin/bash

read -p "choose a color: " Color
 
grep_color="$(grep -i -w $Color colors.txt)"

    while [ -z "$grep_color" ]
    do
    read -p " try again: " Color
    
    done


```

still not working the way i want to
hopefully someone can fix my script
thanks in advanced

---

### Post by ibuclaw on 2009-11-22
> **Purell86 said:**
> hey i need some help with a loop statement.  i know i'm close at least i think i am.

i have a file called colors.txt that has this in it:

```

white
black
red
blue
yellow

```

now im making a small script that asks the user "choose a color" and if the user spells the word incorrectly or chooses a color thats not in the list i need to loop it by asking the user" try again"

i thought i could try it using the while loop but im having problems with it:

```

#!/bin/bash

read -p "choose a color: " Color
 
grep_color="$(grep -i -w $Color colors.txt)"

    while [ -z "$grep_color" ]
    do
    read -p " try again: " Color
    
    done


```

still not working the way i want to
hopefully someone can fix my script
thanks in advanced

Try to think in a procedural manner.
You have the while loop running forever because the variable ($grep_color) never changes once you enter the loop.

Putting the grep command inside the while loop will fix your issue.
```

while ! grep -iwq "$Color" dab.c
do
    read -p " try again: " Color
done

# Assign the value after validating it.
grep_color=$(grep -iw "$Color" dab.c)

```

---

### Post by Martin Witte on 2009-11-22
see [this link]("http://tldp.org/LDP/abs/html/commandsub.html") on how to store the result from a command into a variable

---

### Post by Purell86 on 2009-11-22
GOT IT THANKS A LOT [[COLOR=#D40000]**Tinivole**[/COLOR]]("http://ubuntuforums.org/member.php?u=490875")

---

### Post by ibuclaw on 2009-11-22
> **Purell86 said:**
> GOT IT THANKS A LOT [[COLOR=#D40000]**Tinivole**[/COLOR]]("http://ubuntuforums.org/member.php?u=490875")

Your welcome, but the real question is...

Do you understand it?

---

### Post by Purell86 on 2009-11-22
oh definately it makes perfect sense  i think i was practically working backwards in my script.. that why i was getting errors

---

### Post by ghostdog74 on 2009-11-22
here's a simple construction with bash, without using external tools like grep etc

```

declare -a ARRAY
exec 10<"file"
let count=0
while read LINE <&10; do
    ARRAY[$count]=$LINE
    ((count++))
done
exec 10>&- 

while true
do
 read -p "choose a color, [Q|q] to quit: " Color
 ELEMENTS=${#ARRAY[@]}
 for (( i=0;i<$ELEMENTS;i++)); do
    case "${ARRAY[${i}]}" in
      $Color) echo "found: $Color";break;;
      * )echo "Not found: ";break;;
    esac
 done 
done

```

---

