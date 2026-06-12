---
title: "replacing text split by &quot;\n&quot; using sed"
date: 2009-10-16
forum: Programming Talk
---

### Post by nathan726 on 2009-10-16
I need to replace all occurances of "somestring" with "x" in the following example:
```
blah blah somestring blah some
string blah somestring somestring blah so
mestring blah blah blah blah somestrin
g somestring blah somestring
```Using sed 's/somesting/x/g' gives me:
```
blah blah x blah some
string blah x x blah so
mestring blah blah blah blah somestrin
g x blah x
```But what I want is something more like this:
```
blah blah x blah x
 blah x x blah x
 blah blah blah blah x
 x blah x
```Is there some way to do this without doing a search/replace with every single possibility (s\nomestring, so\nmestring, som\nestring, etc...)

I've tried removing all the whitespace first, but sed refuses to work?

---

### Post by Vermind on 2009-10-16
```
awk '{x=x""$0;} END { print x; }' blah.txt | sed -e "s/somestring//g"
```
where blah.txt is your file. You lose newlines though.

---

### Post by ghostdog74 on 2009-10-16
> **Vermind said:**
> ```
awk '{x=x""$0;} END { print x; }' blah.txt | sed -e "s/somestring//g"
```
where blah.txt is your file. You lose newlines though.

why the extra unnecessary sed when you already concatenate all lines into "x" in awk? Just do the substitution in awk at the END block using gsub()

---

### Post by nathan726 on 2009-10-16
> **Vermind said:**
> ```
awk '{x=x""$0;} END { print x; }' blah.txt | sed -e "s/somestring//g"
```where blah.txt is your file. You lose newlines though.

Doesn't seem to work when I put your code into my script (probably cause my script is real messy!)

What I need is a something that can find and replace all instances of a word, even if that word is seperated by a character - like this:
```
cat file.txt | sed 's/fedora/ubuntu/; s/fXedora/ubuntu/; s/feXdora/ubuntu/; s/fedXora/ubuntu/; s/fedoXra/ubuntu/; s/fedorXa/ubuntu/; s/fedorXa/ubuntu/;'
``` I guess could write a script to generate the script for each word I want to replace, but surely there is something more simple?

---

### Post by Arndt on 2009-10-16
> **nathan726 said:**
> Doesn't seem to work when I put your code into my script (probably cause my script is real messy!)

What I need is a something that can find and replace all instances of a word, even if that word is seperated by a character - like this:
```
cat file.txt | sed 's/fedora/ubuntu/; s/fXedora/ubuntu/; s/feXdora/ubuntu/; s/fedXora/ubuntu/; s/fedoXra/ubuntu/; s/fedorXa/ubuntu/; s/fedorXa/ubuntu/;'
``` I guess could write a script to generate the script for each word I want to replace, but surely there is something more simple?

"Doesn't seem to work" is not a good problem description. The approach is good, I think (whether sed or awk does the replacement), and it works when I try it. One problem with it may be that the result may be a very very long line, which doesn't work in all programs, so you will want to split it up in lines again.

Another solution may involve avoiding splitting up words over lines in the first place. Is that a possibility?

---

### Post by nathan726 on 2009-10-16
Well, I wrote a function to do exactly what I need...
```
#! /bin/bash

function replace () {
c=0; for a in "$@"; do i=0; b=($a); d=${b[0]}
while [ ${#d} -gt $i ]; do if [ $i = 0 ]
then array[$c]="s/${d:0:$i}${d:$i}/${b[1]}/g;"
else array[$c]="s/${d:0:$i}${b[2]}${d:$i}/${b[1]}/g;"
fi; let c++; let i++; done; done; echo ${array[@]}
}

echo $(replace 'fedora ubuntu X')
echo -e 3d\n3344 caows cowQs 3d334\n4 cow cows | sed "$(replace '3d3344 3d .' 'cows paddy .')"
```result:
```
s/fedora/ubuntu/g; s/fXedora/ubuntu/g; s/feXdora/ubuntu/g; s/fedXora/ubuntu/g; s/fedoXra/ubuntu/g; s/fedorXa/ubuntu/g;
3d paddy paddy 3d cow paddy

```Not bad considering that I only started learning bash a few days ago. Hmm... still doesn't replace \n though, but I found a fix for that - I just convert my text file to hex using "xxd -p" and can use sed to replace the "0a" characters.

---

