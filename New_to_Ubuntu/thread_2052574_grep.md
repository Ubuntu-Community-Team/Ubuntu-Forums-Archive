---
title: "grep"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by ruben_linux on 2012-09-03
i have a txt which contain a few words, that i would like find in some txt.
i try: 
```
cat source.txt | grep -f -w /home/ruben/*.txt
```but dont works
i found on net this sript but neither works

```
for name in `cat /home/ruben/fuente.txt `
do
grep $name /home/ruben/*.txt >> salida
done
```

---

### Post by hakermania on 2012-09-03
> **ruben_linux said:**
> i have a txt which contain a few words, that i would like find in some txt.
i try: 
```
cat source.txt | grep -f -w /home/ruben/*.txt
```but dont works
i found on net this sript but neither works

```
for name in `cat /home/ruben/fuente.txt `
do
grep $name /home/ruben/*.txt >> salida
done
```

Well, so, as far as I can understand (because, without any offense, you didn't try your best with english), you have a txt file some words, and, depending on these words, you need to find them inside an other txt file.

Let's call the first source.txt and the one you need to search into seach_me.txt. Then, the script would be something like this:

```

#!/bin/bash

counter=0

while read line; do

   let counter=counter+1

   if grep "$line" search_me.txt > /dev/null 2>&1; then
   
      echo "The word "$line" was found inside search_me.txt at line "$counter"

   fi

done < source.txt

```

---

### Post by Hadaka on 2012-09-03
Hi, your post was not clear on exactly what you are attempting to do, but i read it as
you have a file..fuente.txt and you want to find multiple words within that file using
grep.

#EXAMPLE fuente.txt.

Here is a text file with 3 lines of data, this line contains word1.
line 2 contains word2
word3 is in the 3rd line.
____________________________________________________________
to grep word1,word2 and word3 from fuente.txt

```
grep -E "word1|word2|word3" < fuente.txt 
```to grep a single word

```
grep -i word1 < fuente.txt
```is this what you were trying to do??

---

### Post by Vaphell on 2012-09-03
```
$ cat words.txt
python
bash

# gluing words together with |
$ awk 'BEGIN{RS=""; OFS="|";} {$1=$1; print; }' words.txt
python|bash

# using grep with prepared regex
$ grep -E "$( awk 'BEGIN{RS=""; OFS="|";} {$1=$1; print; }' words.txt )" *
raw input.py:#!/usr/bin/env **python**
rearrange.sh:#!/bin/**bash**
receipt.py:#!/usr/bin/env **python**
regex.py:#!/usr/bin/env **python**
regex.sh:#!/bin/**bash**
reg.py:#!/usr/bin/env **python**
restore_ext.sh:#!/bin/**bash**
rnd.sh:#!/bin/**bash**
```

---

### Post by ruben_linux on 2012-09-03
i have a source.txt in /home/ruben, this file contain very words, and another one, in /home/ruben/examenes i have very document.

all document are in txt. 

i would like that "grep" found the words that are in source in the document is in /home/ruben/examen.

sorry about my english, i'm learning :P

---

### Post by SeijiSensei on 2012-09-03
That script you posted originally should work unless the "words" have embedded spaces.

```

for name in `cat /home/ruben/fuente.txt `
do
grep $name /home/ruben/*.txt >> salida
done

```

What went wrong when you ran these commands?  If the names have embedded spaces, you have to put double quotes around $name like this:

```

for name in `cat /home/ruben/fuente.txt `
do
grep "$name" /home/ruben/*.txt >> salida
done

```

Bash treats spaces as delimiters, so if the first entry in fuente.txt is "Barack Obama" then the grep command in your script would read:

```
grep Barack Obama /home/ruben/*.txt
```

which bash will treat as a search for "Barack" within "Obama" and ignore the file specification entirely.

By the way, single and double quotes are not interchangeable in bash.  The string '$name' means the literal $name, while "$name" replaces the variable with the contents of $name.

---

### Post by sisco311 on 2012-09-03
Assuming that each line in *source* contains a single word (or pattern), then:
```
grep -f ~ruben/source.txt ~ruben/examens/*
```
should do the trick.

---

### Post by Bashing-om on 2012-09-03
ruben_linux;

  In regards to your last post, perhaps you are using the wrong tool to accomplish your goal.
Rather than grep, please consider to use cmp (compare two files), or diff (find the difference between two files).
your attention is invited to the man pages:
```
man cmp
man diff

```

[INDENT]I hope this helps <==BDQ

[/INDENT]

---

