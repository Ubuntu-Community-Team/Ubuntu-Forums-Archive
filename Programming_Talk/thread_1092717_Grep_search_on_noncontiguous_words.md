---
title: "Grep search on noncontiguous words"
date: 2009-03-10
forum: Programming Talk
---

### Post by kaibob on 2009-03-10
I need to use grep to search for lines that contain two words that are not contiguous. I finally got this to work by piping one grep search into another somewhat as follows:

```
grep firstword file.txt | grep secondword
```

Is there an easier or more direct way to do this? I did a google search and read the grep man page but didn't find anything. I thought a regular expression might do the trick but couldn't find anything helpful on this either.

---

### Post by cubeist on 2009-03-10
you want to use an OR command, so if it finds word1 OR word2 it will output those lines...
```
cat file | grep "word1\|word2"
```

---

### Post by kaibob on 2009-03-10
Accidental double post. I have reported it for removal.

---

### Post by kaibob on 2009-03-10
> **cubeist said:**
> you want to use an OR command, so if it finds word1 OR word2 it will output those lines...
```
cat file | grep "word1\|word2"
```

Sorry--I didn't explain properly. I want grep to find lines that contain both words. So, it would be word1 AND word2 and, as previously mentioned, these words are located on the same line but are separated from one another by other words.

---

### Post by cubeist on 2009-03-10
no prob, the AND operator is the ampersand &

---

### Post by ghostdog74 on 2009-03-10
> **kaibob said:**
> 
```
cat file.txt | grep firstword | grep secondword
```

Is there an easier or more direct way to do this? 
use awk, and stop using useless cat. tools like grep/awk/wc/cut etc can take in file input.
```

awk '/firstword/ && /secondword' file.txt

```

---

### Post by lavinog on 2009-03-10
> **ghostdog74 said:**
> use awk, and stop using useless cat. tools like grep/awk/wc/cut etc can take in file input.
```

awk '/firstword/ && /secondword' file.txt

```

you don't have to use cat to use grep:
```
grep firstword file.txt| grep secondword
```
I find awk more painful to learn, but there are times when it does seem like the best option

---

### Post by ghostdog74 on 2009-03-10
> **lavinog said:**
> you don't have to use cat to use grep:
```
grep firstword file.txt| grep secondword
```
I find awk more painful to learn, but there are times when it does seem like the best option
grep does one thing in a specific area, awk does more than that.

---

### Post by kaibob on 2009-03-10
cubeist and ghostdog74. Thanks for the responses. I'm new to shell scripting but am making progress.

---

### Post by cubeist on 2009-03-10
> **kaibob said:**
> cubeist and ghostdog74. Thanks for the responses. I'm new to shell scripting but am making progress.

No problem, I agree with ghost dog, when you can, get into the habit of using more advanced programs like sed and awk.  Then in the future, when you are writing more complex scripts, you can go back and use your old sed, awk commands and expand on them...

grep is also a fine tool, but it is usually better if what you are trying to do can be accomplished with one command instead of two... this leads to cleaner code and better recycle-ability...

---

### Post by ghostdog74 on 2009-03-10
> **cubeist said:**
> No problem, I agree with ghost dog, when you can, get into the habit of using more advanced programs like sed and awk. 
(g)awk can be used to do the jobs of some of these commonly used tools:
1) sed
2) grep
3) wc
4) cut
5) tr
6) uniq
7) sort
therefore, learning awk greatly reduces one's learning curve.

---

### Post by kaibob on 2009-03-11
I spent some time with awk, and my script works fine. I've never used awk and found it a bit intimidating, but it's nice to learn a new tool. 

Before moving on, I wondered if someone could help me with one question. As an exercise, I decided to write an awk command that is functionally equivalent to the following grep command:

```
grep -i -m 1 "searchword" file.txt
```

I came up with the following:

```
gawk 'BEGIN {IGNORECASE=1} /searchword/ {if ( NR <= 1 ) {print $0} else exit}' file.txt
```

The above command does work but it's more a product of trial-and-error than a knowledge of awk. Is there a better way to do this? Also, the gawk manual says there should be a semi-colon before the else, but the script won't work if there is.

---

### Post by ghostdog74 on 2009-03-11
> **kaibob said:**
> 

```
gawk 'BEGIN {IGNORECASE=1} /searchword/ {if ( NR <= 1 ) {print $0} else exit}' file.txt
```


in (g)awk, 
```

awk '/pattern/{action}' file

```

the "pattern" part provides an implicit "if" condition, therefore, there is no need to explicitly put "if" in the "action" part, unless your conditions are too complex. eg
```

 awk '$1=="one" && $2 =="two"' file

```
the above just means :-> if column 1 has value "one" and column 2 has value "two". 

in the end, the above gawk command you wrote can be shortened to 
```

gawk 'BEGIN {IGNORECASE=1} NR==1 && /searchword/' file.txt

```
because you are only checking for NR equals 1, you don't need the "exit" statement.

---

### Post by kaibob on 2009-03-11
> **ghostdog74 said:**
> ```
gawk 'BEGIN {IGNORECASE=1} NR==1 && /searchword/' file.txt

```
because you are only checking for NR equals 1, you don't need the "exit" statement.
Ghostdog. Thanks for the very-understandable explanation and the suggested command line. It works great.

EDIT: 03.12.09
After a bit more work, I found that ghostdog's command line did not work in a manner similar to the grep command line above. This is probably my fault for not explaining better. Anyways, just for the record, the following does work like the grep command:

```
gawk 'BEGIN {IGNORECASE=1} /searchword/ {print;exit}' file.txt
```

---

