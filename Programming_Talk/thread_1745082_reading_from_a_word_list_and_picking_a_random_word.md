---
title: "reading from a word list and picking a random word"
date: 2011-04-30
forum: Programming Talk
---

### Post by Mia_tech on 2011-04-30
this I'm doing it in shell, so I appreciate if the code is en same script... I trying to generate a random word. I'm not aware of any command that can do this in ubuntu; however, I know that with `cat file | wc -l` you can get the number of lines in a given file, if I just could pass that number into a var and generate a random number then extracting that word from the file and put it into a variable... that's the idea... if there is an easier way of generating random words with build in linux commands, I would like to know 


thanks

---

### Post by Vaphell on 2011-04-30
```
#!/bin/bash

dict='dict.txt'
n=$( cat "$dict" | wc -l )
while true
do
  rnd=$( date '+%N' | sed 's/^[0]*//' )
  lnum=$(( rnd % n + 1 ))
  word=$( awk -v lnum=$lnum 'NR==lnum { print }' "$dict" )
  echo $lnum $word
done
```

date formatted to nanoseconds should provide enough randomness
row_number = rnd modulo line_count + 1

---

### Post by Mia_tech on 2011-04-30
> **Vaphell said:**
> ```
#!/bin/bash

dict='dict.txt'
n=$( cat "$dict" | wc -l )
while true
do
  rnd=$( date '+%N' | sed 's/^[0]*//' )
  lnum=$(( rnd % n + 1 ))
  word=$( awk -v lnum=$lnum 'NR==lnum { print }' "$dict" )
  echo $lnum $word
done
```

date formatted to nanoseconds should provide enough randomness
row_number = rnd modulo line_count + 1

are you sure you're not missing a condition somewhere?.... and I don't see much diff b/t "date +%N" and "date '+%N' | sed 's/^[0]*//'"... it generate random number either way

---

### Post by Vaphell on 2011-04-30
depends on what that condition is supposed to do

---

### Post by Mia_tech on 2011-04-30
much simpler... just using command substitution

```
FILE=file.txt
LINES=`wc -l $FILE`
RANDOM=`date +%N`
NUMBER=$[ ( $RANDOM % $LINES )  + 1 ]
WORD=`sed -n $NUMBER\p $FILE`
```

---

### Post by PunkLV on 2011-04-30
```

#!/bin/bash
dictionary="/usr/share/dict/american-english"
word=""
wordlist="./wordlist"


function choose_words(){
    characters=$1
    for word in $(cat $dictionary); do
	word_length=$(expr length $word)
	if [ $word_length == $characters ]; then
	    echo $word >> ./wordlist$characters
	fi
    done
    
}

function get_word(){
	characters=$1
	if [ -f "$wordlist$characters" ]; then
		random=$RANDOM
		range=$( wc -l $wordlist$characters | grep -o [0-9]*[0-9])
		random=$(($random%$range))
		random_word=$(awk NR==$random $wordlist)
	else
		choose_words $characters
	fi
}

echo "Word length?: "
read word_length

# makes a list of all words. Takes up some time
# because dictionary has 100k entries.
# However, you could make 10-12 files once and use them.

# choose_words $word_length
get_word $word_length
echo $random_word

```
Coding is not as nice as the previous, yet this was fun.
Should work fine.

---

### Post by Vaphell on 2011-04-30
> much simpler... just using command substitution
```
FILE=file.txt
LINES=`wc -l $FILE`
RANDOM=`date +%N`
NUMBER=$[ ( $RANDOM % $LINES )  + 1 ]
WORD=`sed -n $NUMBER\p $FILE`
```


i merely showcased randomness with an infinite loop
besides your script does pretty much what my did, except you used backticks instead of better $()
[http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

also on my box **wc -l $file** returns '<int> <filename>' and that doesn't look like a valid division parameter.
```
./rnd.sh: line 8: ( 2327 % 196 dict.txt )  + 1 : syntax error
```

Also i had to remove leading zeroes in my version, because it threw an error (leading zeroes indicate base-8 )
```
./rnd.sh: line 19: 006382406: value too great for base (error token is "006382406")
```
For some reason your modulo line doesn't trigger it. It's interesting because my tests say that in your version backticked date +%N seems to degrade to 16bit integer while my $( ) preserves all 9digits

---

### Post by PunkLV on 2011-04-30
There is **grep** for **wc**. And had used a modulo division to limit **$RANDOM**.
Anyways. Seems to work for me, if this is what OP was asking for.
And yeah, needs proper testing anyways.

---

### Post by Vaphell on 2011-04-30
i was replying to OP's post :)

---

### Post by kaibob on 2011-04-30
The Greg's Wiki site has an informative FAQ on this topic:

[http://mywiki.wooledge.org/BashFAQ/026](http://mywiki.wooledge.org/BashFAQ/026)

---

### Post by Some Penguin on 2011-05-01
```

sort -R <infile> | head -1 

```

would also work; sort -R randomizes.

---

### Post by Mia_tech on 2011-05-01
> **Vaphell said:**
> i merely showcased randomness with an infinite loop
besides your script does pretty much what my did, except you used backticks instead of better $()
[http://mywiki.wooledge.org/BashFAQ/082](http://mywiki.wooledge.org/BashFAQ/082)

also on my box **wc -l $file** returns '<int> <filename>' and that doesn't look like a valid division parameter.
```
./rnd.sh: line 8: ( 2327 % 196 dict.txt )  + 1 : syntax error
```

Also i had to remove leading zeroes in my version, because it threw an error (leading zeroes indicate base-8 )
```
./rnd.sh: line 19: 006382406: value too great for base (error token is "006382406")
```
For some reason your modulo line doesn't trigger it. It's interesting because my tests say that in your version backticked date +%N seems to degrade to 16bit integer while my $( ) preserves all 9digits

you're right!.. I forgot to fix it. here's what it should've been

```
LINES=`wc -l $FILE | cut -d " " -f1`
```

---

### Post by Mia_tech on 2011-05-01
> **Some Penguin said:**
> ```

sort -R <infile> | head -1 

```

would also work; sort -R randomizes.

you know what? simplicity is king when it comes to programming!... nice!!!

---

### Post by cgroza on 2011-05-01
In python this would be child play.

---

### Post by cgroza on 2011-05-01
People should switch to python:

```

#!/usr/bin/python
import os, random, sys

def readfile(file):
    if os.path.exists(file):
        txt_file = open(file, "r")
        return txt_file.read()
    else:
        print "Invalid path"
        return

def pick_random_word(text):
    words = text.split()
    return words[random.randrange(0, len(words))]

def main(path):
    print pick_random_word(readfile( path))

if __name__ ==  "__main__":
    main(sys.argv[1])


```

---

### Post by hakermania on 2011-05-01
Common!
```
LINES=$(wc -l < test)
```
is the right way!
Then you simply get a random number using the variable $RANDOM which is at the $LINES's range (let's call this number $random_line) and finally, the random word comes:
```
random_word=$(sed -n "${random_line}p;${random_line}q" dict.txt)
```

I agree that simplicity is good but you have to do some things at first alone (e.g. to generate a random number or to read a specific line from a file), automation isn't always good.

---

### Post by bashologist on 2011-05-01
I know it's solved but for future google searches or something...

Does it have to be indexed? Did you need the index for something? If not then here's another solution.

Not sure if this's what you wanted but
```
sort -R file | head -n 1
```

A faster possible option would be to use seek to a random byte position then read until the next newline then read that line and exit.

Edit: Someone beat me to it lol. Great minds think alike.

---

