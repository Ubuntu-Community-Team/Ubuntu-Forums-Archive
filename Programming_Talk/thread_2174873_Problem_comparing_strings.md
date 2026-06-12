---
title: "Problem comparing strings"
date: 2013-09-16
forum: Programming Talk
---

### Post by linuxonbute on 2013-09-16
I am trying to make up a word search type of program as a way to learn more python.
Ultimately I will want user input for adding new words to the list so that may be different again.
I am doing it in stages and this is my program so far:
```

#!/usr/bin/python
from time import sleep
myword = 'john'
infile = open('/home/norman/dict/WORDS.TXT', 'r')
for myline in infile:
    print myline
    sleep(1)


if str(myline).lower() == str(myword).lower() :
#if myline == myword :
#if myline.strip() is myword.strip() :
    print('Found')
    sleep(5)


infile.close()

```

This is the contents of WORDS.TXT which I typed into gedit.
> 
fred
harry
tom
lilly
anne
john
christine
neil

None of the options I have tried works so I am at a loss as to the correct syntax to get the result I want.
Please show me what will work.
thanks

---

### Post by steeldriver on 2013-09-16
maybe use a list? 

```

>>> with open('words.txt','r') as f:
...     wordlist = [w for w in f.read().split()]
... 
>>> wordlist
['fred', 'harry', 'tom', 'lilly', 'anne', 'john', 'christine', 'neil']
>>> 
>>> 
>>> if 'john' in wordlist:
...     print 'found'
... else:
...     print 'not found'
... 
found
>>> 
>>> if 'bob' in wordlist:
...     print 'found'
... else:
...     print 'not found'
... 
not found
>>> 

```

---

### Post by linuxonbute on 2013-09-16
Great thanks, I altered it to run non-interactively:
```

#!/usr/bin/python
myword = 'tom'
f = open('./words.txt','r') 
wordlist = f.read().split()
wordlist
['fred', 'harry', 'tom', 'lilly', 'anne', 'john', 'christine', 'neil']
 
if myword in wordlist:
     print 'found'



```
and it works fine so on to the next stage.

---

### Post by Tony Flury on 2013-09-16
There are a number of reasons why your initial code would not have worked : 
1) When reading text from a file - each line ends with a \n character - which you need to remove.
2) Assuming the indentation was correct - your if statement occurred after the end of your loop - so you were only comparing agsint the last line

---

### Post by linuxonbute on 2013-09-17
> **Tony Flury said:**
> There are a number of reasons why your initial code would not have worked : 
1) When reading text from a file - each line ends with a \n character - which you need to remove.
2) Assuming the indentation was correct - your if statement occurred after the end of your loop - so you were only comparing agsint the last line
Ah yes! What a dummy I am not to have spotted that!
I went back to the original code and altered it to this:
```

#!/usr/bin/python
from time import sleep
myword = 'john'
infile = open('/home/norman/dict/CROSSWDX.TXT', 'r')
for myline in infile:
    print myline
    sleep(1)
    if str(myline.strip()).lower() == str(myword).lower():
        print('Found')
        sleep(5)


infile.close()


```
which does indeed work.

Thanks guys 2 ways to do it.
Not sure which will ultimately work best as I develop this but it's great to have both to try.

---

