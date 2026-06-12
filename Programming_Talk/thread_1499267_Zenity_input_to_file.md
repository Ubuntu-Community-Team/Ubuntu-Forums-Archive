---
title: "Zenity input to file"
date: 2010-06-01
forum: Programming Talk
---

### Post by Logan513 on 2010-06-01
Okay, right now I have...

```
#/bin/bash

zInput=$(zenity --entry --text "Enter the text you want to translate:" --entry-text "Enter 1337 here");
```Now I want the contents of variable zInput into a .ltr file. So it can be
read later by other programs. How would I go about doing this? I have
googled it many many times and each time I come up empty handed. Is it 
even possible? Oh and how do I get Zenity boxes to pop up without the Teminal
being open?

Thanks for at least taking the time to read. :)
_Logan_

---

### Post by Logan513 on 2010-06-01
Never seems to fail. ;)
Every time I ask a question I find out the answer myself shortly after.

---

### Post by blchinezu on 2010-06-01
> **Logan513 said:**
> Okay, right now I have...

```
#/bin/bash

zInput=$(zenity --entry --text "Enter the text you want to translate:" --entry-text "Enter 1337 here");
```Now I want the contents of variable zInput into a .ltr file. So it can be
read later by other programs. How would I go about doing this? I have
googled it many many times and each time I come up empty handed. Is it 
even possible? Oh and how do I get Zenity boxes to pop up without the Teminal
being open?

Thanks for at least taking the time to read. :)
_Logan_

it's actually really simple..
if you want zInput to be written to a a .ltr file:
```
echo "$zInput" > "/path-to-file/file-name.ltr"
```
that's it

---

### Post by rnerwein on 2010-06-03
hi
your question:  Oh and how do I get Zenity boxes to pop up without the Teminal being open?
my answer:
insert into your script:
DISPLAY=:0
export DISPLAY
# i use this to run zenity via cron.
ciao

---

