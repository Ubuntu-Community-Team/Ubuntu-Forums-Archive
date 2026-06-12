---
title: "Need shell script fixed"
date: 2007-04-10
forum: Programming Talk
---

### Post by stealth75711 on 2007-04-10
Hello, i have a non-working shell script here. need help
to get it to work. what i want it to do is when entered at
the command line #prog75 Now is the time
output: One character words = 0
            Two character words = 1
            Three character words = 2
            Four character words = 1
            Words with five or more = 0
            Total words entered =4

```
#!/bin/bash
case "$1" in

 One)     echo "One character words = ($1)"
        ;;
Two)   echo "Two character words = ($1)"
        ;;
three)  echo "Three character words = ($1)"
        ;;
four)   echo "Four character words = ($1)"
	;;
five)   echo "Words with five or more = ($1)"
	;;

total) echo "Total words entered = ($1)"
        ;;
*)      echo "Invalid option"
        ;;
esac

```

---

### Post by apjone on 2007-04-11
What will be the use of this script ?
For total number of words you can do ```
wc -w $1
```

---

### Post by apjone on 2007-04-11
This script would need a few loops, it is possible to do but would take a while to write. 

count number of words
read in each one and count its charactures incressing the correct word value 
out values and total number of words. 
 
you will need to use 'wc' allot

---

### Post by stealth75711 on 2007-04-11
I still cant figure out solution i am a beginner
script writer can i see an example based on
what i allready submitted corrections
made?

---

### Post by apjone on 2007-04-11
I left the bit of paper i scribbled on in work :( will post it tomorrow.

here check out some of these, they not specific to you but are good for general bash scripting ( eg if it if [   ] or if (   ) ? ) 
[http://www.google.co.uk/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:official&hs=x9j&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=bash+scripting+for+beginners&spell=1](http://www.google.co.uk/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu:en-US:official&hs=x9j&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=bash+scripting+for+beginners&spell=1)

---

### Post by lloyd_b on 2007-04-11
Here's a fairly short script that I think does what you want.  

```
# Initialize an array for the results
for INIT in {1..5}; do
        COUNTS[$INIT]=0
done

# Use "wc" to get the word count
WORDCOUNT=`echo "$*" | wc -w`

# Loop through the arguments
for WORD in $*; do

        # Get the character count for the current word
        CURRENT=`echo "$WORD" | wc -m`
        # "wc -m" returns the character count + 1 
        # We need to compensate for this
        CURRENT=$((CURRENT-1))

        # If more than 5 characters, set value to 5
        if (($CURRENT>5)); then
                CURRENT=5
        fi

        # Add one to the appropriate counter
        COUNTS[$CURRENT]=$((COUNTS[$CURRENT]+1))
done

# Output the results
echo "Words with 1 character: ${COUNTS[1]}"
echo "Words with 2 characters: ${COUNTS[2]}"
echo "Words with 3 characters: ${COUNTS[3]}"
echo "Words with 4 characters: ${COUNTS[4]}"
echo "Words with 5 or more characters: ${COUNTS[5]}"
echo "Total Words: $WORDCOUNT"
```

Lloyd B.

---

### Post by stealth75711 on 2007-04-12
ok thanks for the help

:popcorn:

---

