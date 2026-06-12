---
title: "'tab' button for switching in-between archives when renaming."
date: 2012-07-20
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-07-20
I have found, after using linux for some time now - that when renaming documents, whether they may be photos of text files. You cannot skip from one to another by using the tab button (windows style) is there maybe another key which does this function in Linux or could it be implemented? As it would save me a lot of time instead of having to click 'rename' on every archive?

Thank you. 
K.m

---

### Post by Vaphell on 2012-07-20
while i don't know the answer, you can press F2 (it's the rename shortcut both in win and ubuntu) and navigate with arrows after ENTER. Imho only marginally slower than TAB.

sometimes it's good to rename in terminal in bulk if the names lend themselves to programmatical approach.

---

### Post by kabukiM0n0 on 2012-07-21
Excellent, thank you. That will work. 

The names would lend themselves to programmatical approach but I don't know how to bulk rename from terminal.

---

### Post by Vaphell on 2012-07-21
depends on what is supposed to happen with the names. Any examples?

there is *rename* which supports perl expressions like s/<PATTERN>/<REPLACEMENT>/
and there are basic commands like
```
for file in *.txt; do mv "$file" "${file%.txt}".ext; done
``` (this example changes extension from txt to ext)

---

### Post by kabukiM0n0 on 2012-07-22
I would use it to change the name of my cameras fotos. For example from SANYxxxx to just numbered - from 1-xxx

I have no previous understanding in perl expressions, but will look into it.

---

### Post by Vaphell on 2012-07-22
droppin SANY and preserving the rest of the name would be something like this:
```
rename -v 's/SANY(.*)/$1/' SANY*.jpg
```
(.*) will capture the rest and in replacement part we can call the content of the parentheses with $1 $2 $3... (first () is $1, second $2...). SANYwhatever.jpg becomes whatever.jpg.

if you simply want to drop the prefix and reindex pictures to 1..NUMBER_OF_PICS you can go like this
```
i=0; for file in SANY*.jpg; do ((i++)); mv -v "$file" $i.jpg; done
```
i is file counter and is used to create new name for each file
or
```
i=0; for file in SANY*.jpg; do ((i++)); mv -v "$file" $( printf "**%04d**" $i).jpg; done
``` to pad the number to desired width with 0s - 4 in this example. It preserves alphabetical order used to sort files by name - without it order would be like this 1 > 11 > 111 > 2. with zeros it will be 0001 > 0002 > 0011 > 0111

---

