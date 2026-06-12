---
title: "[Newbie] How would i add text in file at a special position?"
date: 2005-03-10
forum: Programming Talk
---

### Post by André on 2005-03-10
Hi,

i am just new to python and i would like to do some file operations.

Her comes my question:

How would i add some text to a file at a special position?

I am trying to do the following. Suggest that you have the textfile xy.txt with the content:

## file starts here
all
bunnies
cheat on
dumb
fools
## file ends here

1. Please don´t ask me why excactly these word came to my mind!  ;-)
2. How would i add an e - word to my list??
3. Which e - word would yo suggest??

Okay, for me the second point would be most important. If platform independence is a problem it would be okay for me when it just runs on Ubuntu Linux.

Thanks in adavance
André

---

### Post by Buffalo Soldier on 2005-03-10
I would like to help, but having a bit problem understanding what you want actually. What do you mean by "e - word"?

---

### Post by André on 2005-03-10
Hi,

sorry for not being clear. 

The word above start with a,b,c,d & f.

I would like to wirte a word between dumb and fools. 

Suggest you have a list of words in a file like

a
b
c
d
f

How would you write an e between d and f?

Thanks for your post and Greetz
André

---

### Post by tomchuk on 2005-03-10
test.txt:```

all
bunnies
cheat on
dumb
fools
```

to put the word "energetic" between dumb and fools, use sed's append command:
```
sed -e '/^d.*$/a\energetic'
```
Which says use sed **(sed)** to execute the sed command **(-e)** 'match a line **(/)** starting with d **(^d)**, continuing with any following characters **(.*)** to the end of the line **($) (/)**, then append a line **(a\)** with the word **(energetic)**'

Sed will output the following to stdout:
```

thomas@t40 % sed -e '/^d.*$/a\energetic' test.txt
all
bunnies
cheat on
dumb
energetic
fools

```

crap, I just realized you wanted to do this in python... you could import os and do os.system() to call sed, but I'll se if I can come up with something in python...

---

### Post by tomchuk on 2005-03-10
Alright, now in python, using pretty much the same regex, and writing to stdout:
```

#!/usr/bin/env python
import re

regex = re.compile('^d.*$')

fh = open("test.txt", 'r')
for line in fh:
        if (regex.match(line) != None):
                print line + "energetic"
        else:
                print line,
fh.close()

```

---

### Post by toojays on 2005-03-10
A less sophisticated way to achieve what you want is to append your new word to the file, and then sort the contents of your file.
```
echo energetic >> original
sort original > sorted
mv -f sorted original

```

---

### Post by André on 2005-03-11
Hi guys,

thanks for all the answers. Gives me a feeling of what would be some ways to achieve this. I will try out what works best for me when i am back home.

Greetz
André

---

