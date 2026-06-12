---
title: "Bash script to do *something* when a file falls in one of three categories"
date: 2013-03-23
forum: Programming Talk
---

### Post by ntzrmtthihu777 on 2013-03-23
Heh, working on a bash script to chop up a file based on its filesize. As a test I wrote this bash shortie just to see if I can do the test accurately:
```
[s]#!/bin/bash
for i in *.BIN; do
if        [[ 'stat --printf="%s" "$i"' > 71680 ]]
    then    echo "$i is Large"
elif    [[ "$size" > 34816 ]]
    then    echo "$i is Medium"
    else    echo "$i is Small"
fi
done[/s]
```

Unfortuneatly, even though my naked eye and ll tels me that the files are in fact different categories, as far as size goes, each one returns
```
$i is Large
```

anyone care to give a hand?

the end intention is to use cut, dd, or split to section out certain parts of the file into an imagemap and a pallete for use in other software.

Got the test part working =_= had a derp moment and messed up converting the $size variable to the test
```
#!/bin/bash
#many thanks to peawormsworth for the $() idea.
for i in *.BIN; do
if        [[ $(stat --printf="%s" "$i") > 71680 ]]
    then    echo "$i is Large"
elif    [[ $(stat --printf="%s" "$i") > 34816 ]]
    then    echo "$i is Medium"
    else    echo "$i is Small"
fi
done
```

---

### Post by r-senior on 2013-03-23
Did you intend to set a variable called "size" somewhere?

---

### Post by ntzrmtthihu777 on 2013-03-23
Yes, I made an error when placing the stat test in place of $size, I originally had the stat test outside of the if statement and read into the $size variable, but that did nothing, so I rearranged it and got at least some output.

New question, same script: if I wanted to cut, say 1024 bites off of the variable created by stat, how would I read from it? can I give that $() a name of some sort?

---

### Post by r-senior on 2013-03-23
You'd assign it to a variable.

```
size=$(stat --printf="%s" "$i")
```

This would go inside the loop but before the if statement. The if statements would use that variable so that you aren't calling stat unnecessarily.

```
 if [[ $size > 5000 ]]
```

I don't know what you mean by cut 1024 bytes off but you might want to read what the Bash manual says about arithmetic:

[https://www.gnu.org/software/bash/manual/bash.html#Arithmetic-Expansion](https://www.gnu.org/software/bash/manual/bash.html#Arithmetic-Expansion)
[https://www.gnu.org/software/bash/manual/bash.html#Shell-Arithmetic](https://www.gnu.org/software/bash/manual/bash.html#Shell-Arithmetic)

---

### Post by ntzrmtthihu777 on 2013-03-23
ah, you seem to have exactly what I needed. so this goes after the for, but before the if? What I mean is I needed to be able to set a few other variables based on arithmatic with the $size variable, but since I used $() I wanted to be able to call this number somehow. Thank you, that about does it, methinks.

---

### Post by prodigy_ on 2013-03-23
Just a tip: when performing strictly numeric comparisons in bash you want to use something like **if [ "$foo" -gt 1 ] ...** (note the single brackets). This will error out if $foo is not defined or is not a number. Makes debugging easier, especially in more complex scripts.

---

### Post by iMac71 on 2013-03-23
the following code should work:
```
for i in *.BIN
do
    size=$(stat --printf="%s" "$i")
    if [ $size -gt 71680 ]
    then echo "$i is Large"
    elif [ $size -gt 34816 ]
    then echo "$i is Medium"
    else echo "$i is Small"
    fi
done
```

---

### Post by r-senior on 2013-03-23
As an occasional scripter I get really confused by this choice of brackets, would there be any advantage in:

```
if (( size > 71680 )) ...
```

---

### Post by prodigy_ on 2013-03-23
> **r-senior said:**
> (( size > 71680 ))
In this example undefined $size will be silently evaluated to 0, while [ "$size" -gt 71680 ] will produce an error message:
```
$ unset size
$ (( size > 71680 ))
$ [ "$size" -gt 71680 ]
-bash: [: : integer expression expected
```

---

### Post by ntzrmtthihu777 on 2013-03-23
Quite frankly I like [[ ]] because it makes == a bit easier to use =_= I can't tell you how many times I've facedesked over "unary operator expected"

---

### Post by prodigy_ on 2013-03-23
> **ntzrmtthihu777 said:**
> "unary operator expected"
That's why you want to enclose strings and vars in double quotes. ;) Well, actually for short scripts that are likely to stay short and easily readable it all doesn't matter.

---

### Post by ntzrmtthihu777 on 2013-03-23
Yeah, now I double padlock everything, lol. [[ ]] and "$var" all around :P

---

### Post by schragge on 2013-03-23
> **ntzrmtthihu777 said:**
> Quite frankly I like [[ ]] because it makes == a bit easier to use =_= I can't tell you how many times I've facedesked over "unary operator expected" Then use it with double-brackets: ```
[[ $size -gt 71680 ]]
``` The point being *[[ $size > 71680 ]]* is just plain wrong as e.g. ```
[[ 8 > 71680 ]]&& echo Gotcha
``` evaluates to true (8 follows 71680 in the dictionary order).
 
BTW, no need to quote $var inside [[]] :p

---

